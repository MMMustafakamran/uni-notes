# Algorithms Notes (transcription)

Auto-transcribed from `Algo.pdf` (OCR + AI correction). Diagrams/tables are approximate.

## Page 1
### Recurrence Relations
#### Example 1: W(n) = 2W(n/2) + n^2
```text
Recurrence
To solve
use master theorem
1- Iteration
to confirm all
2- Recursion tree
methods
3- Master Theorem
Example 1)
W(n) = 2W(n/2) + n^2
W(n)
=>
n^2
n^2
W(n/2)  W(n/2)
W(n/2)  W(n/2)
W(n/2) = 2W(n/4) + (n/2)^2
W(n/2)
W(n/2)
W(n/4) = 2W(n/2^3) + (n/4)^2
W(n/4)
n^2
(n/2)^2
2(n/2)^2
4(n/2^2)^2
Decreasing Geometric
2^k (n/2^k)^2
series always gives a
constant.
n^2 + 1/2 n^2 + 1/2^2 n^2 + 1/2^3 n^2 ... 1/2^k n^2
n^2 [1 + 1/2 + 1/2^2 + 1/2^3 ... 1/2^k]
2^k = n
= n^2 (1 - 1/2)
k = log n
Sum of
= n^2 (1/2)
Geometric
```

## Page 2
#### Example 2: T(n) = 3T(n/4) + cn^2
```text
Example2  T(n) = 3T(n/4) + cn^2
cn^2
n^2 -> n^2
c(n/4)^2
(n/4)^2
(n/4)^2
(n/4)^2  3n^2/16
T(n/4^2)
T(n/4^3)
3^k n^2 / 16^k
= n^2 (1 + 3/16 + 9/16 + ... 1/4^k)
O(n^2)
= 3(n/4^k) + c(n/4^(k-1))
=)
```

## Page 3
#### Q2: T(n) = 2T(n-1) + 1
```text
Q2) Solve T(n) = T(n/4) + T(n/2) + n^2
b) T(n) = 2T(n-1) + 1   n>0
T(n)
2^0
T(n-1)  T(n-1)  1
2^1
T(n-2)  T(n-2)
2^2
[1 + 2 + 2^2 + ... + 2^k]
increasing geometric
so O(2^k) = O(2^n)
```

## Page 4
### Master Theorem
```text
Master theorem
f(n) = Θ(n^k log^p n)
T(n) = aT(n/b) + f(n)
eg: T(n) = T(n-1) + 1  X
x must be > 1
a >= 1, b > 1
Solution is
T(n) = n^(log_b a) [U(n)]
depends on R(n) = f(n) / n^(log_b a)
if R(n)    U(n)
case 1  log_b a > k then Θ(n^(log_b a))
n^r, r>0    O(n^r)
2   log_b a = k
n^r, r<0    O(1)
3-  if p > -1 -> Θ(n^k log^(p+1) n)
(log n)^i, i>=0   (log_2 n)^(i+1) / (i+1)
Q1) T(n) = 8T(n/2) + n^2
Ans) a = 8, b = 2, f(n) = n^2
T(n) = n^(log_2 8) . U(n) = n^3 . U(n)
calculate U(n)
-> R(n) = n^2 / n^(log_2 8)
= n^2 / n^3 = n^-1,  n^r, r<0 so O(1)
Q2) T(n) = T(n/2) + c
Ans) a = 1, b = 2, f(n) = c
n^(log_2 1) U(n) = n^0 . U(n)
U(n) = R(n) = f(n) / n^0 = c / n^0 = c / 1 = c
(log_2 n)^(0+1) = log_2 n . c = O(log_2 n)
```

## Page 5
### Recursion Tree
#### Sum of Geometric Series
```text
Recursion Tree
· Sum of Geometric Series
x^0 + x^1 + x^2 + ... + x^n = (x^(n+1) - 1) / (x - 1)   for x != 1
x^0 + x^1 + ...
= 1 / (1-x)
for |x| < 1
Q1) T(n) = 2T(n/2) + n
Ans) T(n) = 2 . T(n/2) + n
n
n/2
T(n/2) = 2 . T(n/2^2) + n/2
n/4
n/4
T(n/4) = 2 . T(n/2^3) + n/2^2
n/8
T(n/2^3) = 2 . T(n/2^4) + n/2^3
continue expanding
until problem size
T(n/2^k) = 1
reduces to 1
Total cost = L_c + I_c   L_c: cost of leaf nodes, I_c: cost of internal nodes
n = 2^k => k = lg n
L_c = 2^k = 2^(lg n) = n^(lg 2) => n
I_c = k . n
I_c = n lg n
Hence ∴ T(n) ∈ O(n lg n)
```

## Page 6
```text
n = 1
Q2) T(n) = { 1  n=1 ;  2T(n/2)^2 + n^2  n>1 }
Q3) T(n) = { 1  n=1 ;  3T(n/4) + n^2  n>1 }
assume n is exact power of 4
Ans)
= 3T(n/4) + n^2
T(n/4)
n^2
n/4  n/4  n/4
3
n^2
= 3T(n/4^2) + n^2/4^2
n/256  n/256  n/256
3/16 n^2
= 3T(n/4^3) + (n^2/16^2)
9/16^2 n^2
T(n/4^k) = 1
T(1)
L_c => n = 4^k => k = log_4 n
L_c = 3^k => 3^(log_4 n) => n^(log_4 3)
I_c = n^2 . [(3/16)^0 + (3/16)^1 + ... ] =>
```

## Page 7
### Divide and Conquer
```text
Divide Conquer
a11
a12
A11
a13
a21
A12
a14
B11  B12
B21
c11 = a11*b11 + a12*b21
c12 = a11*b12 + a12*b22
c21 = a21*b11 + a22*b21
C11 = A11B11 + A12B21
```

## Page 8
```text
```

## Page 9
### Recurrence Relation (Code Analysis)
```text
Recurrence Relation
* Tree
· Convert to T(n) form
void Test(n) {
T(n)
O(1)
if (n>0) {
for( i=0; i<n; i++) {
O(n)
print
O(1)
}
Test(n-1);
T(n-1)
}
Sum => T(n) = T(n-1) + n + 2
T(n) = T(n-1) + n
b) solve T(n) = { 1  n=0
{ T(n-1) + n  n>0
T(n)
time taken
n
n
T(n-1)  n-1
n-1
T(n-2)  n-2
T(n-3)  n-3
n-3
T(2)
2
T(1)  1
T(0)  1
=> 1 + 2 + ... + n-1 + n = n(n+1)/2
=> O(n^2)
```

## Page 10
```text
Q2) T(n) = T(n-1) + log n
T(n)
log n
T(n-1)
log(n-1)
log(n-2)
log(1) + log(2) + ... + log(n-1) + log(n) =
log 1 + log 2 + log(n-1) + log(n)   Log Property
log(1 x 2 x ... x (n-1) x n)
log(n!)
=> Log n!
-> No tight bound
-> upper bound for n! = n x n-1 ...
=> log(n x n x ...) = n Log n
n log n + 2(n/2 log n/2) + 4(n/4 log n/4)
n log n
2^k n^k log n^k
= 2^k
```

## Page 11
```text
Q3)
T(n) = { 1 ; 2T(n/2) + n }
n
n/2
n/2
n/2^2
n
n/2^2
n/2^k = 1
n = 2^k
k steps
n.k steps
log n = k
=> n.k =
n.log n
Q4) T(n) = 4T(n/2) + n^2/log n,  T(1) = 1
n^2 / log n
(n/2)^2 / log(n/2)
= 4(n^2 / (4 log(n/2)))
log(n/2)
n^2
so
=> n^2 / log n + n^2 / log(n/2)
```

## Page 12
### Rabin Karp
```text
Rabin Karp
Abdul Bari
Q1) Text = a a a a a b
pattern = a a b
Ans)
size of pattern
so  a a b = 1+1+2 = 4
m = 3
a = 1
hashcode
b = 2
hash func
c = 3
1+1+1 = 3 x    1+1+2 = 4
1+1+1 = 3 x
Θ(n-m+1) average
Θ(nm) worst if spurious hits eg
Q2) worst case
c c a c c a a e = Text
d b a
= Pattern
dba = 4+2+1 = 7
c c a  c c a a e
hashcode matches but string doesnt
mod by number if too big
Actual Rabin Karp
dba = (4 x 10^2 + 2 x 10 + 1) = 421
P[1] x 10^(m-1) + P[2] x 10^(m-2) + P[3] x 10^(m-3) ...
(331 - 300) x 10 + 3
c c a c
3x10^2 + 3x10 + 1 = 331
```

## Page 13
### Finite Automata
```text
Finite Automata
Q1)
Text: a a a b a b a a b a a
pattern: a a b b
Σ = {a, b}
0 -a-> 1 -a-> 2 -b-> 3 -a-> 4 -b-> 5
split into 2 exams
Prefix match
Transition Table / Finite Automata table
abb = ab   bb
a   b
0   1   0
1   2   0   -> ab = 2 prefix value
3   4   0
-> aaa = 2
aabab = 0
aabaa = 2
4   2   5
5   1   0
aababa = 1
aababb = 0
Text = a a a b a b a a b a a
0 1 2 2 3 4 5 0 2 3 4 2
Start
from
final
reached
so pattern
present
from zero
```

## Page 14
### Knuth Morris Pratt Algo
```text
Knuth Morris Pratt Algo
calculate prefix table
of pattern, this will be
pattern abcd abc
used, as values of this table
will indicate where P[index]
will go if mismatch
[ P[i] = P[value-1]
prefix
a, ab, abc, abcd,
suffix c, bc, abc, dabc
value at
prefix table
π or LPS = longest prefix suffix
P1:
a b c d  a b  e  a b f
P = A B C A C B A B
1 2 3 4 5 6 7
0 0 0 0 1 2 0 1 2 0
Array = [0 0 0 1 0 1 1 2]
a b c d e a b f a b c
0 0 0 0 0 1 2 0 1 2 3
a d b c a d a a b c
A B C A C x
0 1 0 0 1 0 1 2 0 0
A B C A C B
A B C A C B A = 1
A B C A C B A B = 2
a a a b a a l d
0 1 2 0 1 2 0 0
Matching
Q1) string:
a b a b c a b c a b a b a b d
1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
pattern:
a b a b d ~ pi table, prefix table
0 0 1 2 0
move i, j by checking, when mismatch move j to mismatch pi value, if j goes to zero move i as mismatch
```

## Page 15
### Heaps
```text
Heaps
* nearly complete binary tree
maxheap
21
· all levels filled except lowest
· value i >= value of parent
· lowest filled from left to right
17  15
· height = O(log n)
14
19
12  13
1 2 3 4 5 6 7 8 9 10
21 | 17 | 15 | 14 | 19 | 12 | 13 | 8 | 5 | 1
8  5  1
root
right child = 2i+1
left
= 2i
parent = floor(i/2)
Full vs complete Binary tree
last level might be unfilled from left to right
of node
Height = number of edges on simplest path from node down to leaf
level = length of path from root to node
height of tree = height of root
level
at level l
· At most 2^l nodes in binary tree - at level l
· 2^(h+1) - 1 = max nodes in all tree
· height = Lg(n)  number of nodes
```

## Page 16
### Building Heap
#### Max-Heapify
```text
* Building Heap
· Adding / Deleting Node  · Node added at bottom (Left to Right)  · removed from top (Right to left)
Max-Heapify
// maintains/restore heap property  L how it works
Lit (Node < child) exchange with larger child. Move down tree until (node>child)
Example
Max-Heapify( A, i, n )
l = left(i)
r = right(i)
if l <= n and A[l] > A[i]
then largest = l
else largest = i
if r <= n and A[r] > A[largest]
then largest = r
if largest != i
then exchange A[i] <-> A[largest]
Max-Heapify( A, largest, n )
```

## Page 17
#### Inserting
#### Deleting
```text
Abdul Bari
* Inserting
O(lg n)
Q1) insert 60 into
1) insert at left bottom
2) compare with parent exchange
* Delete 50 out of
(lg n)
remove
exchange
replace with
last element in array
exchange with bigger child
Before Deleting:
50 | 30 | 20 | 15 | 10 | 8 | 16
1 2 3 4 5 6 7
After Deleting:
deleted element
30 | 16 | 20 | 15 | 10 | 8 | 50
Keep Deleting root:
20 | 16 | 10 | 15 | 8 | 30 | 50
heap
sorted array of Deleted
so
```

## Page 18
### Heap Sort
#### Heapify
```text
Heap Sort n log n
Q1) 10 20 15 30 40  heap sort
insert 10
insert 20
exchange
n log n to insert & form heap = [40 30 15 10 20]
· Now Delete Root
remove 40 exchange
heapify
remove
heapify
[10 15 20 30 40]
[30 15 10 20 40]
(n x log n) for deletion
Total Sort Time = n log n + n log n = n log n
Heapify (n log n)
· In heap sort we created heap by adding it from Left to Right of array 10 20 15 ....
· In heapify create by adding Right to Left
18 is a heap as single
12 40 25 18
no children
to adjust
12 40 15 18
12 20 15 18
```

## Page 19
#### MaxHeapify Code
#### BUILDMAXHEAP
```text
Code:
Array  index  size
· save right, left child index
MaxHeapify (A, i, n) {
· check right, left, node which is longest
l = left(i) = 2i  // store left child
and save in largest
· exchange
· Recall function with (A, largest, n)
r = right(i) = 2i+1
if ( l <= n
&& A[l] > A[i] )
largest = l
else largest = i
if ( r <= n && A[r] > A[largest] )
then largest = r
if (largest != i)
exchange A[i] <-> A[r]
MaxHeapify( A, largest, n )
· moves from Root to leaf = height,
at each level 2 comparison
= 2h
so O(2h) = O(2 lg n) = O(lg n)
BUILDMAXHEAP (A)
(Right to left)
leaves
n = length(A)
already heaps
for ( i = n/2 to i=1 )
do MaxHeapify(A, i, n)
O(n log n)
```

## Page 20
#### 3-ary Heap Questions
```text
Q1) if 3 children Heap give calc for each child
= 3i, 3i+1, 3i+2
b) for 3 children heap
MaxHeapify 3ary ( A, i, n )
l = 2i
m = 2i+1
r = 2i+2
if ( l <= n && A[l] > A[i] )
largest = l
else largest = i
if ( m <= n && A[m] > A[largest] )
largest = m
if ( r <= n && A[r] > A[largest] )
largest = r
if ( largest != i ) exchange ( A[largest], A[i] )
MaxHeapify 3ary ( A, largest, n )
c) What is worst case for search a word in heap
heap search = linear search = O(n)
d) if word is found, its frequency increased, words are sorted on basis of max frequency, Assume a word searched, determined to not be
in heap, what worst case of inserting new word
O(1) inserted at first empty slot left to right.
e) if word search, it is found, what is Big O for updating freq
O(log n), updating freq would call maxHeapify
Q2) is a ascending sorted array a min heap
Yes
```

## Page 21
### Heaps
```text
7
b) This is a valid Min Heap
9
7
6
Y
2
5
12207
11
20
14
18
3
S
12
3
2
Insert 6, 1
-12
6
1 s
y
2 3 9 7 5 12 20 7 11 20 14 18
2
3
9
3
b
13
2
2
3
75
12
26
7 11 20 14 18 12
20
X
3
7
14
1 3 2 7 5 12 6 7 11 20 14 18 12 20
=7 1 3 275
delete root twice
S
14
12
after 1st
20
3
7
$
12
7
11
20
18 12/ 20
4
6
1
9
10
267
8
5
14
12
6
20
12
19
2
4
5
c
7
9
10
"
12
3
```

## Page 22
### String Matching Algo
#### Naive Method
```text
x ≥ y   x is suffix
String Matching Algo
x ⊏ y   x is prefix
Exact or Approx
Preprocessing
Matching time
Naive String
O((n-m+1)m)
0
Rabin
O(m)
O((n-m+1)m)
Finite Au
O(m|Σ|)
O(n)
Knuth
O(m)
O(n)
Revise Rabin Karp
Preprocessing O(m)
Naive method
check valid shift through loop
Text
Naive matcher (T, P) pattern
n = length(T)
m = length(P)
for (s = 0 to n-m)
if( P(1...m) = T(s+1 ... s+m) )
print "Found"
```

## Page 23
#### Rabin Karp
```text
Aryan Mittal's video
Rabin Karp
hash letter into number
Spurious hits eg 'ab' 'ba' = 3
To reduce
length (n)   26 characters
2 1 0
radix   index
S = a b c
a*(26)^2 + b*(26)^1 + c*(26)^0
0(92)4)+,(92)#9
b2+c☆2°
base value
such that no
repetition eg
2
20232
if we use '2'
2
X
+3
4+4
=n
二
mach
so as letter (0-25) we chose number greater than 25, which 26
92 ym sz vo rab sanv
T = "a b c d ..."
n = 10^5
↓50
mod = 10^9+7
hash = a*(26)^(n-1)
+ b*(26)^(n-2) ...
so
hash = a*(26)^(n-1) % mod + b*(26)^(n-2) % mod
a my sunds fy
nandleit
value to 10^9+7
handle it later
ezan
```

## Page 24
```text
Q1, String = "a c a b b"
P = "a b b"
for next hash wind use out
by -1*(26)^2 then *26
then + b*26^0
a c a b b
a b b
hash
1*(26)^2 + 3*(26)^1 + 1*(26)^0
a(26)^2 + b(26)^1 + c(26)^0
1(26)^2 + 2(26) + 2*1
个
0(92)1+,(97E(92)x1)
*26 - a(26)^m + c(26)^0
multiply by hash / radix
minus leading letter hash
Hash(s+1) = hash(s)*26 - s[i]*26^m + s[i+m]
26^m = maxweight
Putes
moadie
Rabin Karp ( T, P, d, q )
i
Computing P using Horner's rule
P[1...m] = "3457", m=4 so
p = 7 + 10(5 + 10(4 + 10(3)))
p = 3457
small p is hash of pattern
small t_i is hash of Text's index
q: mod
```

## Page 25
#### Rabin Karp Matcher
#### Finite Automaton
```text
d=26
mod
Rabin Karp Matcher (T, P, d, q)
n = length(T)
m = length(P)
h = d^(m-1) mod q
mogmodg
p = 0
11
t0 = 0
// preprocess
for( i = 0 to m)
p = (dp + P[i]) mod q   // calculate hash of P
t0 = (d t0 + T[i]) mod q   // calculate hash of t0
for ( s = 0 to n-m)
if (p = ts)   // hash matches
"Pattern occur found"
1
1
if ( s < n-m)
then ts+1 = d(ts - T[s+1]h) + T[s+m+1] mod q
26
(92)+V-
12×71
Finite Automaton
revise Page
- Table
- Transition thingy
L Trace text if state reached found
Pattern - state function
σ(bab) => b=b ✓ ab≠ba = 1
length of longest prefix of P that is suffix of x
pehpHati
badaa = b≠a, ba≠aa, bad≠daa = 0
```

## Page 26
#### Prefix Table
```text
Prefix table
ex aaabaaca
a
a
a
a
a
c
a
0
1
2
0
1
aa = 1
35
aaa = aa ✓, aa = aa
aaab ≠ a b✗, aa ab✗, aaa aab ✗
aaaba = a a ✓, aa ba✗, aaa aaba ✗
Q1, P = abab
a) σ(acba) = 1
b) σ(cbabab) = 4
length of longest prefix of P that is suffix of x where σ(x)
Finite Automaton Matcher (T, δ, m)
Transition Function ( P, Σ )
m = length(P)
n = length(T)
for (q = 0 to m)
q = 0
for (i = 0 to n)
for (each character a till m)
q = δ(q, T[i])
K = min(m+1, q+2)
if (q = m)
repeat K = K-1
until
print (Pattern occured)
P_k ⊐ P_q a
δ(q,a) = k
return δ
```

## Page 27
### Graphs
#### Breadth First Search
#### Depth First Search
```text
min spantree
Graph
prim - start at point, select smaller weight node
edge no
Greedy Algo
Dijkstra
Shortest path
vertex
from one node to everyone
edge
Kruskal - smallest edge, that doesn't make cycle  O(E log n)
10
12 153 1415
0
0 x
3
S
1
x
2
y—3
3
X
x1
5
DES.
Breadth First
BFS
use queue, bool visited array
e.g
0
—2—4.
Push edge into queue = 3
explore 1 = 3 push into queue
3
5
145
Lexpue
4
uireay
DFS
backtrack
if dead end
降
5
3
```

## Page 28
#### Dijkstra's
#### Prims
```text
Dijkstra's
choosing
unvisited node = {A, B, C, D, E}
A: 0
B: 4
3
C: 2
2→C
D: ∞
E: ∞
same as prim but add total
cost and cost if next step added then consider
Prims
L code
```

## Page 29
### Huffman Coding
```text
decoding
substitute code with character
Σ = {a, b, c, d}
technique for data compression
example
C1 { a=00, b=01, c=10, d=11 }
code
then bad is encoded to
length = 20
= 8 × 20 =
010011
8 bit per letter Ascii
L 010011
can be bad or acaa
freq/count
code
A
3
000
3×20 = 60 bit
Prefix of one
character code
B
5
001
+ 5×8 + 5×3 = 55 bit  } table
can't be equal
C
6
010
7
011
D
Binary tree
100
shows optimal
E
2
code each
node is a character
Variable size code
some character appear more = give smaller size
arrange lowest count
A
3
001
make node of smallest node, combine 2
B
5
10
often
C
6
11
D
01
4
E
2
000
0
11
freque
0
0
4
5
6
2
E
A
3
D
B
C
Meve  bit
=3x2+3×3+90+
9+2xS+2xht
y0
```

## Page 30
```text
Space complexity of Directed Graph = Big O (V+E)
time com of BFS
= O(V+E)
vertex edge
No of edges in DFS
= V-1
Prims
is greedy because each step chooses minimum weight
Prefix constraint in Huffman = No codeword can be prefix of any other
codeword
Time com = O(C log C)
Minimum Edges in connected graph = V-1
Max ' ' ' ' ' ' = V(V-1)
2
```

## Page 31
### Final Exam Format
```text
Final algo
May 25th, Saturday
25 shatqs (3 min each)
Part A:
3 Qs Time Complexity
3 Qs String Matching
3 Qs Amortized Analysis
Part B
2 Qs Recurrence
2 Qs Divide, conquer
5 Qs Graphs, Greedy
Part C  2 Qs sorting
2 Qs Heaps
3 Qs Hashing
Q2, DP 50%
L Q1, Rod cutting or Matrix chain or LCS (15%, 25 min)
Numerical from OBST, 0-1 Knapsack, Bellman Ford or
Floyd Warshall (15%) 25 min
Unseen problem (20%, 20 min)
```

## Page 32
```text
```

## Page 33
### Dynamic Programming
```text
Dynamic P
Problem must be recursively divisible in sub independent
problems
Worst case exp sol
Solve each sub-P just once and save
4 steps
1- characterise optimal solution structure
2- Recursively define optimal value of solution
3- calculate value, iteratively / Rec use memoization
Fibonacci tree
fib5
fib4
fib3
fib2
fib2
(b)
fib1
fib0
fib1
Not memoized solution - subproblem get repeated, O(2^n)
Memoized top down
```

## Page 34
#### Top Down Memo
#### Bottom Up
```text
Top Down Memo
recursive
int[] d = new int[n+1];
for(int j=2; j<=n; j++){  // set arr to -1
d[j] = -1;
d[0] = 1;
d[1] = 1;
int fibonacci( int n){
if (d[n-1] < 0)   // if value isn't saved calculate it and save
d[n-1] = fibonacci(n-1);
return( d[n-1] + d[n-2]);
1
fib(4)  if (d[4] < 0)
(1>(hSp)+!
S
=({194
b2fib(1)=1=
passed into fib(5)
return
return
11=2
A
Bottom Up - iterative
memo[];
Fib (n){
memo [0] = 1
memo [1] = 1
for ( 2 to n){
memo[i] = memo [i-1] + memo[i-2] ;
return memo(n);
```

## Page 35
### Rod Cutting Problem
```text
Rod cutting Prob
t rozl
Rod
3
n inches
Table of Price
inches
2
3
y
s
price
s18
9
Find max price if cut to be sold in any way.
n = 4
combainsrs9
181
s5
11s'0
combinations
pla]
9
1,8   5,5   8,1
18
1,1,5   1,5,1   5,1,1   1,1,1,1
Top Down
cutRod (p, n)
if (n == 0) return 0;
price
q = -∞;
// zero arr
for ( i = 1 to n){
q = max(q, p[i] + cutRod (p, n-i))
}
return q;
4
Top Down (3)
2
17
```

## Page 36
#### Top Down with Memo
```text
Top Down with Memo
CutRod(p,n)
int main (){
memo[n] = -1;
Rodcut( p, n, memo){
if (memo[n] >= 0) return memo[n];
if (n == 0) q = 0;
else q = -1;
for ( 1 to n){
q = max (q, p[i] + Rodcut (p, n-i, r))
}
r[n] = q   // save value in memo
1/ save valuein memo
return q;
}
Before memo:
After Memo
3
0
QQ
0
0
2
repeated
T(n) = 1 + sum_{0}^{n-1} T(j)
```

## Page 37
#### Bottom Up (Rod Cutting)
```text
Bottom Up
(O(N^2))
CutRod(p, n)
int mem[n] = -∞;
mem[0] = 0;
for( j = 1 to n)
for( i = 1 to j)
q = max(q, p[i] + mem[j-1]);
mem [j] = q
return mem[n];
* Extended
smaller pieces
int mem[n], s[n] = -∞
length that give the corresponding mem[j] value
mn [.
r[0] = 0;
for( j = 1-n){
for ( i = 1-n)
if (q < p[i] + mem[j-1])   // if more profit
q = p[i] + r[j-1]   // save new mem
s[j] = i;   // save smaller rod size
ejdeg
r[j] = q
return (r and s)
1 2 3 4 5 6 7
P[i] = 1 5 8 9 10 17 17
Output for n = 7
S
10
2
3
9
mem
0 1 5 8 10 13 17 18
8
10
13
17
s  0 1 2 3 2 2 6 1
1
S
0
2
2
```

## Page 38
### Longest Common Subsequence
```text
Longest Common Subsequence
Problem: string 1: abcdefghi
2: cdgi
LCS = cdgi
er
eg 2)
1: abcdefghi
2: ecdgi   lines must not intersect
c,d intersect e so
pasutou
LCS = egi ✗
but
0P
LCS = cdgi
pa ba
eg 3)  a b d a c e
b a b c e
bace } both same length
abce } both write
Recursive with memo  O(2^n)
int LCS( i, j){
if ( A[i] == '\0' || B[j] == '\0') return 0;
else if ( A[i] == B[j]) return 1 + LCS( i+1, j+1);
else
return max(LCS(i+1, j), LCS (i, j+1));
}
for segy
→abcd
b 1a
A[0]：18[1]
u,a=1
=2
b1b
1二9句
dyc7-18 ixpilitin
0,4)
dcJ.
a,5)
1=0句0=20√
d0=1
101(0+1
6->1
```

## Page 39
#### Memoization
#### Bottom-Up (LCS)
```text
(x : vaar)
Memoization: O(m×n)
cd
10
algorithm was top down but table filled from bottom up
b
2
2
toponon but
a
1
D
tabre fMed Rrm
10
dis
bottonrtoug
b19
da
B=2
P
106
a
=1
di)
#②0
9
Dontheve
Don't have to make calls if memo
tomeveals
Bottom-Up
if(A[i] == B[j])
LCS[i,j] = 1 + LCS[i-1, j-1]
else
LCS [i,j] = max{ LCS[i-1, j], LCS[i, j-1] }
.if
b
Mnotch
LCS = where arrow goes diagonal
d
d
diagral
C
场
0
0
0
$d.16
0
6
0
0
compare with column, if matched +1 diagonal element
0
e
22
+1 diagrat
```

## Page 40
```text
one
Check with column ->
equal
add +1 to column
translate the dry to code
max(<,^)
not equal
紅pn
Code:
for( i = 0 to n){
mem[i, 0] = 0;  // initialize first row, column 0;
for ( j = 0 to m){
mem[0, j] = 0;
for( i = 1 to m)
for( j = 1 to n)
if (x_i = y_j) c[i,j] = c[i-1, j-1] + 1;
b[i,j] = "↖";
else if ( c[i-1, j] >= c[i, j-1])
then c[i,j] = c[i-1, j];
01
D
O
```

## Page 41
### Matrix Chain Multiplication
```text
Matrix Chain Multiplication
A1 . A2 . A3 . A4
5x4
4x6 6x2 2x7
A x B
= C
for this one
element (1st Row
in 1st column)
so 5 x 3 = 15 x 4 = 60
5x4  4x3
5x3
for second element (1st row x 2nd column)
must be same
Which pair should I select such that total cost of multiplication
A4
is minimum
A3
Possibilities
((A1 . A2) . A3) . A4)
((A1 . A2) . (A3 . A4))
A1  A2
A3  A4
T(n) = 2nCn
n+1
T(3) = 5
```

## Page 42
```text
sizes = 2x3 3x4 4x2
A1 x (A2 x A3)
(A1 x A2) x A3
3x4 4x2
2x3
2 3 3 4 x 4x2
3 x (4 x 2) = 24
2x3
=> 2x3x2 = 12
=> 24
=> 36
+ 2x4x2 = 40 multiplications
24
matrix 1
Cost [1,3]
matrix 3
so
A1 x A2 x A3
(A1 x A2) x A3
C[1,2] = 24   C[3,3] = 0
A1 x (A2 x A3)
C[1,1] = 0   C[2,3] = 24
2 3  3 4
4 2
C[1,2] = 24
C[3,3] = 0
d0  d1  d2  d3
C[1,2] + C[3,3] + d0 x d2 x d3 = 40
C[1,1] + C[2,3] + d0 x d1 x d3 = 36
```

## Page 43
```text
min
C[i,j] = { C[i,k] + C[k+1,j] + d(i-1) x dk x dj }
i<=k<j
2(n-1)
root matrices.
C(n-1) = possible parenthesis combinations
n+1
2(3)
Q1) A1 x A2 x A3 x A4
C3
= 14
4
d0 d1  d1 d2  d2 d3  d3 d4
k=1  C[1,1] + C[2,4] + d0 x d1 x d4
C[1,4] = min
k=2
C[1,2] + C[3,4] + d0 x d2 x d4
i  j
1<=k<4
k=3
C[1,3] + C[4,4] + d0 x d3 x d4
A1 x (A2 x A3 x A4)
(A1 x A2) x (A3 x A4)
(A1 x A2 x A3) x A4
C[1,1]   C[2,4]
0
C[2,4] = min
k=2
C[2,2] + C[3,4] + d1 x d2 x d4
2<=k<4
k=3  C[2,3] + C[4,4] + d1 x d3 x d4
repetition
Cost
K-Table =
First step
second step
Fill + diagonal
```

## Page 44
### Knapsack (0-1)
```text
KNAPSACK (0-1)
Problem: Find max value such that weight of objects don't
increase exceed limit
item1
V=5$
W=4kg
V=2$
W=3kg
Bag
7kg
capacity
item2
V=3$
V=2$
W=2kg
W=1kg
V=4$
3
W=3kg
At capacity 3, weight
no include
capacity
not include current item
0
1
2
3
4
5
6
7
0
0
0
0
0
can fit
V=2, w=3
with item 1,2
0
2
2
2
2
02
2
2
4
V=2, w=1
2
if we don't include item 3 best value = 4
if we do
items
V=2, w=3
0
2
4
6
5
Continues
F(i,j) = { max( F(i-1,j), vi + F(i-1, j-wi) )
if j-wi >= 0
F(i-1, j)
if j-wi < 0
```

## Page 45
#### Selecting items for best value
```text
look item 1,2 can be added
2
3
16
7
capacity 4 - 1 = 3
0
0
0
0
0
(2,3)
1
0
0
0
2
2
2
2
2
if dont include item 3
2
.0
2
2
2
4
4
4
9
added to value 2 at weight 1
3
0
2
2
67
L The diagonal arrow
is current item weight
minus capacity
2
2
4
6
7
3
0
2
6
7
9
Steps
To select item for Best value
L Check if above smaller
Start from 10 wala box
Yes
No
select
item
don't select item
move diagonal   move up
value above differs (9)
yes
include that item 5
and go diagonal arrow (7)
so item = 2,4,5
include item 4
to 2
above doesn't differ (2)
move up, don't include item
(0)
differ (2)
include item 2
doesn't differ
```

## Page 46
### Bellman Ford
```text
Bellman Ford
A
B
E
A
B
5 nodes = 4 iterations
∞ initialize
Relax edge, go to next
```

## Page 47
### Optimal BST
```text
Optimal BST
OBT is where avg number of comparison lowest
A,B,C,D with Probability = 0.1, 0.2, 0.4, 0.3
B
A
D
Avg comp = (0.1x2) + (0.2x1) + (0.4x2) + (0.3x3)
C
= 2.1
Avg Max Comparison = (0.1x1) + (0.2x2) + (0.4x3) + (0.3x4) = 2.9
C(i,j) = min { C(i,k-1) + C(k+1,j) } + sum from s=i to j of Ps  for 1<=i<=j<=n
i<=k<=j
Smallest Avg Number of comparisons possible
```

## Page 48
#### Construct OBST for given keys
```text
Q1) Construct OBST for given keys
Key
A
B
C
D
prob 0.1
0.2
0.4
0.3
K table
0
1
2
3
4
0
1
2
3
4
0
0.1
0.4
11
1.7
1
1
2
5
3
1
0
0.2
0.8
1.4
2
2
3
3
2
0.4
3
0
1.0
3
3
3
0
0.3
4
5
0
C(i,i) = pi
o Rows = Key+1 = 4+1 = 5
C(i,i-1) = 0
(C(1,0) + C[2,2]) + sum s=1 to 2 of Ps
C(1,2) = min
k=1
k=2 (C(1,1) + C[3,2]) + sum s=2 to 2 of Ps
( 0 + 0.2 )
+ (0.1 + 0.2)
= min
( 0.1 + 0 ) + (0.1 + 0.2)
= min { 0.5  k=1 X  -- crossed for k=1
{ 0.4  k=2
= 0.4  k=2
o Avg comp = 1.7
Ktable = 3 for K(1,4) so 3 = C root of tree
K(1,2) = 2 so B root
C
A B
To find structure
D
```

## Page 49
### Floyd-Warshall
```text
load first row - column
midpoint check if repeats
Floyd-Warshall O(V^3)   shortest path b/w all pair of vertex, negatives allowed
Distance table - keep track of the
graph
path from each vertex
2
2
3
1
3
1
4
0
32
7
2
3
0
2
4
4
0
2
3
4
0
8
2
8
2
4
3
for ( K = 1 to V)
for ( i = 1 to V)
3
8
8
1
8
for ( j = 1 to V)
if ( dist[i][j] > d[i][k] + dist[k][j] )
dist[i][j] =
2
3
4
A[1]
8
8
K = 1 2 3 4
8
4
i = 1 2 3 4
2
j = 1 2 3 4
3
8
8
0
d[1][3] > d[1][1] + d[1][3]
8
∞ > 0 + ∞  X
[2,1] + [1,3] = 3
d[2][3] > d[2][1] + d[1][3]
4 + 2
3 > 4 + -2 ✓ so d[2][3] = 2
3 > 2 ✓
[2,1] [1,4]
[3,1] + [1,2]  [3,1] +
4 + ∞
∞ + ∞
∞
```

## Page 50
### Time Complexity
```text
Time Comp
for ( i = n/2 , i <= n , i++)
// n/2
for ( j = 1 , j <= n/2 , j++)
// n/2
for ( K = 1, K <= n, K = K*2 ); //
n = 2^0 -> 1, 2, 4, 8, 16 ... so 2^K
log 2^K
= log2 n
O(N)
O(n/2 x n/2 x log n) = n^2/4 log n
for ( j = 1 ; j <= n ; j++ )  // O(n)
for ( K = 1 ; K <= j*3 , K++)
inner loop = 3 + 6 + 9 + ... 3n
for ( i = 0 to N)
for ( j = 2 ; j <= n ; j = j*j)
2 + 2^2 + 2^4 + 2^8 = 2^(2^K) = (log2 log2 n)
```

## Page 51
### Hashing
#### Linear Probing
```text
Hashing
Properties
1. Data must determine hash value
2. Use all input data in hash function
3. Uniformly distribute Data
4. Produce very Diff value for similar Data
Linear Probing
L HashFun(k) = K % 10
HF(23) = 23 % 10 = 3 already taken collision
72
43
L so HF(3+1) =
23
135
```

## Page 52
### Amortization
#### Dynamic Table
```text
Amortization
Dynamic table
If overflow - Double size
Worst case - copy elements = O(N)
for n insertion = O(n^2)
no of insertion
2
3
12
13
16
size of dynamic table
8
10
size i
1
2
4
4
8
16
16
16
16
16
16
16
16
cost i
2
3
9
copy, swaps, insert
cost of ith insertion = { i, when power of 2
1, otherwise
series = {2^0 + 2^1 + 2^2 + ... + 2^(log n)}
cost of n insertions = sum of cost i
i=1
Sum series = a(r^n - 1)/(r - 1)
= n + sum 2^j
= 1(2^(log n + 1) - 1)
j=log(n-1)
j=0
= 2^(log n + log 2) - 1
= n + 2(n-1)
2
= 2 . 2^(log2 (n-1))
= 3n - 2
so O(n)
```

## Page 53
#### Potential Method
```text
Potential method
• initial potential of DS = D0
• after operation i  D(i-1) -> Di
Actual cost = ci ,  Amortized cost = ĉi
φ(D0) = 0
potential zero
Amortized cost = Actual cost + change in Potential
ĉi = ci + φ(Di) - φ(Di-1)
overestimated
time comp
> 0 then ĉi > ci overcharged
Δφi
< 0 then ĉi < ci undercharged
• Case 1 = power = 2
ĉi = i + 2 - 2^(lg i) + 2^(lg(i-1))
= 3
Case 2 = Not 2
= 3
therefore O(1)
```

## Page 54
#### Accounting Method
```text
Accounting Method
• ĉi , 2, 3 3 3 3 3
9
10
1
size
2
4
8
8
8
8
16
16
cost
2
3
9
fee ĉi
3
2
3.
3
3
3
3
3
3
bank
2
4
2
4
8
2
4
needed = 2, charged 3, so 1 surplus added to bank
needed cost = 1, charged 2 so 1 surplus added in bank
```

## Page 55
### Huffman Coding
```text
theory behind
Huffman Q3
a) Min bits to encode text using fixed length (3)
Q1) Symbol  F
b) Min bits to encode text using
variable length? (10)
A
6
B
18
Show Algorithm
C
c) show final tree
(2)
25
D
11
E   3
• every left branch = 0
• every right branch = 1
• you can get code for every character
38
B
D
A
C B D A E
1
Redo
D
A
E
25
18
11
```

## Page 56
```text
Summer Semester
```
