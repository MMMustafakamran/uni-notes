# Databases Notes (transcription)

Auto-transcribed from `Db.pdf` (OCR + AI correction). Diagrams/tables are approximate.

## Page 1
```text
rabail.zahid@isb.nu.edu.pk
Quiz 10% - assignment based
Ass
10%
Proj
10%
Mid
30%
Final
40%
```

## Page 2
### ER diagram
```text
Entity
Weak entity
ER diagram
Time Stamp Date Time
Identifying
relationship
shipmovement
full participation (double line)
multivalued attribute
Key attribute
History
composite
Type
Derived attribute
SName
Ship
Type
ShipType
```

## Page 3
### Database Session 2
#### Joins
```text
Database
Session 2
* Joins
Inner
outer left / Right
Full outer
Transaction
foreign key
customer
customer_id Name
T-id amount customer_id
100
4.99
3
1
Mustafa
101
2.89
2
2
Ahmed
102
2.19
1
3
Ali
103
2.20
Null
4
Naveed
Inner Join (will display combined columns, after joining with a common row)
select * From Transaction INNER JOIN customer
ON Transaction.customer_id = customer.customer_id;
T-id
Amount
customer_id
customer_id
Name
100
4.99
3
3
Ali
101
2.89
2
2
Ahmed
will be
102
2.19
1
1
Mustafa
in order
Doesnt contain T_id = 103
Doesnt contain Naveed
of n'
table
if we use left join it will
use right join
T-id
Amount
customer_id
Name
100
Ali Mustafa
4.99
101
2.89
2
Ahmed
102
2.19
3
Mustafa
4
Naveed
```

## Page 4
#### Functions
```text
Transaction id amount
* Functions
1
4.99
3
count
2
2.89
2
3.88
2
max, min
3
3
4.99
AVG
4
1
1.00
4
SUM
5
5
CONCAT
calculate how many rows, in amount's column
1, Select count(amount) as "today's transaction"
Today's Transaction
from transactions
→
5
2, Select max (amount) from transaction
min (amount)
4.99
1.00
3,
AVG (amount) from trans → 3.45
SUM
→ 17.25
employ_id firstname lastname
1
Mustafa
Kamran
Ali
Asif
2
Talha
Ali
3
4, select CONCAT(firstname, " ",
lastname) as FullName
from employees
→
FullName
Mustafa Kamran
Ali Asif
```

## Page 5
#### Library Schema Queries
```text
- Null, is not
not in, not exist
Q1, Book
Bid | title | Pub_name
Author
id | name
Bookcopies
Publisher
Bookid | Branchid | No of copies
Name | Address | Phone
Book loans
Bookid | Branch id | Cardno | Dateout | Duedate
LibraryBranch
Branch_id | Branchname | Address
Borrower
card_no | Name | Address | Phone
Q1, how many copies of "The Lost Tribe" owned by library whose name "Sharpstown"
Select Noofcopies
From Bookcopies, Book, Branch
where Branch.Branchname = "Shapiown" and Book.Title = "
2, How many copies of "The Lost Tribe" owned by each Branch
Select BranchID, Noofcopies
from bookcopies, branch, book
where Innerjoin
3, Name of all borrower who dont have books checked out
select Name
from Borrower
Innerjoin Bookloans a on cardno=cardno
where Bookid = null
```

## Page 6
#### Where not exist
```text
* where not exist
clause used to filter rows based on subquery
e.g Select Name
From Borrower
where not exist (Select * from Book_loans where B.cardNo = L.cardNo)
will select
rows in Borrower table
where a related row doesn't exist in Book_Loans table
* Name Address
Sharptown
shows borrowers of Sharptown with Duedate of today
5, write query, retrieve name, address, number of books
checked out for all borrowers with more than 5 books checked out
Select Bname, Baddress, count(*) as "no' of books checked"
From Borrower B, Book
where B.cardNo = BL.cardNo and BL.book_id = Bk.Book_id
Having count(BL.bookid) > 5
Select BW.Name, BW.address, count(BL.Bookid) as " Number of book"
From Borrower BW
Innerjoin Book_Loan BL on BW.cardNo = BL.cardNo
Groupby BW.cardNo  Having count(BL.Bookid) > 5
```

## Page 7
```text
6, for each book authored by "Stephen King", retrieve title, no of copies owned
by Branch 'central'. Use full outer join.
join 3 table
book - Name
Select Bo.title, Bc.noofcopies
From Book B
Bookcopies - Noofcopies
Full outer join BC on B.Bookid = Bc.bookid
Branch - Name
join Branch BB on BB.branchid = BC.branchid.
where BB.Name = "central" and "B.Publisher = "stephenking"
```

## Page 8
### Relational Mapping
#### Regular entity
#### Weak entity
#### Binary 1:1
```text
* Relational Mapping
Regular entity
include all simple attribute, all simple attributes of composite
chose a primary
if primary is composite then all composite
will be primary
Weak entity
include all simple + add foreign key of primary key of
where derived from
Binary 1:1
modified table add foreign key
identify S, T
include foreign key
choose entity with total participation in R in role of S
start
Location
Date
eg
Salary
Name
Number
Department
employee
manages
Department
Dname | Dnumber | Mgr_ssn | Mgr_startdate
foreign key
```

## Page 9
#### Binary 1:N
#### Binary M:N
```text
Binary 1:N
identify S, T
N side
Add foreign key in S, which is T's primary key
Include attribute of relation
N
works for
department
eg
employ
S
add foreign key of Number
eg2
employee
add SSN as foreign key
1
supervise
N
Name SSN Address salary Supervisor_SSN
* Binary M:N
create new relation S to represent R
add 2 foreign key from each entity
hours
Name Location
Number
M
employee
works on
N
Projects
workon
Employee_SSN | Project_Number
Hours
```

## Page 10
#### Multivalued Attribute
#### N-Ary Relation
```text
* Multivalued Attribute A
create new relation R
include attribute = A, primary key attribute K
Location
include multiple
Name
include Attributes
Department
so
Dept_Locations
D_Number | D_Location
* N-Ary Relation
Doctor
Q1, ID | First | middle | Last | Patient ID
Prescription
patientID
Spe
Patient
ID | Name | Age | Locality | Town | medicinecode
Medicine code | Name | Quantity | BrandID
```

## Page 11
### File system Anomalies
#### Draw Relation model of ERD
```text
Business
UG
Publication:
Publication typ
book, chapter
book
Publication
d
article
* File system Anomalies
scalability
Redundancy (Repetition)
Concurrency (updation), constraints
Data Security
Data Query Retrival
Date
* Draw Relation model of erd
M
N
exam
Name
Person
NID email
Name
Person
NID Name
Exam
Person_Email
e_ID Name
NID email
Qualification NID | eID | Date
```

## Page 12
### Normalisation
#### First Normal Form
```text
Normalisation
To Remove Redundancy
1 Row level
Duplicacy 2 column level
Use Primary Key to Remove Row level Dup
SID
SName
Age
RAM
20
Varun
1
25
2
RAM
20
1
SID
SName
cid
cname
Fid
FName
salary
DBMS
1
C1
F1
John
30
Same
JAVA
F2
Ali
40
2
C2
DBMS
F1
John
30
3
C1
Insertion Anomaly
Deletion Anomaly
Updation Anomaly
First Normal Form
should contain Multivalued Attribute
Rollno | course | Name
Roll | Name | course
Roll | Name | course1 | course2
ALI
C++
OR
1
C++/C
1
BOB
2
Java
1
C
2
Java/C
YO
2
3
3
Java
C
3 option divide
into course table
Primary key = Roll number + Course
```

## Page 13
### Functional Dependencies
#### Second Normal Form
```text
Functional Dependencies
X → Y  Dependent Attribute
Determinant
satisfy
SID sname
1
Ali X
2 Ahmed
* Transitive
X → Y and Y → Z then X → Z
Second Form
must be in 1 Normal form
All non prime attribute must be fully functional dependent on
candidate key (No Partial Dependency)
CustomerID | Store ID | Location
Delhi
1
1
3
Mumbai
2
1
Delhi
3
2
Bangalore
4
3
location = Non Prime must be fully dependent on
Mumbai
both customerID, storeID X
only dependent
Candidate key = Customer ID, Store ID
on store ID
Location
Delhi
(Partial)
CustomerID | Store ID
StoreID
Divide Table
1
3
Bangalore
3
Mumbai
```

## Page 14
#### Third Normal Form
```text
Third Normal Form
Must be in 2nd Normal
must be no Transitive Dependency
Roll No | State | City
1
Punjab
Mohali
F.D =
Candidate key = Roll Number
2
Haryana
Roll_no → state
Punjabi
3
Mohali
state → city
transitive
```

## Page 15
#### Partial Dependency
```text
n=7
Partial Dependency
No Transitive Dependency in 3rd Normal
3, 4, 5, 6.
Candidate key vs super
All possible key
subset of
( studentid,
(5,1) (4,2) (3,3)
N=6
(3,2,1) (4,1,1)
```

## Page 16
```text
```

## Page 17
### Database Final
### Relational Algebra
```text
Database Final
20th Monday
Topics after sessional II
Relational Algebra
Query processing, Optimization
Transaction Processing
Relational Algebra takes 1 or more relations as input and produces output
Fundamental operations
Additional operations.
select (σ)
set intersection (∩)
Project (π)
Assignment operation (=)
Union (∪)
Natural join (⋈)
set difference (-)
Division operation (÷)
cartesian Product (x)
outer join
Rename (ρ)
left (⟕)
right (⟖)
full (⟗)
```

## Page 18
#### Select
#### Project
```text
* Select (σ)
selects tuples that satisfy a given predicate
Syntax:
σ condition(Relation)
eg
σ ID=2 (employee)
comparison operators =, ≠, <, >, ≤
connectives AND (∧), OR (∨), NOT (¬)
Q1, Instructor table
Salary
ID
Name
D.Name
a, write an RA expression for
10101
John Biology
65000
all instructor working in Finance
12121
Robin
Computer Science
90000
σ Dept.Name = Finance (Instructor)
b, Find instructor of salary > 87,000
c)
σ (Salary > 87000) (Instructor)
σ Salary > 87000 ∧ Dept.Name = Finance
* Project (π)
returns argument relation with certain attributes left out
it is unary operator
It is a set relation
Duplicate rows are eliminated
(Relation)
Syntax: π
Attribute 1, A2, A3...
a, list instructor everything but dept name
π ID,name,salary (Instructor)
b,* Find Instructor Name in computer science department
π name (σ dept_name = computer science (Instructor))
```

## Page 19
#### Rename
#### Union
#### Set Difference
#### Intersection
#### Division operation
```text
* Rename
ρ
* Union
A | B
A | B
a
2
So σ(r∪s)
a
2
β
3
r
A
B
a
β
a
No duplicate
s
a
2
β
3
* Set Difference => r - s → includes tuples in r that are not in s
A B
So
σ(r-s) =
a 1
β 1
* Intersection => r ∩ s → include common tuples
r - (r - s) = r ∩ s
* Division operation
r ÷ s
Tuples of r associated with tuples of s
eg show names of students required in every/all courses
R2 ÷ S possible if R2 ⊂ R1 ∪ S
subset
S must not be equal
ex
```

## Page 20
#### Cartesian Product
```text
example => student ÷ course
Student table
course table
cname
S-Name
CName
DBMS
Tom
DBMS
DS
DS
CN
Tom
DS
Tom
CN
Ali
DBMS
Amy
CN
Amy
DBMS
Amy
DS
so
Tom
Amy
Student ÷ course → 'students enrolled in all courses' →
* Cartesian Product (X)
• every tuples of R with every tuples s
• Binary operation
• All possible pairings
• same attribute appear in R1, R2
Ambiguity
Ac-No
C.Name
Loan-no
same column name
John
Tom
Smith
Rose
Tom
Deposit
Borrower
Jack
Tom
→
C.Name
Loan-No
R = Deposit X Borrower
John
Tom
A-101
Smith
John
L-201
Rose
Rose A-304
Smith
L-658
Rose
Rose
Rose
L-256
Rose
Jack
Jack
L-547
```

## Page 21
```text
Q1) Find names of all instructors in Physics dept together with course id
of all courses they teach
σ deptname = 'physics' (Instructor × Teaches)
will give all instructors of physics with courses they taught
Instructor
Teaches
course-ID
sec-ID
semester
ID
Name
1010
Deptname
Dont match
Instructor-ID
Name
Deptname
78787
Raj
Physics
10101
78787
Raj
Physics
2020
78787
Raj
Physics
7879
• choose Tuples where instructor.ID = Teachesoid
so
σ instructorid = teachesorid (σ deptname = 'physics' (instructor × Teaches))
so
78787 | Raj | Physics | 78787
• only want Name
π Name, courseid ( . . . )
)
```

## Page 22
### Natural Join
#### Theta Join
```text
Natural Join
• Inner Join
Select tuples that satisfy join criteria
Discard rows that dont match
1- Theta Join (⋈θ)
2- Equi Join (⋈θ)
3- Natural Join (⋈*)
1. Theta Join
P ⋈θ Q
predicate / condition = ≠ < >
P ⋈θ Q = σθ (P × Q)
so
eg=> S1 ⋈S1.S-ID > R1.S-ID R1
Rating
S-ID S-name Rating Age
S-ID B-ID
Date
S.Rating
22
Tom
7
22
101
10-May
8
Amy
31
8
58
103
5-Jan
10
58
Rose
10
22 > 22 X don't join
31 Amy 8
22
10th May
31 > 22 ✓
58 Rose 10 58 103 15th May
31 > 58 X
=>
58 > 22 ✓
58 > 58 X
```

## Page 23
#### Equi Join
#### Natural Join (⋈*)
### Aggregate Function
```text
2) Equi Join
L only use = as condition
3) Natural Join ⋈*
case of equijoin
(Ch
can be performed if common attribute
name, domain must be same
Doesn't concatenate
P ⋈* Q = π columns (σ⋈* (P × Q))
e.g. S1 ⋈* R1
L if S.ID matches, Rating must also match
so
58 | Rose | 10 | 103 | 5th Jan
π S.ID, DID, Gradyear, Nationality ( σ student ⋈
student.id = deptmin.ID )
Aggregate Function
Q1)
Sum of assets of all branches
(branch)
G sum(assets)
group by
Convert: select branchname, sum(Balance) as sum_balance from account group by
branchname
π branchname, sum_balance ( branchname g sum(balance) as sum_balance (Account))
select Department, count(*) as employee count, Avg(salary) as
Average salary from employees group by department
G g department (employees)
π dept, count(
```

## Page 24
### Heuristic Optimization
```text
Heuristic Optimization
Q1) Course ( C.No, cname, credits)
Student (Rollno, Name, Address, sem)
enrollment (CNo, rollno, Grade)
Query = select s.name, s.address, E.grade from
course c, student s, Enrollment E
where s.rollno = E.rollno and c.CNO = E.CNO
and cname = 'PBDP'
Initial Tree:
• Start from bottom of query
π s.name, s.address, E.grade
σ c.name = 'PBPB' ∧ s.rollno = e.rollno ∧ c.CNO = E.CNO
Joining
Selection
×
×
S
student
enrollment
course
```

## Page 25
```text
π s.name, s.address, e.grade
σ c.cno = E.cno
×
Student enrollment
course
Step 2: Reorder Relation
• better to join E and c first as there might be student that dont
enroll in any course
replace with
join
σ s.rollno = E.rollno
×
⋈ c.cno = E.cno
σ course = 'PBPB'
S
e
c
Step 3: Replace selection and × by Join
π name, address, grade
⋈ s.rollno = E.rollno
⋈ c.cno = Eno  only required
only connected
σ cname = 'PBPB'  so π cno
e
c
• Step 4: Move Projection Down
```

## Page 26
```text
Heuristic Optimization
Q1) Course ( C.No, cname, credits)
Student (Rollno, Name, Address, sem)
enrollment (CNo, rollno, Grade)
Query = select s.name, s.address, E.grade from
course c, student s, Enrollment E
where s.rollno = E.rollno and c.CNO = E.cno
and cname = 'PBDP'
Initial Tree:
• Start from bottom of query
π s.name, s.address, E.grade
σ c.name = 'PBPB' ∧ s.rollno = e.rollno ∧ c.CNO = E.CNO
Joining
Joining
Selection
×
S
E
student
enrollment
course
```

## Page 27
```text
π s.name, s.address, e.grade
σ c.cno = E.cno
×
Student enrollment
course
Step 2: Reorder Relation
• better to join E and c first as there might be student that dont
enroll in any course
So π name,
replace with join
σ s.rollno = E.rollno
×
σ c.cno = E.cno
σ course = 'PBPB'
Step 3: Replace selection and × by Join.
π name, address, grade
⋈ s.rollno = E.rollno
⋈ c.cno = Eno  only required
only connected
σ cname = 'PBPB'  so π cno
e
c
• Step 4: Move Projection Down
```

## Page 28
```text
π s.name, address, e.grade
⋈ s.rollno = E.rollno
⋈ cno = e.cno
π cno
π s.rollno, s.name, s.address
σ cname = 'PBPB'
π cno, e.rollno, e.grade
C
Course
S
Enroll
```

## Page 29
### Transactional Processing
```text
Transactional Processing
L program which execution changes content of a DB
Transaction Boundary
Begin / end Transaction
Types of Transactions
Read
Read set of T: all data items that transaction T reads
Informal example
transfer 40,000 from checking to saving account
L read balance of checking = read(X)
read(Y)
subtract 40,000 from
Y + 40,000
write (X)
• Read(X) requires
1. find address of disk block that contains X
2. copy disk block in buffer in main memory
3- copy X from buffer to variable named X
• Write (X)
= same 3 steps
3 - copy variable to buffer (opposite)
4. Store updated block from buffer to disk (might be temporary)
```

## Page 30
### Concurrency Control
#### Lost Update Problem
```text
Concurrency Control
solves: solves lost update problem
temporary update problem
incorrect summary
read/write = Db operations
calculations = non-DB operations
Database consistent state
2 or more Ts
• Concurrent Transactions: happen at same time
but CPU can only execute one (so context switch)
Lost update problem (write, write problem)
eg
T1 | T2
Buffer  A = 10
R(A)
A++
W(A)
so
W(A) //write so
commit
A will be so in DBMS
at end, so T1 lost
Commit
as committed later
ex A++ could be lost so inconsistent state
• Two users Read same time
L if T1 write and T2 Read the newly written by T1 value
• Dirty Read
• Incorrect Summary
```

## Page 31
```text
A = 100
B = 200
T1
T2
sum = 0
R(A)
sum = sum + A
sum = 100
R(B)
B = B + 100 =
B = 300
W(B)
R(B)
sum = sum + B
= 400
L it should be 100+200 = 300
system crashes before data written
may
• Problem of atomicity
• shared data modification while transaction
L Problem of serialization, isolation
solution:
Concurrency Control
and
Recovery Mode
system crash, Disk failure, Location error
Physical prob
```

## Page 32
### Transaction and System Concepts
#### System Log
```text
Transaction and System Concepts
Begin_Transaction:
READ, write
END_Transaction
COMMIT_Transaction
Partial
ROLLBACK or ABORT = undo
Begin_T...
commit
Active
End_Tr...
Partially committed
committed
Abort
abort
SYSTEM LOG
• transaction ID
• System log
multiple record type file
log kept on disk
Periodically backed up
• Log Records
1. [start_Transaction, T]
2. [write-item, X, old-value, new-value]
4) [commit, T]
5) [abort, T]
6.) [checkpoint]
• If crash, check last checkpoint before that permanent
```

## Page 33
### Properties of Transaction
#### Serializability
```text
Properties of Transaction
• Atomicity: one unit of operation
• Consistency
• Isolation
• Durability
Conflicts if
L Different T
L same variable
L use's write once
conflict serializable
Serializability
L Schedule can be serializable if
S
Graph
T2
T1
R(A)
T1
T2
W(A)
R(A)
W(A)
serial
schedule -
as T1 ended first before
T2 started
2)
T1
T2
R(A)
so
R(A)
W(A)
W(A)
• make this serializable
L either convert to
T1 → T2
or T2 → T1
```

## Page 34
#### Conflict Equivalent Schedule
```text
• Conflict equivalent schedule
(S ≡ S')
R(A)  R(A)  } Non conflict pair
R(A)  W(A)
W(A)  R(A)
conflict pair
W(A)  W(A)
R(A)  W(B)
W(B)  W(A)
Non-conflict
as different variables
both
Q1) check if conflict equivalent of both
T1
T2
T2
R(A)
and R(A)
W(A)
R(A)
R(B)
pair, swap timing
W(A)
• If conflict pair no swapping
R(A)
R(B)
W(A)
R(A)
so
W(A)
→
R(B)
same
R(A)
R(A)
so Yes
R(B)
conflict
W(A)
equivalent
S ≡ S'
```

## Page 35
#### Conflict Serializability
```text
Conflict Serializability
T1
T2
T3
check if schedule is conflict serializable
R(X)
R(Y)
- make precedence graph make edges
R(X) find W(X)
R(Y)
check conflict
R(Z)
T1
T2
pairs in
transaction
W(Z)
T3
R W
W R
R(Z)
W W
W(Y)
W(Z)
• for edge start from above, eg R(X) find for all below conflict pair, if found make
edge
• If graph has loop / cycle
then non conflict serializable
• If no loop
then yes conflict serializable and thus consistent also
• Possibilities of serial
T1 → T2 → T3
T1 → T3 → T2
check
T2 → T1 → T3
graph
T2 → T3 → T1
so remove T2 from graph
T3 → T1 → T2
find node with no arrow coming towards it so = T2
T3 → T2 → T1
so
```

## Page 36
#### View Serializability
```text
• if loop found
L check if View Serializable
Q1) Check if these 2 schedules are view equivalent
T1 T2 T3
T1 T2 T3
1st R(A)
2nd W(A)
W(A)
W(A)
W(A)
W(A)
OV
• give value to each
write eg A+10 if output equal then view eq - lead to same result
• make precedence graph - same ways as before
T1
T2
T3
```

## Page 37
### Relational Mapping
#### Integrity Constraints
```text
Name course
disregarded
eg)
20
more efficient
as disregarded students that arent
enroll
S
20
so
Name  course
π name, sum_balance (
eg
20
★ Relational Mapping
relation = Table
relation schema = Name of Table + attributes
Degree = Total number of attributes in Relation
cardinality = Total
'' Rows in Table
★ Integrity Constraints
L ensure accuracy, consistency
★ Domain Constraint - int, string etc
★ Entity Integrity Constraint (Primary key ≠ null)
★ Referential Integrity Constraint - foreign key must point to existing primary key
★ Key Constraint
L Unique
key
L Composite = 2 columns
Super
Candidate - minimal, replaceable eg Name
Surrogate
L artificially
added to serve as primary key
```

## Page 38
### Recurrence
#### Methods to Solve Recursion
```text
Recurrence
• The expression:
Base case
T(n) =
c    n = 1
2T(n/2) + cn   n > 1
how many recursive calls
Q1) public void func (int n) {
if (n>0) {
print(n);
func(n-1);
T(n) = 1T(n-1) +
Ans)
Methods to solve Recursion
Substitution
Iteration
Recursion tree
Master Theorem.
```

## Page 39
#### Substitution Method
```text
Substitution Method
1. Guess form of solution
2. Verify by Induction
3. Solve for constants.
Q1) T(n) = { 1
n = 1
2T(n/2) + n   n > 1
1, Guess : T(n) = n lg n + n
Ans)
2) Induction
Basis : n = 1 => n lg n + n = 1 = T(n) ✓ satisfies Base case
Inductive step: T(K) = K
lg K + K for all K < n
T(n) = 2T(n/2) + n
← put Guess into it
= 2( n/2 lg n/2 + n/2 ) + n
inductive hypothesis
= n lg n/2 + n + n
= n(lg n - lg 2) + n + n
= n lg n - n + n + n
n lg n + n
```

## Page 40
#### Iteration Method
```text
★
Lower bound with Substitution
skipped
★ Iteration Method
Q1)
S(n) =
0   n = 0
c + S(n-1)   n > 0
Ans)
S(n) = c + S(n-1)
c + c + S(n-2)
2c + S(n-2)
2c + c + S(n-3)
3c + S(n-3)
kc + S(n-k)
• Base case reach when n=0 or when k = n
so
nc + S(n-n)
nc + S(0)
cn
```

## Page 41
#### Iteration
```text
Iteration
Q2) s(n) = {
0    n=1
n + s(n-1)    n>0
s(n) = n + s(n-1)
= n + n + s(n-2)
n + (n-1) + s(n-2)
= 2n + s(n-2)
n + n-1 + n-2 + s(n-3)
=>
n
+ s(n-k)
s(n) = => Σ i
Arithmetic Series
i=n-k+1
solve this
Base case, when k=n
This step is the
most marks
s(n) = Σ i + s(0)
= Σ i + 0
= Σ i
s(n) = Σ i
n=n
i=1
```
