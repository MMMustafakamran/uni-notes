# Software Design & Architecture Notes (transcription)

Auto-transcribed from `Sda.pdf` (OCR + AI correction). Diagrams/tables are approximate.

## Page 1
```text
```

## Page 2
### SSD (System Sequence Diagram)
#### Invoking Static Methods
```text
SSD
:system
viewAttendance()
call
L course
instructor
* Invoking static Methods
Calender
report
locales = getAvailableLocales
Java code:
class Register{
void report (){
Locale [] locales = Calender.getAvailableLocales();
}
* : Sale
lineItem [i]: SalesLineItem
Loop
for each sale line item
sl = getSubtotal
```

## Page 3
#### Process Sale
```text
o scenario to SD
examqs.
* Register
loop
condition
If else
: Register
alt
* Process sale
: Register
: Product catalog
makeNewSale();
create()
: Sale
enterItem(itemID,qty)
spec: getProductSpec(itemID)
add lineitem
endSale()
make Payment.
```

## Page 4
### SSD: System Actor Interaction
```text
dy
dt
∫ dy/dt dt = ∫ y . dt
y = e^t + c
* SSD
L System Actor interaction
Dont involve classes
cust interact with 1 system class
o make SSD from Main success
a)
main success
1° cashier starts Newsale
success
2° cashier enter
loop [more items]
: system
: cashier
makeNewSale(date,time)
enterItems( id,qty)
endSale ()
Dotted line
total
make Payment (amount)
coming
back
opt [payment saved] balance.
```

## Page 5
### Sequence Diagram
```text
2) Sequence Diagram
L interaction of objects within system
L UI layer , Domain layer
handles
system interaction
actors
: Student
: Actor
Activation bar
synchronous message
(waits for return)
asynchronous
create obj, height lower at new obj
: Teacher
<<create>>
<<destroy>>
delete
self message
lifeline
s1: Sale
=> Sale s1 = new...;
sales: ArrayList<Sale>
ArrayList<Sale> sales = ....;
o Selfmessage
cancel Transaction
Register
```

## Page 6
#### Return Value
#### Loops
```text
* Return value definition
method 1:
: Sale
: Register
: Sale
: Register
theReport = report
or
report
theReport
: Register
Q) eg
report
locales = get AvailableLocales
Locale[] locales = Calender.getAvailableLocales();
}
[Line items: SalesLineItem]
* Loops : Sale
loop [for each salesitem]
Q.
st = getSubTotal
for( SalesItem& lineitem : lineitems){
to code
st = lineitem.getSu-
}
```

## Page 7
#### If, else
#### Convert SSD to SD
```text
* If, else
alt
else line
Q1)
Convert SSD to SD
:System
:Cashier
makeNewSale()
all arrow going to system
loop [more items]
1- MakeNewSale
enterItem(itemID, quantity)
2- EnterItem
3- EndSale
endSale
total
makePayment (amount)
change
```

## Page 8
### Class Diagram
```text
Register -> sale
* Class Diagram
Student
type
+ name : string = 'Ann'
attribute
variable
registration: course[*]
name
+ register(c:course)
operator
+ isRegistered(c:course): Bool
return type
means could be zero
0..1
Date
Order
date Received
* lineitems
orderline
Bidirectional
*
Person
car
so
Person
Car
carsowned: car[*]
+ owner: Person [0..1]
Shape
*
may override
may add feature
Square Circle Rectangle
Generic superclass may be abstract
width = height
radius: int = width/2
associations of superclass are inherited
```

## Page 9
### UI Layer and Business Layer (Controllers)
```text
(Has A)
Aggregation
Club
member
Company
Report
Composition (Is
* UI Layer and Business layer
obj represents overall system
Facade controller: hide complexity
L shouldn't contain business logic
Session controller
L obj represent a use case
Bloated controller
if does too many operations
design make many controllers
Dispatch
Front controller
uses
Student View
+ isAuthenticatedUser
+ trackRequest
HomeView
```

## Page 10
### Information Expert, Creator, Coupling, Cohesion
```text
*
Information Expert
L class with info
information encapsulation
low coupling
* Creator
L principle states
L object associated should create new class
Coupling
L Dependence of one class on other
o Degree of how much one class
depends/ interacts with other
high
o High coupling = Bad
L changes in one class
require changes in other
Dependence on each other
High cohesion
* Degree of how elements
L how func of class belong together
e.g
or serves a generic function
My Reader
M
validate
e.g High cohesion = filehandler
read from DB
class only handles file
read from web
related operation
low cohesion = Utility
class handles diff file
Skipped
operations, Database connection,
L Javafx
message retrieval.?
L Activity Diagram
```

## Page 11
### Lec 14: Design Patterns
#### Key Principles
```text
Lec 14#
L PV, factory, singleton
* Design Pattern
L is solution to common problems in software engg.
It is a reusable blueprint
L of best practices
L GOF
Gang of four = book
principles
Program to interface
non implementation
favour composition vs inheritance
* Key Principles
1° Program to interface not implementation
L use interface to define behavior instead of concrete classes
L first make interface that defines behavior of obj , define its methods
and then create actual class
2° Favour Composition over Inheritance
o Test Driven Development
L make code which is easy to test
o Flexibility & maintainance
2) Comp vs
Inheritance
Inheritance
o tight coupling , issues if we add
* loose coupling
L more - flexible, secure
a new function to subclass
- secure
- testing (mock methods)
o Use when 'has-a' relationship
o Use when 'is-a'
'car' has a 'engine'
L Dog is an Animal
```

## Page 12
### GoF Design Patterns
#### Design for Change
```text
* Gof Design Patterns
creational patterns : creation of objects
structural
'' : deals with class structures : Inheritance ,comp
Behavioural '' : provide solution for behaviors eg - lose coupling
- flexibility
Creational
Structural
Behavioural
Adapter
Abstract Factory
chain of responsibility
Builder
Bridge
command
Factory method
Composite
observer
Prototype
Decorator
strategy
indirection:
Facade
singleton
Visitor
To decouple two
classes and
Flyweight
Memento
assign responsibility
Proxy
to a mediator
* Design for change
- Identify Areas of change : minimize impact of these areas
- Key Principles
L Protected variation;
Use - indirection
- polymorphism
to provide stable interface for changing functionalities
eg Handling Persistence
L Student
Persistent Handler
Persistent Handler
DB
saver
Handler
Student
OracleDBHandler
option1 o Instead of Student directly writing
SQL X - low cohesion
option2 o user connect with DB handler X
- high coupling
option3 o write to Interface -> Persistent
```

## Page 13
#### Factory
#### Singleton
```text
* Factory
problem: who should be responsible for creating complex objects
solution : Factory class
L encapsulate creation logic
L avoid coupling of obj and its creation
L Benefits
eg
- Hides complex creation logic
Persistance Handler
can implement caching/recycling for obj management
Persistance Factory
Student
OracleDBHandler
so
class P_Factory {
P_DBHandler obj;
public P_DBHandler createHandler (name){ //create and return P_DB
obj = new OracleDBHandler ('Name'); //inheritance
return obj;
object
* SingleTon
Problem: Ensure a class has 1 instance and provide global access to it
solution: use a private constructor and static method to return instance
* Private constructor : Prevents external instantiation
* Static Method
L Return created cached instance
Singleton
```

## Page 14
```text
class Singleton {
private static Singleton instance; private Singleton() // Prevent outside access of constructor
public static Singleton getInstance(){
if ( instance == null) new Singleton   return instance;  }
Combined code:
```

## Page 15
### Lecture 15: Strategy & Observer Pattern
#### Observer Pattern
```text
Lecture 15#
Strategy & observer pattern
observer : Decouple subject-observer communication
concluded
Benefits:
adapter : Bridge incompatible serv interfaces
strategy : simply algorithm selection, improve flexibility
* Observer Pattern
L Purpose
o establish 1-M relationship
instagram
o Subjects change state , all observer notified
e.g
celebrity (subject)
followers (observers)
UML:
observer
Subject
update
observerState = getState
Attach(observer)
Detach(observer)
for all observer
notify()
observer
concrete
update()...
observerState
subject
concrete subject
setState
getState
return
subjectState
class
<<interface>>
<<interface>>
observers: list<observer>
Subject
observer
+update
+attach(observer)
+notify()
concrete
+update(content)
observer2
concrete observer1
concrete
Concrete
Subject
```

## Page 16
#### Adapter
#### Strategy
```text
* Adapter(structural) /wrapper
L bridge b/w incompatible interface
e.g changing Adapter
Eg example
Jubilee Insurance
Hospital - Adapter
Meezan Insurance
Faysal Insurance
L> Adapter implements insurance
* Strategy
L defines family of algorithms encapsulated &
e.g Sort
o Sort is Context class
L context class doesnt know which
algo to choose instead client specifies
eg
<<interface>> RouteStrategy
Navigator
-routeStrategy
+ buildRoute(A,B)
Road strategy, Public Transport
walking strategy
* UML
Context
<<interface>>
strategy
-setStrategy
execute
Client
strategy
execute
```

## Page 17
### 3 Tier Architecture
#### 2 Tier
```text
3 tier Archi
3 logical
and physical tiers
1- Presentation GUI - collect info from user
2- Application
3 - Data tier - Database (stores Data)
Tier vs Layer
o functional division on
o functional division on software only
software that runs on
e.g
contacts App on phone
different hardwares
L 3 layer
but 1 tier
Business
Database
layer
layer
o each tier runs on diff machine, have seperate os, custom hardware
Benefits of 3 tier
o Presentation can't directly access Data layer
*
2 tier
L client/server
UI) Business
Logic
server
client
Adv
DisAdv
o easily switch with diff database
o tight coupling
o Heavy load on server
o Potential congestion
```

## Page 18
#### Benefits of 3 Tier
```text
Benefits of 3 tier
* Seperation of Logical, physical; * seperate OS on each tier can be run
* Custom Machines (specialized) without impact on other
* Faster Development : each tier can be developed simultaneously
* Improved scalability
* improved reliability : outage of one tier less impact
* improved security
```

## Page 19
### Lec 13: Package, Component, Deployment, Activity
#### Package Diagram
#### Class Package Diagram
```text
Lec 13#
Package
component
Deployment
Activity
1- Package
o use case Design -> usecase Package design
deposit
Check
banker
withdraw
balance
Maintenance
Login
Modify
maintenance person
2. Class Package Diagram
ATM
transaction
Withdraw Deposit
Maintenance
+deposit
public class
L part of public interface
o UC can make all classes private and add a
public facade class
```

## Page 20
#### Component Diagram
#### Artifact
```text
a import F but
F already present
so name it F'
import : functionality imported
Access : requires assistance eg
<<import>>
<<access>>
Component Diagram (special type of class)
L module system
L interacts through Interface
L reused , replaced , combined
L Black Box (hidden inner) or White box
required
<<component>>
Component
Another comp
provided
interface
ball socket
= black box view
Artifact
L physical file eg app.exe or user-saved
java table
<<manifest>>
<<component>>
<<artifact>>
order.java
order
```

## Page 21
### Deployment Diagram
### Activity Diagram
```text
Deployment Dia (Virtual hardware with S/O)
Shows
Components
Connections
Dependency
Node (Hardware)
<<device>>
<<device>>
: webserver
<<RMI>>
Applicationserver
<<JDBC>>
DBserver
Student
link
: container
<<jsp>>
artifact
Node
<<message>>
Activity Diagram.
ATM Machine
Bank
Customer
start
Insert card
Authorize
[valid]
[Invalid An]
Amount Enter
Enter pin
check balance
fork
Deduct amount
Collect money
End
```

## Page 22
```text
```
