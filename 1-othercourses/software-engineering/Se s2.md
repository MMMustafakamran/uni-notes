# Software Engineering Notes (transcription)

Auto-transcribed from `Se s2.pdf` (OCR + AI correction). Diagrams/tables are approximate.

## Page 1
### Cost Estimation
#### Techniques
#### Algorithmic
#### Estimation by Analogy
#### Expert Judgement
#### Parkinson's Law
#### Pricing to Win
```text
SE
sessional 2
- Project Mana.
- Project Scheduling
- ,, Architecture
- ,, Cost estimation
(12) Cost Estimation
Fundamental Question: How much effort? How much time to complete? Total cost of activity
L salaries, insurance (premium)
L cost of buildings, communication, Hardware
1.
Techniques
Algorithmic
uses formula based on historic data
and software size (Function point, COCOMO)
Estimation by Analogy
Compare project to previous similar past project
to estimate cost
Adv
DisAdv
Not Possible if no prior
Accurate if data available
project.
Requires maintained cost database
Expert Judgement
Done by experienced expert in software development and
application
Adv
Cheap, maybe accurate
If not expert = inaccurate
Assume project cost determined by available resources as they can be restricted
Parkinson's Law
eg "less developers", Work expands to fill time
Example: project deadline = 15 months, 5 people available so effort
estimate is 60 person months
Dis
Adv
- unfinished system
- No overspending
Pricing
to Win
```

## Page 2
#### Functional Point Analysis
```text
Pricing To Win
L set cost based on customer budget
DisAdv
Adv
Help secure contract
Poor customer satisfaction
estimate size/complexity of function
estimating based on functionality provided to user
Functional Point Anal-
L 1st step: identify counting boundary
being measured and external
application or uses
FP = UFP x (0.65 + 0.01 x sum of GSCs)
Unadjusted Function Points: calculate by number of each type of component x corresponding weight.
and summing up
5 factors
Value Adjustment Factor: Factor to adjust UFP based on (GSCs) General system
characteristics e.g performance, usability, complexity
F=
5 unadjusted Function Points
count
Transactional Function type
1, EI external inputs e.g user search form, product search form, add to cart form
2, EO '' output e.g confirmation email, order summary page, invoice gen = 3
3, EQ '' enquiries e.g product availability check, order status = 2
Data function type
=
2
4, ILF Internal logical files: user data, product catalog, order details
= 3
5, EIF external interface file: Payment gateway interface, third party shipping interface
```

## Page 3
#### Value Adjustment Factor
```text
ranking
calculated
Component
Low complexity
Avg
High
EI
3 x 3
4
6
EO
4 x 3
5
7
EQ
3 x 2
4
6
ILF
7 x 3
10
15
EIF
5 x 2
7
10
sum cases
14 factors
Value Adjustment (VAF)
value (0-5)
1, Data Communication
high influence
give value for each
2.
of 14 steps from
3 Performance
0-5
4
sum all values
Range will be
(0-70)
7
complex Processing
max possible
Reusability
value of total sum
12
13
14
Q1. For project these are UFP
= 606
Q1
EI = 30 x 4, EO = 60 x 5
EQ = 23 x 4
ILF = 08 x 10
EIF = 02
x 7
weighting factors are 4, 5, 4, 10, 7 respectively, and out of 14 factors 4 factors not applicable
and others have value 3. Find total value of Function point metric
FP = UFP x VAF
= UFP (sum of (weight x )) x (0.65 + 0.01 x
= 606 x (0.65) + 0.01 (4 x 0 + 10 x 3)
= 606 x 0.65 + 0.01 (30)
```

## Page 4
#### COCOMO
```text
human
Cocomo
duration
Learn calculate
effort time from KLOC lines of code
Three levels
- Basic
- Intermediate
- Detailed
Development modes
size of Project
Nature, Innovation, Deadline, Dev Environment
organic
2 - 50 KLOC
small size, eng familiar
Little
easy
project
semidetached 50-300
medium eg utility systems
medium
medium
over 300
Large, Real time, complex
A lot
Tight
ATM, Air Traffic control
SS = E / D
Persons
effort E = a_b x (KLOC)^bb
staff size
unit
duration D = c_b x (E)^db
KLOC
P =
E
productivity
aa bb cb db constant values depend on type of Dev
a
organic
2.4 1.05 1 11
semi
3.0
'' '' '' ''
embedded
```

## Page 5
#### Intermediate COCOMO
#### Detailed COCOMO
```text
Intermediate: Includes cost drivers
Product Attributes
Rely, Data, CPLX
computer
Personnel Attributes
Project A
rating
all given rating:
V low   Low
Nominal
High
V High
Extra high
0.75
0.88
1.00
1.15
1.40
1.4
effort Adjustment factor
E = a_i (KLOC)^bi x EAF
product of all rating of drivers
= 0.75 x 0.88 x 1 x 1.15 ... = 1.1
Detailed
Includes phase wise effort multiplier of software Dev Phase Mp
Planning + requirement
System Design
e.g: Intermediate E = 52.91 personmonths
integ Testing
E = a(KLOC)^b x EAF
Ep = Mp(E)
D = 11.29 months
Dp = Tp D
so
L Phasewise distribution
Effort % and D %
Planning
6-8%
10-12%
S
10-12%
0.7
M
Integration
if we can reuse a pre existing
size equivalent
A = 0.4 DD + 0.3 C + 0.3 I,
adjustment factor
document design
code
integ
design
S(equivalent) = (S x A) / 100
```

## Page 6
### Project Management
#### Key Terms
#### Lifecycle & Processes
```text
CH#09 Project Management
Key Term
Milestone : checkpoint, has description, date, person responsible
Deliverable : work product provided to client
Dependency : activity that can't start until event occurs
Event : end of a group of activities
Scope : Product scope (features/functions), Project scope (work reqd to deliver product)
Slack : delay in activity without affecting due date
LF - EF
Work Package : large section of work, atleast 12 months
Task
: Smaller work, part of work package, 3-6 months, single person
Lifecycle & Processes
Proj manag Life Cycle & Process
Standard approach : Define scope, divide in task/milestone, estimate time/resources
create schedule, review progress, modify plan as needs
L managed by separate Proj manage team
Five Process Group
1. Scope of Proj
criteria
state problem, establish goal, define objectives, identify success,
list assumptions
2. Develop detail Plan
3. Launch Plan.
4. Monitor Progress
5. Close out
```

## Page 7
#### Project Planning
#### Types of Plan
```text
Key Knowledge Areas: Integration/Scope, Time, Cost, Quality, HR, Risk, Communication
Project Planning
L define or strategy to achieve goal
Guide execution
Document assumptions
Document
Facilitate communication
Provide baseline for progress management
Types of Plan
1 Software Development Plan: describe how to develop system
2 Quality Assurance Plan: specify quality & standards
3 Validation plan
: How client will validate system
4 Configuration Management plan:
5 maintenance plan
staff dev
```

## Page 8
```text
```

## Page 9
### CPM Critical Path Method
```text
CPM critical path method
Est Duration
Predecessor
expected days time
9
ES
EF
Q1
1
2
45
LF
ES = start
3
9
LF - duration
Effort of activity
3
1
9
2
4
3
9
Step1 - Forward Pass
3
Step2 - Back Pass
9
1
Step3 - calculate
4
9
8
1
8
9
8
2
9
bigger than EF
9
2
zero slack
3
zero slack as ES = LS
10
18
1521
13
921
6
38
3
9
2
13
15
23
9
12
516
1921
LF - D = 23 - 2 + 1
9
8
11
15
9
15
12
Critical Path: path with zero slack
```

## Page 10
### Project Scheduling
#### Strategic Planning
#### Choosing Projects
#### WSM Weighted Scoring Model
```text
10# Project scheduling
PM (Project Management) enables managers to
manage:
coordinate plans, people and work
Focus on big picture & guide to success
make swift decision during conflict
communicate project detail to upper management + Stakeholders
- set long term goals
- look future trends
- first what new product/service might be needed
SWOT (Strength, weakness, opportunities, Threats) to assess position
- using
Choosing Project
or focus on organizational need
Finance Analysis (NPV net Present value)
Use WSM (Weighted Scoring Model)
WSM
1. identify criteria : what's important (e.g support business goals
2. Assign weight : How important each criteria? Assign % add up to 100%
3. Score Projects: rate each project against criteria
4. Calculate : multiply each score by weight, add to total weigh score,
higher the better
```

## Page 11
#### Project Charter
#### PMP Project Management Plan
#### Monitoring
```text
then need
once Project chosen
formal authorization => Project Charter
document officially
stating - objective
- management
direction
then PMP (Project Management Plan)
L master document coordinates all efforts, guide strategy, execution
...(scope, budget, &1..)
Key Parts of PMP
Introduction : Proj Name, goal, estimates, key people
Organization : How team structure, responsibilities
Processes : How managed (eg Monitoring method, change control
method, risk management approach, staffing)
Work : summary of main tasks
schedule : detailed timelines
Budget :
expert judgement : Help PMs make teams, make execution related decisions
Meetings : Facilitate relationship building
Monitoring
collect/measure performance info
Baseline : PMP states a baseline for performance measured
Changes : inevitable so must monitor them and control them
```

## Page 12
```text
```

## Page 13
### Software Architecture
#### Architecture Patterns
```text
Software Architecture
minimize coupling blw modules
less need to access outside info
max cohesion
contents within module closely related
Package : grouping of system element
Component: replaceable part of a system
Node : physical element existing at runtime to provide computational resource
e.g (computer, router)
Framework:
Platform which provides foundation of developing software
e.g HTML, .NET
Architecture Pattern
1 Pipe & Filter
system that produces datastream
processing steps are 'filters', data flows through pipes
usage : UNIX shell, compiler (lexical analysis -> parsing -> codegen)
DisAdv
Adv
- Not suitable for interactive system
- Easy to understand,
- support reuse
- overhead
- parallel process
- data transformation issues
- simple evolution
2 object oriented
Data hiding, problem decomposition into interactive agents
can be multithreaded / single thread
DisAdv: object must know who they interact with
3 client server
server helps auto to client - email, online banking
Con: server clients must know where server is
```

## Page 14
#### Layered
```text
4 Master-Slave
L master hands work to slave, combines their result
L used in : data replication
5 Object Broker
Adds broker blw client servers so clients don't need specific server
support multiple servers e.g Apache, Kafka
DisAdv: broker = bottleneck
6 Peer to Peer  L peers act both as client and server
e.g Spotify, BTorrent
7 Event based
component reacts to events announced by other component
Announcer don't need to know who will handle event
supports reuse + evolution (adding piece)
DisAdv : lack of control over order of computations
usage: Android dev, notification
8 Layered (N-tier)
layer with abstraction
each layer provide service to layer above it. Request goes down, notification
up
layer can be changed + added
usage : desktop apps
Common layer: UI, Application, Business logic, Data Access
L Design Principle: build bottom up, maintain abstraction level
within layer, keep lower layer lean, specify
interfaces to use
```

## Page 15
#### Repository
#### MVC
#### Architecture vs Design
```text
9 Repository
L central Data (repos) accessed and modified by agents
L control by agent / repos
Adv: Reduce duplication need of data
DisAdv
L Repository = bottleneck
usage: Databases,
10 MVC (Model View Controller)
L Divides interactive application to three parts
model: Core functionality + data
view: UI display info to user
controller: handle user data
Architecture vs Design
'How' - dig into detail of each component (what button do)
The 'what' how components work interact
in big Picture
L Planning a city
each
building a house,
```

## Page 16
### Testing
#### Verification vs Validation
```text
Testing
Q1 1 S/W error: Mistake made by a human during s/w dev process.
Fault (bug): Programming / Design error whereby delivered system doesn't
conform to specification (eg coding error, protocol error)
Failure: softw doesn't deliver the service expected by the user
(eg mistake in requirements, confusing ui)
Fault avoidance: build system so that are fault free
fault detection: detect fault before s/w put in operation.
Fault tolerance:
L build system that continue to operate when problems occur
Testcase
L set of test inputs, execution condition, expected result developed for a
particular objective
Verification
Validation
ensure s/w built correctly by checking if it
ensure s/w meets customer requi. expect
adheres to its specifications.
if product solves intended problem
Are we building the product right?
Are we building the right prod
Defect detection, correction by comparing specification to implem
Focus: confirm product aligns with customer need
Time :
During Dev (unit test)
After Dev (acceptance test)
e.g:
check if triangle problem logic is correct
check if triangle program outputs user expected result
```

## Page 17
#### Types of Test
#### 3 Level Correctness
#### Structure of Test Case
```text
Types of Test
L code inspection
: review code manually
Unit test
: Test individual component(s).
Integration test: how modules work together
System test: test entire system
Compliance test: ensure adherence to standards/regulation
Interoperability test: check if s/w works with other systems
Recovery Test: Test how system recovers from failures
Security
:
Acceptance Test : verify s/w meets user requi.
Regression Test: Ensure new changes haven't broken existing functionality
3 level correctness
(1 test case)
Possible Correctness : Programs works on single input
edge
Probable
: multiple input + test cases
exhaustive
Absolute
: all possible inputs proven mathematically or through testing
Structure of TC
T.C ID : TC001
Description: verify addition function works add two positive int
Module/Requirement ID:
Addition Function
Test Data (input):
input a=5, b=3
input 5,3 into func, execute it, check output
Test steps
expected result.
output: 8
Actual
3
Result
Fail
```

## Page 18
### White Box Testing
#### Statement/Node Coverage
#### Decision/Branch Coverage
```text
Whitebox
Statement/Node coverage
- cover all statement, nodes
weak guarantee of correctness
several input may execute same statements so test statements
void foo(a, b, x) {
=> input 2 0 3
if (a>1 && b==0) {
x = x/a
if (a==2 || x>1)
'||' symbol must cover it conditional coverage
}
stmt coverage = No of stmt cove x100
very weak
Total
x = x/a
x = x+1
path uncovered
because
of or
Decision/ branch coverage
for so cover (a==2 || x>1) this too
coverage = conditions covered
Total
```

## Page 19
#### Path Coverage
#### Cyclomatic Complexity
```text
conditional branch
Demo(int a)
if (a>5)
print(a)
}
No
print(b)
Branch coverage covers
this as well.
DisAdv
L valid for all domain
L no lead to a boundary
ignores branches inside Boolean Exp
Condition
Path
each path checked
less practical
Branch
Decision
all edges checked
if (x==0 || b>0)
make sure it checked for T/F
make sure both x==0, b>0 checked
Path DIA: No of path no longer for loops
some paths not feasible
Cyclomatic complex
V(G) = E - N + 2
= P + 1
shows No of indepe Paths
new
(set = Basis set)
```

## Page 20
### Black Box Testing
#### Equivalence Partitioning
#### Boundary Value Testing
```text
Black Box Testing
L input o/p without internal knowledge of code
Types Error
Incorrect, missing Function :
Interface
: incorrect button behaviour
Database, Data structure
: how data stored
Performance error
: too slow
Initialization & Termination
: when starting /stopping program
Equivalence Partitioning
Adv
1. Identify input domain (ranges, values, conditions)
- Reduce Test bugs
- increase efficiency
2. Partition into VECs (valid Eq class) or IECs (invalid)
3. Test at least one value per class, focus on boundary
- Ensure broad coverage
e.g Age input system
Vec 1  0-4 years (100% discount)
Vec 2  5-15
(50)
Vec 3
16-64 (0)
65-125 (25)
Test case = 3, 6, 18, 69
Boundary Value Testing
error at edges of its equivalence class e.g 5-15 so test cases should include
boundary and just
outside
Strong ECT
Weak ECT
L cover each class 1 time
L Test all combination of EC, e.g system with 3 input variables
e.g A (3 class), B (4 class), C (2 class)
total test cases = 3 x 4 x 2 = 24
```

## Page 21
### Next Date Equivalence Classes
### Software Process Models
#### Agile: XP and SCRUM
```text
Next Date
input = month (1-12), day (1-31), year (1812-2020)
e.g
Poor EC =
Better EC = M1 : {1,3,5-12} {31 days}
M1
1 ≤ month ≤ 12
D1
1 ≤ day ≤ 31
M2 : {4,6,9,11} 30 days month
Y1
1812 ≤ year ≤ 2020
M3 : {2} Feb
Days D1 29
D2 30
D3 31
Y1 : 1900 nonleap year
Y2 : leap year
month
Day
leap year
A
Year
M1
Strong EC : Test case
1
Y1
2
D1
M1
Y2
3
M1
D2
Y1
M1
D2
Y2
M
D3
Traditional
Waterfall  Incremental  Iterative  Prototype  RAD  Spiral
partial delivery
high risk
(Requirements, Design, Implement, Test)
sequential
less
Agile:
SCRUM
Iterative sprints (1-4 weeks)
XP
standards
Product Backlog : user stories
scrum master : entire scrum, 15 minute meeting
team :
simple design
40 hour week
Areas
Sprint Backlog
15 min
Daily Scrum
Sprint Review
```

## Page 22
### User Stories and Requirements
```text
As a user I want to [goal] so I can [reason]
Independent
Negotiable
Valuable
Estimable
Small
Testable
Functional
services, reaction to input, behaviors in specific situations
A user shall be able to search the appointments
Non-Functional
Constraints (reliability, response time)
Requirements
elicitation : gathering
Analysis : n
validation : ensuring requirements meet customer needs
Management
```

## Page 23
#### Requirements Prioritization
```text
Req Prioritization using Weights
Priority = (value %)
Cost % * Risk %
```
