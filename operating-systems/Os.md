# Operating Systems Notes (transcription)

Auto-transcribed from `Os.pdf` (OCR + AI correction). Diagrams/tables are approximate.

## Page 1
### Operating System
```text
Operating System
Faisal cheema
code based, sessional + Final.
Ass (3-4)
12%.
Quiz (4-6)
8%.
sess
32%.
Proj
8%.
40%.
Final
```

## Page 2
```text
```

## Page 3
### What is OS?
#### Serial Process
#### Batch Processing
#### Multiprogramming
#### Time sharing
```text
Q1, what is OS?
provides interface b/w
Hardware and software
Provides GUI
manges hardware resources
Platform to run programs
Os is a software
User
TopDown view
Program
OS
UI
Hardware
* Serial Process
saves value if unpaused
memory
Monitor
Prog 1
Prog 2
Batch Processing
2 programs in memory but cpu can only process 1 program,
-> Multiprogramming
when a program stops e.g cin, other prog proceed.
-> Time sharing
```

## Page 4
### Multiprocessing
#### Cluster Computers
#### CPU works by
```text
Multiprocessing?
multiple CPUs
Register
CPU
CPU
cache
Main memory (RAM)
memory
Programs
one motherboard has one mainmemory,
* cluster Computers
Virtually connect memories
connect virtually, alot of latency.
If cache made common, its called as Multicore
* CPU works by?
fetch -> decode -> execute
CPU looks in cache then in ram.
Ram is directly connected to CPU
CPU is dumb, how can we implement time sharing? = Interrupt.
IVT
interrupt vector table
fetch -> decode -> execute -> ISR
interrupt service routine
Hardware Interrupt (cin keyboard)
checks if interrupt aya
Software Interrupt (Traps)
control shifted to OS
```

## Page 5
#### DMA
```text
DMA (Direct Memory Access) (I/O devices)
input output device
User
user mode
CLI GUI Hardware
system call
UI
Generates req to os to do stuff eg cin,cout
Program execution  I/O operation  Filesystem  Communication  resource allocation
os components
Accounting  Error detection
HAL
Protection
Security
Watch Interrupt illustration
Hardware Bit
0
1
Kernal
mode
user
mode
os-controlled.
```

## Page 6
#### API calls
#### Parameter Passing
### Kernal Architecture
```text
illustrations
L API calls (watch slides)
(Application Programmer Interface) e.g iostream
cout
user mode
sys
write()
* Higher level lang, easier to understand, doesnt more task e.g iterate
* Parameter Passing by using for system calls
Registers (limited data)
Register (by reference)
Stack (runtime stack)
Kernal
main memory
stack
I/O writer
-> Kernal function is not added to stack
X
cout
user mode
* We have seperate stacks for user and Kernal
* Kernal Architecture
L> what is it? Ans = Part of os
always resident part of os in memory
Traditional unix e.g
it OS == Kernal than architecture is
main
mono Lithic, (allot os is in memory)
service procedure
Memory
OS
util procedure
```

## Page 7
#### Layered Architecture
#### Modern style (Microkernal, Nanokernal)
```text
Layered Architure (Not Popular)
Advantage
* Security, due to many layers
user apps
LN
L3
L) Slower, many layer
L2 file sys
nature of program diff, calculator app
L1
want a io layer near while others
L0
H/W
Modern style
* Kernall << os
L way smaller
NanoKernal
L Kernal <<<< os
To make Kernal smaller, divide os into
Essential
Nonessential
- Memmanagment
. File sys
main mem
I/O
OS kernal
essential always in Kernal
- Prog execution
filesys
when wanted U:M -> kernal
can be kicked out of memory
I/O
They are Modular
independent
component communicate through interface.
can add / remove module into memory.
Next class ( Virtualisation)
```

## Page 8
### Virtual Machines
```text
Virtual Machines
```

## Page 9
#### Containerization
```text
Containerization
(e.g Dockers)
App
10gb
App
Bin/Lib
Bin/Lib
Docker engine
can allow app to run on both
OS
linux, window, the app is
VM
I/O Host
Host OS
H/W
H/W
Memory
packaged, uploaded on Docker Hub
Part of Kernal
Prevents hacking
Why software house use Docker
cloud (dockerhub)
DockerApp
cross Platform
Devops, automation.
```

## Page 10
### Process
```text
Process
Kernal
stack
int a
&a = 25;
Data
Heap
Process
address space
Code
C
PCB
D
PC
Stack
register
B
Heap
powerstack
File
Data
Code
Every metaData has register, program counter
Dispatcher part of Kernal, it saves state + register / Pc from cpu
to it's PCB
when interupt made dispatcher activated
only One process can be in running state
2 state Process
Not running
A
F E D - B
timeout
```

## Page 11
#### 5 process states
```text
1- Clock /Timeout.
2- I/O
Process Control Block.
3- Abnormal termination /error
4- Normal Termination
5- Wait for Another proc
5 process states
Dispatcher - always works
on ready queue
Run
Ready to Run
Exit
all proces in exit
states are called
Blocked /out
"Zombies"
Hometask
L unix state proces diagram
5 -> 9/11
```

## Page 12
#### Process Creation
```text
Ready to Run
New
Ready
Run
Exit
Blocked
Blocked suspended
* Process Creation
Shell
Runs binary file.
init
shell
Unix
process hierchy
child
1. Process replicate
a.out
fork().
2. overlay a.out
to new process.
// in linux every Process is a child of a process.
```

## Page 13
#### fork()
```text
a.out
int main(){
shell
process
fork(); //system call to req to make new
a.out
a.out
// a.out replicated, instructions/
text is replicated,
}
Data
all replicated
Stack
heap
pcb - majorly copied.
new pcb will be made for
new process
// C++ if
int fork()
if(0) = False
only
success
1
failure
if(NULL) = F
false
-1
if(100) = T
0
if(-1) = T
if(1) = T
if(-100) = T
fork returns process id of new or child
In child returns 0
if pid = 0 - child process
if pid > 0 - parent proc
Both parent, child continue executing after fork() call;
```

## Page 14
```text
fork - 2
fork()1
fork()2
fork()3
fork()4 fork()5
int pid = fork().
C
P
```

## Page 15
#### Dry Run
```text
int main() {
if( fork()
&& ! fork()) {
if( ! fork() ){
}
cout << "-";
}
cout << "*";
exit();
}
Dry Run
exit
exit
exit
= -**
or = *-*
* Make Process Tree
```

## Page 16
```text
int main(){
fork()
int pid = fork();
if(pid){ // parent
wait();
}else{ // child
}
exit();
}
* Parent/Child
Parent
will be
Ready
Run
in wait
exit
state
child will
Blocked
be in new
state
1- fork() ok
2- Executable Run /overlay binary
int main() {
fork
exec("/bin/ls")
cout << "msg", (ngi)
```

## Page 17
### Interprocess Communication
```text
Interprocess Communication
Ram
Kernal
Kernal
shared memory
Process A
Proc. A
Process B
Proc. B
message passing
You req kernal to allocate
memory, attach process
Process B can access its address,
shared
space area.
having many process share memory at
once is quicker but chaos.
```

## Page 18
### Sessional: Chap 2 Process
#### Process Management
```text
Sessional
Chap2 # 2
Process is a program in execution (sequential)
Process Management
L Allocate necessary resources, memory, processor
L Schedule, watch for processor, utilization response time
L Interprocess communication
L check potential deadlocks
* Process
code (Text)
current activity ( P.Count, Processor register)
Stack containing temp data
L func parameters, return address, local variable
Data ( global variable)
max
stack
Heap ( DMA)
Program
Process
heap
Passive entity
Active
data
static code + static data
Dynamic instantiation of code + data move
text
0
executable file loaded
Program
Process
one program -> many process
multiple user run same prog
```

## Page 19
#### PCB
#### Context Switching
#### Process Creating
```text
PCB (Process Control Block) = Identified by Integer Process ID
L store all data of Process
Process state
Process number
5 state model
process counter
registers
Ready
Running
memory limits
Exit
list of open files
event waiting
Blocked
Suspended
5 state model = better memory, low hit rate
suspend
L Disk I/O faster
L swap process that cause problem
L Periodic tasks with long period
L Suspend child
Context Switching
L save context including Program counter, PCB register
L Move PCB to queue (Blocked, ready)
L select another process
L update PCB
L update memory management data structures
L Restore context
main memory
Process Creating
L Assign pid
L Allocate space
content
Programcode
Data
L Initialize PCB
L Setup linkage
content
L Create or expand
Data
Programcode
```

## Page 20
#### Process Spawning
#### Zombie
```text
Process Spawning
Resource
L P,C share resources
L C share subset of P's resources
- P, C execute same time
- Parent waits until C terminates
Address space
- C duplicate of P
- C has a program loaded into it
Parent = 1
C = 0
child inherits
L stack, memory, Environment, open file descriptors, current working
directory, Resource limits, Root Directory
L Parent inherit
L Process ID
L Timer
L Resource utilization, CPU times
L memory and file locks
* Zombie
L process table still contains exits child
so parent can read
exit status by wait call
```

## Page 21
### Threads
```text
Threads
* Computational Speedup
(Independent Modules)
by Parallel Processing
Slowest thread will slow the whole process
Foreground + Background processing
eg, Microsoft word
editor
spell check
* Asynchronous Process
they run when load less to prevent overloading
Dont run all the time /aperiodly
Modularity
Client Server
network
create Tn -> Run the Required
layer
[R1 R2 R3]
task on Tn
R2
Reuse
```

## Page 22
```text
```

## Page 23
### Priority Scheduling
#### Aging
```text
Priority Scheduling
Scheduler chooses priority
can be preemptive
Static / dynamic
Danger of Starvation
low priority process may never have
Aging
Process
Priority
Burst time
P2 P3 P1 P4
P1
3
10
P2
1
1
P3
2
2
P4
15
conflict, use algo to see which to
if equal priority
Round Robin - gives burst time
FCFS
I/O bound process = higher Priority vs CPU
4 algo SJF, SRTF, RR, FCFS
How many Algo can Run at a time? Depends on Number of Queue
```

## Page 24
```text
```

## Page 25
```text
Priority Scheduling
Scheduler chooses priority
can be preemptive
Static / dynamic
Danger of Starvation
low priority process may never have
Aging
Burst time
Process
Priority
P2 P3 P1 P4
P1
3
10
P2
1
1
P3
2
2
P4
3
15
conflict, use algo to see which to
if equal priority
Round Robin - gives burst time
FCFS
I/O bound process = higher Priority vs CPU
4 algo SJF, SRTF, RR, FCFS
How many Algo can Run at a time? Depends on Number of Queue
```

## Page 26
### Short Job First
### Round Robin
```text
Short Job First
selects process with smallest CPU burst time to exec next
can Remove a Process even after CPU allocated
Pre emptive (SRTF)
Non pre emptive
Avoids convoy, min Avg waiting time
If Two process have same CPU burst time then First Come First Serve
time to execute
= Time completion - Arrival
Time
from
Arrival time  Burst time
Completion time CT
Turnaround Time
Waiting time
P1
2
1
7
7-2=5
5-1=4
4
P2
1
5
16
16-1=15
15-5=10
11-1=10
P3
4
1
8
4
3
7-4=3
0
P4
0
6
6
6
0
P5
3
11
8-2=6
2
9
6
Time spent waiting in Ready Queue
Gantt
chart
P4
P1
P3
P5
P2
6
7
11
CPU
time
Round Robin
Time sharing, similar to FCFS with time quantum
mode = preemptive
If time q increased => RR = FCFS
Next Page
RoundR vs SJF
better IO utilization
starvation for longer process
must estimate length
```

## Page 27
#### SRTF
```text
Arrival time
Time
Quantum
AT  BT
CT
TAT  TQ=3
SJF
Q.1,
P1
0
10
SRTF
P2
5
P3
1
1
P4
6
1
P5
8  2
Time quantum
Good for varying sized jobs
Ready Queue
AT+TQ
P1 P2 P3 P1 P2 P4 P3 P5 P1 P2 P4 P3 P5
Gantt Chart
P1
P1 P3 P1 P2 P4 P3 P5 P1 P2
0
3
9
12
15
18
21
23
6
after 3 sec P1 goes back to ready queue, before that Queue is added by new comers
SRTF
Preemptive
AT
BT
10
P1
2
Queue
P4, P2, P1, P5, P3
P2
1
5
same
P3
4
1
0
4
P5
2
10
P4 P4 P1 P4 P3 P5 P4 P2
P2
2
3
10
check after each sec if new arrival, if yes check BT if less exchange
```

## Page 28
#### Multilevel Queue
#### Feedback Queue
```text
starving for low priority process
Priority Scheduling
that block I/O
priority of for job
Preemptive
Check for 0 arrival time add
Run till next comer
check priority if less dont exchange
if same priority FCFS
Ready/Running
* Multilevel Queue
dispatch
To reduce
latency
Ready Queue
Foreg (Interactive) RR each has scheduling algo
80%  Back
(Batch) FCFS
Given
Time slice
RR
Priority: High
System Proc...
CPU
Interactive Proc
SJF
Medium
Batch
FCFS
Problem
If alot of high Priority system process then Batch will starve
Solution :
Feedback Queue
to CPU
Lowest RR, quan=8
to CPU
Medium
RR, quan=16
FCFS
CPU
Highest
```

## Page 29
### Long Medium Short Scheduler
### Threads
```text
Long Medium Short scheduler
short criteria
CPU utilization, Throughput, Response time, Fairness, scheduling overhead
no of process completed
time spent
time
on context
switching/mapping
I/O process and CPU can work simultaneously eg
CPU  I/O  AT
Process A  2  5
0
Process B
4  2  2
A  B
100%A
100%B
P1 | P1 | P3 | P3 | P3
Ans,
I/O
P2 | P3 | P3 | P2 | P2
CPU
P1
5
0
6
P2 P1 P5 P2 P4 P1
Threads
model of. Program Counter
code
shared
Data
Register set
stack
thread ID
Lightweight
suspending / terminating
process terminates all thread
Parallelization
less time to create/terminate vs Process
Uses
overlay background storage
Asynchronous Processing Save while editing
modularity (too much overhead) - solution thread pool
```

## Page 30
### User Space
### Threads by Kernel
```text
User Space
Kernel not aware
Runtime System (thread library execution)
Allows customized schedulers
Any OS
but
Blocking of thread = block whole process
Thread Library
Adv
DisAdv
create/destroy thread
pass message b/w thread
FAST
block process
greater scheduling
doesn't benefit
POSIX
any OS
from multiprocessor
system
Win32
Threads by Kernel
less efficient than user as Kernel involve for creation / termination / switching
scheduling on thread basis
No blocking Problem
Adv
DisAd
No blocking
slow
Multiprocessor
M to one
One to one
library
user
kernel
space
```

## Page 31
### Interprocess Comm
#### Shared Mem
#### Message Passing
```text
Interprocess Comm
Process = access to memory -> address space
Parent receives exit status of child communication
Two modes
Shared mem
Message Passing
establish region for sharing usually address space
system call for every message
OS syscalls needed to setup memory
send/receive
read/write
No sharing of resource
POSIX API
send ( {destination}, message)
create shared mem
receive ( {source}, message)
id = shmget (IPC_PRIVATE, size, S_IRUSR | S_IWUSR);
Physical
Implementation  Logical
sending process that wants access
shared_mem = (char*) shmat(id, NULL, 0);
Direct
Direct symmetric communication
Direct Assymetric
write to shared mem
send (P1, message)
send (P, message)
receive (P2, message)
receive (message)
Detach shared mem
shmdt (shared_mem);
Problem: Changing identifier of process
all process defn must be updated
InDirect
limited modularity
Uses mailbox / port
1:1
S1 -> mailbox -> R1
specific receiver
shared by multiple receiver
send (A, message)
m:1
A is mailbox
receive (A, message)
S2
1:m
S1 -> mailbox
R1
m:m
```

## Page 32
#### Mailbox Owner
#### Synchronization
#### Buffering
### File Descriptors
```text
Mailbox Owner
responsible for create, delete, send, receive
OS
owner receives messages
termination of process = destroy mailbox
Synchronization
Message Passing by blocking, nonblocking
synchronous
asynchronous
send blocked
until message received
until message available
Buffering (Queue)
No queue capacity
zero capacity
send to block until receiver gets message
Bounded
Process
Process
shared info
Kernel
filesystem
File Descriptors
file struct
file
2
PCB keeps track of open files
files
fd[1]
fd[2]
Pointer
File op
file
read/write
f_mode
File structure pointers read if process opens file
fd[2]
f_pos
I/O operation by reading file descriptor
Pointer to actual file
f_inode
Access to files = standard system calls
f_op  File operation routine
file descriptor 0 stdin
1 stdout
```

## Page 33
### Pipes
#### Named Pipe
#### Redirection
```text
Pipes
Pfd[1] = write
[0] = read
#include <unistd.h>
int arr[2];
pipe (arr[2]) if -1 = error
write (arr[1], "test", 5);
close (arr[0]) //close read end
Named Pipe
char* myfifo = "/tmp/myfifo";
mkfifo (myfifo, 0666)
fd = open (myfifo, O_WRONLY)
write (fd, "Hi", sizeof(Hi));
close (fd);
unlink(myfifo);
Redirection
Process read from file descriptor
close / open method
close(0)
open(filename, O_RDONLY)
Open / Close / Dup
fd = open
newfd = dup(fd); //make current fd the lowest available fd = 0
close(fd)
```

## Page 34
### Assignment 1
```text
Assignment 1
Q3, int main ( int argc, char* argv[]){
if (argc == 1)
else modify code
Ass 2
Q1, Game
int main{
generate Game board
int pipes [Max_Players][2];
pipe( pipes)
pid_t pid = fork();
if(pid == 0){ // child
close read end
player process ( Player ID, ... )
random position x,y
message. player ID = player ID
enter Direction
move
message . action = 0
message . position n
// Send message to main
write (write pipe, &message, sizeof(message));
}
exit(0)
// read message (so it waits
generate new board
```

## Page 35
### Intro to Sync
#### Mutual exclusion
#### How to Protect critical section
```text
18th April 2023
Intro to Sync
Identify critical
parts of code and Remainder Section
section
that X manipulate shared variable
Condition for critical section entering
Mutual exclusion,
no 2 process can occur at same time
Don't assume speed of execution, no of CPU
No Process should await forever to enter critical section
No process running outside critical section, or remainder section shouldn't block
critical process
How to Protect critical section
next free slot
Printer
Read nfs=in
print queue
write file in nfs
queue is Producer consumer problem.
inc in
nfs=in:
A1 => nfs=5
A2 Adoc
B1 nfs=5
B2 Bdoc
A1 nfs=5
Adoc
A2
A3 in=6
B1
B2
```

## Page 36
#### Solving OS
```text
Program/App level
Solving OS
1- Based on software solution
2. H/w solution
3. OS solution
1, S/w
bool Flag = T
This loop prevent 2 critical
process to enter at same time
but CPU intensive
(1) while( Flag == False){
Flag = false;
Lock
(2) C.S()
Flag = True;
unlock
A and B
A1
A2
B1 as flag false B1 wont enter C.S
A3
A4
B1
B2
B3
B4
During context switching
2 process can enter so one lock
cant prevent this
```

## Page 37
### Conditions
```text
Conditions
1- M.E
2- No gun about speed/num of process
3- Bounded wait
4- Progress
1. while( turn==1)
2. C.S()
3. Turn = 0 ;
4. n_c.s();
5. interested [1] =
```

## Page 38
#### Lamport Bakery algorithm
```text
Problem: Sign
while(1) {
interested [1] = T
1,
2, turn=0;
3) while ( interested [0] = true && turn ==0);
4, CS
5, interested [1] = F;
interested [0] = T
6) ncs ();
turn=1
while (interested [1] == true && turn==1)
interested [0] = false;
ncs ()
turn 0 : 1 : 0
cs  ncs  Not interested for CS
cs | ncs | interested for CS
Lamport
Bakery algorithm - works like Bank queue ticket, assign max numb
```

## Page 39
### Semaphores
```text
Semaphores
P1 P2 P3 P4
Deadlock
It is a Integer
mutually exclusive
CS
Dont allow more to
Binary
Counting
enter.
(0,1)
S=3,2,1,0,-1
(-inf = +inf)
add
from waiting list
P1 P2 P3
used in
entry code
P(); down, wait
CS
V(); up, signal, post, release
exit code
Down( semaphore S) {
when entry code
S.value = S.value-1;
if (S.value < 0){
put process (PCB) in
block list
suspended list sleep();
else return;
UP(
exit code
S.value = S.value+1;
if (S.value <= 0){
mean enter
into CS, not remove from block list
```

## Page 40
```text
Problem: Sign
while(1) {
interested [1] = T
2, turn=0;
3) while ( interested [0] = true && turn ==0);
4, CS
5, interested [1] = F;
interested [0] = T
6) ncs ();
turn=1
while (interested [1] == true && turn==1)
interested [0] = false;
ncs ()
turn 0 : 1 : 0
cs  ncs  Not interested for CS
cs | ncs | interested for CS
Lamport
Bakery algorithm
works like Bank queue ticket
assign max numb
```

## Page 41
### Semaphores
```text
Semaphores
To Prevent Race Conditions
P1 P2 P3 & P4
Deadlock
It is a Integer
mutually exclusive
CS
Dont allow more to
Binary
Counting
enter.
(-inf - +inf)
(0,1)
S = 3, 2, 1, 0
-1
add
from waiting list
used in
entry code
P(); down, wait
CS
V(); up, signal, post, release
exit code
Down( semaphore S){
when entry code
S.value = S.value - 1;
if (S.value < 0){
put process (PCB) in
block list.
suspended list (sleep);
else return;
}
UP(
exit code
S.value = S.value + 1;
if (S.value <= 0){
select process from wake up (list);
}
dont
into CS, not before from block list
mean enter
```

## Page 42
```text
```

## Page 43
```text
OS Final
Wednesday
Chapters
Processes
Threads
Scheduling
Synchronization   Ask sessional
memory Mana
```

## Page 44
### Synchronization
#### Race Condition
#### Requirements
```text
Synchronization
shared mem
write at same time
Results not same
Result dependent on order
Race Condition
can be avoided if no two threads in CS
Requirements
No 2 processes enter C.S
No assumptions made about speed /number of processors
No process outside C.S may block other process
Progress:
Fairness (Nostarvation) : Every process makes progress
Bounded waiting,
Deadlock Freedom : At least one process can make progress
No process wait forever to enter C.S
Before entering CS. A bound must exist on number of time it has entered CS
CS
P1
if infinity bound wait not met
P1 P2
P1 was allowed to enter 4 time before P2 turn
No of time CS used
if e.g 4, 0 then bound wait
```

## Page 45
### Software Solution
#### Lock Variable
#### Strict Alternation
```text
Software Solution
Lock Variable
flag = False => Someone is in C.S dont enter/wait
while( Flag == False ) {} // wait
Flag = false;
// before entering C.S, mark Flag
C.S();
flag = true;
// after exiting
mark flag true
non C.S();
Doesnt satisfy Mutual exclusion and Forgets turn.
Strict Alternation
Process 1
Process 2
while ( True){
while ( true){
// wait for turn
while( turn != 2){}
while( turn != 1) {};
C.S
turn = 1;
C.S();
turn = 2;
non C.S()
non C.S();
Mutual exclusion, Progress X
Process 1 - enters C.S, exits, sets turn=2
Process 1 - enter n.cs - very long
P2 - enters CS, exits, set turn = 1
P2 - verrry short n.cs, exits, enters C.S, waits as turn=1
violation - no process outside
c.s may block
although it was P1's turn P1 was not interested
```

## Page 46
#### Peterson's algorithm
#### Lamport's Bakery
```text
Peterson's algorithm
while(true){
interested[0] = true;
turn = 1;
while( interested[1] == true && turn == 1){}
C.S();
interested[0] = false;
non C.S();
Lamport's Bakery
before entering CS each process get a number, P with small number enters
Software solution not used
as modern Compilers reorder instructions
```

## Page 47
### Hardware Support
#### Interrupt Disabling
#### Test & Set Lock
```text
Hardware Support
Interrupt Disabling
Disabling interrupt guarantees mutual exclusion
while (true) {
Disadvantages
// disable interrupt
Process gets limited inability to leave program
C.S()
Multiprocessor - disabling interrupt on one
// enable interrupt
processor will not guarantee mutual exclusion
R.S();
User programs dont directly disable interrupts
Using Machine Instruction
Test & Set Lock
0 or 1
unlocked   locked
if a process wants to enter, check lock if locked wait
boolean TestAndSet (boolean *target){
Atomic operation
single operation uninterrupted
boolean rv = *target;
*target = true;
return rv;
}
Process 1
while ( TestAndSet(&lock)) {} // wait if lock true
C.S();
lock = False;
R.S();
```

## Page 48
```text
Test-set doesn't satisfy Bound waiting
if P1 in cs, P2 waiting in loop, P3 enters just as P1 leaves cs
P3 gets CS, P2 starved
exchange -> Process 1 {
int key = 1;
while (key){
exchange(bolt, key)
}
CS();
exchange(bolt, key)
remainder();
}
key = T F  enters; T
bolt = F T  F
Advantage of hardware/Machine ins - Applicable to both uni/multiprocessor
Disadv
Busy waiting consumes processor time
Starvation
Deadlock (if priority based scheduling)
Low priority enters CS
```

## Page 49
#### Bounded waiting
#### Semaphores
```text
Bounded waiting
do{
waiting[i] = true;
key = true;
while( waiting[i] && key){
key = TestAndLock (&lock)
} waiting[i] = False;
//CS
j = (i+1) % n;
while ((j != i) && !waiting[j])
check all
Process in waiting
array
j = (j+1) % n;
if (j == i)
F F T T
lock = false
}
else
searching
thread
waiting[j] = false
// remainder section
and this process
will be entered in CS
Semaphores
wait() //P(){
while (s <= 0) {} // wait
s--;
}
//CS
signal() //V(){
s++;
}
CPU wasted executing the while waiting loop so instead use call
sleep(), block() and wakeup();
```

## Page 50
#### Binary Semaphore
```text
Binary sema
struct bin_sem_t {
enum { zero, one } value;
queue type queue; // can be linked list of PCB
};
int wait ( bin_sem_t s){
int signal ( bin_sem_t s){
if ( s.value == 1) s.value = 0;
if(isempty(s.queue))
else{
s.value = 1;
// block and place current process in s.queue
else {
state (current) = Blocked
p = pop (s.queue);
append (s.queue, current)
state (p) = Ready/Running;
}
```

## Page 51
### Dining Philosopher
```text
Dining Philosopher
Philosopher
eats
Thinks
picks left or right fork, cant pick already
dont interact
picked fork
Represent each fork with semaphor-
if philosopher wants to grab fork, wait() operation
if philosopher releases fork, signal(); operation
binary
semaphore chopstick[5]; = 1;
means free
do{
// right chopstick
wait( chopstick[i]);
wait( chopstick[(i+1)%5]); // left chopstick
// eat (s);
signal( chopstick[i]);
signal( chopstick[(i+1)%5]);
// think
Disadvantages
Deadlock Possible
if all philosopher grab left fork, so
all forks = 0; so when each philosopher grabs right delayed forever
```

## Page 52
### Producer Consumer
```text
Solution to Deadlock
Only only 4 philosopher to sit
one folk will be free if all hungry, grab
left
allow philosopher to pick chopstick only if other chopstick
available.
Use assymetric solution : Philosopher 1 , 2
pick right then left
pick left then right folk
Producer Consumer
Producer not produce if buffer full
empty
Consumer not consume
Both must not produce, consume data at same time
Solution: make use of three semaphores
1. mutex (binary)
2. empty (counting semaphore = number of slots)
3. full counting semaphore = 0
Producer          Consumer
do{
do{
wait (!empty); // wait till empty>0, then decrement
wait (!full);
wait (mutex);
wait (mutex); // acquire lock
// remove data
signal mutex
// add data to buffer
signal (mutex); // release lock
signal empty
signal (full); // increment full.
```

## Page 53
#### Semaphores Drawbacks
#### Monitors
```text
filled slots
int Buffersize = 10; int count = 0;
void producer(void){
produce_item(&item);
if (count == Buffersize) sleep();
//enter_item(item);
count++;
if (count == 1) wakeup(consumer);
Semaphores DrawBacks
Global variable can be accessed anywhere
No connection b/w data controlled, and semaphore
No control /guarantee of proper usage
Prone to Bugs
Monitors
Avoids managing of multiple semaphore
Programming language construct
Control access to shared data
Synchronization code added by compiler, enforced at runtime
```

## Page 54
```text
shared variable must only be accessed
Monitor monitor_name {
by procedure in the monitor
// shared variables
local procedures can only access
procedure P1(){
local variable
}
condition construct   condition x,y
only wait(); signal(); can be invoked
on it
x.signal();
shared data
entry queue
queues of
x,y condition
y -> []
variable
operations
initializer
example
code
Monitor Account {
monitor mutual exclusion {
double balance;
procedure CS(); // critical sect
balance = balance - amount;
end;
return balance;
}
Process P1:
Repeat
CS();
R.S();
```

## Page 55
```text
wait
Signal
Q1) a b a b  ab ab
a b
signal
#include <pthread.h>
increments semaphore
#include <semaphore.h>
using namespace std;
sem_t sem_a, sem_b;
void* function_1 (void* arg){
void* function_2 (void* arg){
while (true){
while (true){
sem_wait(&sem_a);
sem_wait(&sem_b);
cout<<'a';
cout<<'b';
sem_post(&sem_b);
sem_post(&sem_a);
return nullptr;
decrements semaphore
}
int main(){
pthread_t thread1, thread2;
//initialize semaphore
sem_init(&sem_a, 0, 1);
sem_init(&sem_b, 0, 0);
Thread attributes
function argument
pthread_create(&thread1, nullptr, function_1, nullptr)
pthread_create - - -
return value
pthread_join(thread1, nullptr)
sem_destroy(&sem_a);
sem_destroy(&sem_b);
return 0;
}
```

## Page 56
```text
Some Ghost house Problem
Skipped Deadlocks
```

## Page 57
### Memory Management
#### Memory Hierarchy
```text
Memory Management
Memory
efficiency depends on
size : large
Access time : down
time taken
by process to
Per unit cost : down
allocate program in mem
Memory Hierarchy
Register mem
increasing
access
cache mem
time
main mem   primary memory
magnetic Disk
Auxillary
Secondary
memory
magnetic Tapes
Tasks of OS
1. which data should come from secondary to main memory,
at which location
2. CPU generates address for data at secondary mem, but have
access to main, ( OS performs address translation)
Functions of memory management module in OS
track status of each memory location whether free/allocated
Determine Allocation policy
mem Allocation technique
memory protection schemes
```

## Page 58
#### Address Binding
#### Logical vs Physical Address
#### Linking
```text
programs are brought into memory, placed in process queue to Run
Input/Job queue
Address Binding
Bind address to instruction
can be done
compile time
Load time
Run time (Dynamic)
logical vs Physical Address
seen by mem unit, loaded into
generated by CPU
MAR (memory address register)
At compile / load time logical address = physical address
At run time, they differ so MMU ( memory management unit)
Linking
written codes is compiled into intermediate machine
readable (object File)
use certain codes reused e.g Header's inc
Linking combined object to function libraries into
executable file
```

## Page 59
#### Swapping
#### Overlays
#### Reallocation and Protection
```text
Swapping
program must be brought from secondary to main memory, size limited
so swapping to maintain degree of multiprogramming
swap temporarily to backing store (secondary storage)
Operating System
Main mem
Process 1
swap out
P2
Backing store
User space
Overlays
if size of process > amount of mem allocated to it
then overlay used to execute this program
Overlay Keep in memory only data that is needed at that time
when data needed, loaded into space of previously used data
Reallocation and Protection
swapped program must be relocated
cant be sure on location of memory
Addressing
No absolute e.g location variable
Protection
must keep program out of other process's partition
```

## Page 60
### Paging
```text
Divide memory in small equal size chunks ( frames)
(pages)
Divide process into
Page table for each process
frame location
memory address = page numb, offset within page
logical
address
Main mem
offset
Physical Mem
Page 0
0 a
1: b
0001
frame 0
2: c
0000
P
10 k
3: d
0011
Page 1
4: e
0101
0100
5: f
2
3
Page 2
2
4
3
Page 3
12 m
15: p
15
Page 2
eg, CPU wants to execute 8: i => logical address = 1000
now
refer to page table for Page 2 => Frame = 3.
offset
so
01100
frame offset
so
physical
address
memory
P
d
CPU
page table
```

## Page 61
### Page Table
#### Typical Page Table Entry
```text
address
Number of entries in Page table = Number pages logical space
Page Table
L Kept in main mem and Page Table base register (PTBR) points
to Pagetable
Page Table maintains 4 bit per Page table entry
- Use bit
- modified Bit
- valid bit
- Read only
Adv
No external Fragmentation
Internal Frag
Simple algo
Page table may consume more memory
Multilevel Paging = leads to memory reference overhead.
Swapping easy
Typical Page Table entry protection
Page frame number
caching
modified
Absent
referenced
Present/valid : indicates if value valid otherwise page fault
Protection : defines which accesses are permitted
reference : references to frame
caching : needed if value read from I/O device
modified: Need if page frame reclaimed
- Dirty: Needs to be written on disk first
```

## Page 62
### Address Translation
```text
Address Translation
L logical address generated by CPU is divided in 2 parts
Page No (p) : used as index in page table which
contains base address of each page in physical mem
Page offset (d) - combined with base address to define
physical memory address, it is sent to memory unit
page no
page offset
p
d
m-n
n
bits
bits
size of logical space = 2^m = # of pages (2^(m-n)) x page size (2^n)
example = 16 x 4096
2^m = 2^4 x 2^12
2^m = 2^16
m = 16 bits
so m=16, n=12
Page no = m-n = Leftmost 4 bits
Page offset = n = 12 bits Rightmost
```

## Page 63
#### Address Translation Example
```text
example => incoming virtual address = 8196
m = 16 so total bits in logical address = 16
16 bits
00 1 000000000100
0010
4 bits for page no
page no = 2
12 bits for offset
4 bits = 2^4 = 16 total no of pages
Page
table
000000000100
110
001
110
010
combine
offset bits
frame
no
outgoing physical
address
PTBR - (Page Table base register)
PTLR - (
length register)
TLB not included
```

## Page 64
### Two Level Page Table
```text
Q1)
32 bit = logical AS
4kb = Frame size
find, How many entries in page table
4kb = 4000 bytes so log2(4000) = 12 so 2^12 for 4kb data
so 2^20 = Total no of pages
32-12 = 20 so
20 12
pages no offset
so
=> 1 million
in single level page logical address =
4 bits
pageno
offset
4 bits point to 16 total pages
for a two level p.. this Logical address will be
01 10
tells outer page number
2bit 2bit 4 bit offset
inner
innerpages
outer page
inner page
of 4
each outer page has 4 inner pages
```

## Page 65
### Inverted Page Table
### Virtual Memory
```text
Inverted Page table
L convert Physical address to Logical
page frame
information of process that owns that page
decreases memory need for each page table
but increases time to search the table
L use hash table to limit search to one
Virtual address
page #
offset
Page# Process ID
chain
hash function
Frame # offset
Virtual Mem
L illusion that ability to execute program larger than main memory
size
page replacement
swap in, out
M-M
swap in only pages required
valid bit = 1, indicates
page in main mem,
e.g page 5 required,
page table searches for page 5
valid bit = 0, i.e not already
LAS
swap pages from LAS to MM
Page Fault
```

## Page 66
### Page Fault
### Page Replacement Algorithms
#### FIFO
```text
if valid bit
How to resolve
page fault causes control shift from user to OS (kernel mode)
default control handle & fill required page and
Find free frame
Swap in required page from harddisk
Reset valid bit
Restart function
Goal: algorithm : min no of Page faults
Modified page first saved
L unmodified overwritten (dirty bit)
Fifo
Q1) 1,2,3,4,1,2,5,1,2,3,4,5 Reference string
3 frames
swapped out bit was first in
Hit Hit
page
9 Page faults
fault
```

## Page 67
#### Belady's Anomaly
#### Optimal Page Replacement
```text
1 2 3 4 1 2 5 1 2 3 4 5
4 frames
10 PF
Belady's Anomaly = increasing frames increased Page faults
Optimal Page Replacement (Future)
in future
replace the page with least future demand
7 0 1 2 0 3 0 4 2 3 0 3 2 1 2 0 1 7 0 1
reference string
fault
called
last demand
so replace 7
```

## Page 68
#### Least Recently Used
#### Clock / Second Chance
```text
Least Recently Used
L replace the least recently used in Past
oldest
which of these had the oldest
demand
7 has the oldest demand
Redone
Clock/Second Chance, LRU approximation
Uses reference bit (use) initially 0, if page referenced = 1
To replace page
L First frame with use bit 0 replaced
L Purely search all from it (use bit==1) use bit=0;
if all use bit set = FIFO
```

## Page 69
```text
Clock
Pages in circular list
use bit
0
made 0, hand advanced
page replaced,
new page is inserted
into the clock
and hand advances
one position
0 4 1 4 2 4 3 4 2 4 0 4 1 4 2 4 3 4
if hit
use bit = 1
as FIFO
as FIFO
I would be
replaced 0
replace
and make 4 in use
4 into 4
Clock
LRU
Page
Faults
OPT
No of Frame
```

## Page 70
```text
P.P, Q1, reference string 1 2 3 4 5 3 4 1 6 7 8 7 8 9 7 8 9 5 4 5 4 2
FIFO
OPTIMAL
1 2 3 4 5 3 4 1 6 7 8 7 8 9 7 8 9 5 4 5 4 2
check for optimal from frame-1
LRU
1 2 3 4 5 3 4 1 6 7 8 7 8 9 7 8 9 5 4 5 4 2
```

## Page 71
```text
Q1)
32 bit LAS
Page size = 8 K bits
physical mem size = 1 Gb
a) How many bits for page number = log2(8000) = 13 bits
32-13
32 bits
Rightmost = 13 = offset, 19 = Page no
b) 2^19 = 524288 = Total Pages
c) How many Total Frames created
1Gb = log2(1,000,000,000) = 30 bit
30-13 = 17
2^17 = 131072 Frames
1Gb / 8Kb = 125000
1Gb size
8 Kb
Valid bit, no. bits = 13 => 14 X
d) Size of each table
one entry size = 1 + 13 + 1
frame
valid
bit
```

## Page 72
```text
4x5=20
528
```

## Page 73
### Memory Allocation: Next Fit, Best Fit, Worst Fit
```text
Processes
212K, 417K
112K, 426K
First fit swapped with 212K
500K
426K
Next Fit
212K, 417K, 112K, 426K
100K
500K
200K
300K
600K
Best Fit
Worst Fit
```

## Page 74
### Probability and Stats
```text
Probability and Stats
Mam K.
```
