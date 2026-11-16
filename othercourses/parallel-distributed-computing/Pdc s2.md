# Parallel & Distributed Computing Notes (transcription)

Auto-transcribed from `Pdc s2.pdf` (OCR + AI correction). Diagrams/tables are approximate.

## Page 1
### OpenCL
#### Architecture
#### Framework layer
#### Platform Model
```text
PDC
Sess II,
for
works on
diff processor
+ cross platform
* Architecture
L application runs on host (CPU) that offloads tasks to
one or more devices (GPU)
Kernel = function/task
*
Framework layer:
OpenCL API :
Interface b/w app and openCL
OpenCL Runtime : manages device
Device Drivers : communicate with hardware.
Application -> OpenCL API -> OpenCL Kernels -> Runtime -> Device hardware
* Platform Model
L how openCL organizes hardware
Host : CPU running Application
Devices : one or more GPU/CPU
Compute Units (CUs) - subdivision of device
Processing Elements (PE) : smallest exec
memory divided into
units in CU.
device memory
host memory
```

## Page 2
#### Work Group
#### Memory Model
```text
Work Group -> Work items (single instance of kernel execution)
NDRange : Total work items in a space
Global : total items in all groups
Local : items per group
Thread mapping :
work items identified by -> Global id -> get_global_id(0)
synchronization within groups using barrier or memory fences
Memory Model
Private Memory :
per work item, fast but small
e.g temp variable in kernel
Local memory :
shared within a group, faster than global
Global memory
accessible by all groups
Constant mem
Read only
Host memory -> on CPU, must be transferred to device
Data movement:
Host -> Global -> local -> Private
```

## Page 3
#### OpenCL program
```text
OpenCL program
Host Prog
Kernel program
L implement C = A*B matrix
A = N x P
B = P x M
__kernel ( __global float *A, __global float *B, ... C, const int N ){
C = N x M
replace i,j except sequential code
int i = get_global_id(0) // Row index
2D.
int j = get_global_id(1) // column index
for (int k=0 ; k < N ; k++){
sum += A[i*N+k] * B[
skipped
```

## Page 4
### MPI advanced
#### Broadcast
```text
MPI advanced
collective communications
involve all process
block (all process wait till operation complete)
Broadcast
root -> All
int MPI_Bcast( void * Buf, int count, MPI_datatype dtype, int root, MPI_comm comm)
intracomm   rank of root
all process must call Bcast with matching count, dtype
e.g
int main ( ) {
char msg [20];
int rank;
P1 P2 P3
MPI_Comm_rank( MPI_COMM_WORLD, &rank);
if (rank==0){
strcpy( msg, "Hello world")
MPI_Bcast( msg, 13, MPI_CHAR, 0, MPI_COMM_WORLD);
print ("Process ... ,"
MPI_Finalize();
for 4 process
Output:
Process 0 : Hello world
P '' 1 : Hello world
P '' 2 : Hello world
P '' 3 : Hello
```

## Page 5
#### MPI scatter
#### MPI gather
#### MPI scatterv
```text
* MPI scatter
L root divides arr to chunks - send chunk to all (including
self)
int MPI_Scatter( *sendbuff, int size, datatype, *recievebuff, recievesize, type, int root, comm)
* MPI_gather
L inverse of scatter
e.g
P0
P1
P3
gather
abc
int MPI_Gather( same as scatter)
root recieves all data
* MPI scatterv - variable chunk size
disp = (0,5,9)
L> P0
0
scatter
9
uses
displs array
P0
L each index tell
P1
where to start from
P2
MPI_Scatterv(
sendbuff, sendsize, * displs, type ....
...)
same
for
MPI_Gatherv
```

## Page 6
#### All-to-All
#### All-gather
#### Synchronization
#### Reduce
```text
All-All
unique
L every process sends data to every other process
L used in matrix decomposition
=> MPI_Alltoall( sbuf, size, type, rbuf, size, type, comm)
All-gather
L after gathering by root, data sent to all process
Synchronization
L> int MPI_Barrier ( MPI_comm comm)
each
process wait until all have reached
Reduce
L combine data from all process using operation (sum, max e.g) and provide
result to
MPI_Reduce ( * input data, * result, int count, MPI_type,
MPI_op op, int rank, comm)
e.g
int main ( ){
SUM MAX MIN PROD
...
isend = rank+1
comm
MPI_Reduce (isend, &irecv, 1, MPI_INT, MPI_SUM, 0, comm)
if (rank==0) print(irecv)
Output: 4 process =>
P0 : irecv = 10 (1+2+3+4)
All reduce = reduction + broadcast
L result given to all process
```

## Page 7
#### Exam tips
### OpenMP
#### Core concepts
```text
exam tips
- broadcast = root to all
- MPI_status ignore
- MPI_AlltoAll
= fixed length
- MPI_scatterv , displ + sendcount array
starting index
elements to send
L api for shared memory parallel programming
not distributed mem
L private mem for each process
Runtime Routine : Functions e.g getthreadID, setnumofthreads
Environment variables
L set behavior outside code (e.g default num of
Threads)
Goal
L standardization, threading, multi OS supp
OpenMPI
OpenMP
L distributed sys
shared mem systems
L message passing
parallelization
normally it is MIMD e.g (# pragma for) but # pragma omp simd for
for vectorisation
Core concepts
L Fork / Join model
L master thread forks team of threads
(0)
join at end.
# pragma omp <directive> [ clause(s)]
e.g parallel, for, critical
modifier e.g
private(var),
num_thread(4)
reduction
}
```

## Page 8
#### Directives
```text
compiler ignore # pragma if not supported so runs either way
To compile
g++
#include <omp.h>
int main (){
# pragma omp parallel
int thread_id = omp_get_thread_num();
printf ("Hello world from thread = %d\n", threadid)
}//implicit barrier wait here until all arrive
}
Directives
L spawn parallel reg
L Divide block of code among thread
L Distribute loop iteration
1- parallel
L create team of thread
L code inside run by all threads
L implicit barrier at end
e.g
# pragma omp parallel
{ 'Hello world', Thread id
}
# pragma omp parallel if (exp)
clause
L if false only master
thread, if true then
spawn team
* num_threads(8)
L>
# pragma omp num_threads(8)
or
omp_set_num_threads (4); default
# pragma omp parallel {
}
```

## Page 9
#### Data environment
```text
here
put all these
# pragma omp
2- for/do - distributes loop team
3- single
4- master
5- critical [name] = mutex lock
6-
atomic
=
single operation lock
7-
barrier
=
all wait
8-
=
ordered loop exec
# pragma omp parallel for reduction (+: total_sum)
9- Reduction
Data environment
L how variable declared outside parallel region behave
inside it.
1. shared( variable name)
L default, accessible to all
2. private(
L each thread = own local uninitialized copy
so changes are local, don't effect
int variable = 10
# pragma omp parallel private (variable){
{
variable = variable +1
inside v = 1
uninitialized
}
0+1 = 1
value outside remains 10
}
3. first private
parallel
L all local but initialized with value before region
4. Last Private - every thread get uninitialized
and after loop has value of last thread.
11 if first private
used
L variable out will have value from last thread executing (last iteration)
# pragma omp for
for (int i=0; i<10; i++)  * total 4p
e.g
N = 5, loop 0...4, last i=4 so b = 50+4 = 54
```

## Page 10
#### For clauses (schedule)
```text
recommend for debugging
if not specified assume share
Default (none) or default (shared)
L if used then will have to specify data environment for all variable in parallel reg
# pragma omp parallel for default (none) private(i) firstprivate(a)
for (i=0, i<5, i++){
a++
}
For Clauses
L schedule how iteration divided and assigned
to threads
1. static
L iteration divided to chunks, default size = Loop count
by round robin
/ Num threads
Pros: low overhead
con = bad Load imbalance
e.g
shedule(static) or shedule (static, 1)
chunk size of
1 assigned via
so 25 per thread
e.g 10/3 threads
# pragma omp parallel for shedule ( static,10)
for...
thread 1 : 1 4 7 10
so
thread 2 = 2 5 8
thread 3 = 3 6 9
if chunk shedule (static,2)
thread 1 = 1,2, 7,8
9,10
2- Dynamic
L chunks assigned to available thread as
they finish previous chunk
shedule(dynamic, 10)
pros better
L overhead more
con
- load balance
e.g 100 iteration, 4 thread
t0 : 0-9
t1 : 10-19
-> finishes first get 40-49 .....
t2 : 20-29
t3 : 30-39
```

## Page 11
#### Reduction clause
```text
* Reduction clause
L private copy made for each variable and initialized
at end all private copies examined and shared variable result
written
e.g
int winner
# pragma omp parallel reduction( max: winner) num_thread(10)
{
winner = (random) + 10
}
output -> winner outside will be the max local value of all thread.
```

## Page 12
### Dependency
#### Data Dependency
```text
Finals
their execution
order
Data Dependency
control dependency
Two statements
It occurs when 1 statements
have this if one
statement depends on
determines if other statement
result of previous
will occur or not.
e.g
e.g
S1
if (T is not 0)
S1
Pi = 3.142
S2
S2
A = A/T
S3
Area = Pi x R**2
. exec S2 before S1 can cause divide
. S3 can't be exec befor S1 or S2
by zero
* ensure
1. both statement
access same memory
location and atleast one stores on it
2. There is feasible
execution path
read write
flow RAW
* True Dependence (R after W)
x = 5 // write
y = x // read
WAR
* Anti Dependence (W after R)
y = x
x = 10
* output Dependence (W after W)
x = 5
x = 10
* input (R after R)
```

## Page 13
### Dependence in loop
```text
Data Dependency
- only flow dependences are true dependence
- Anti and output can be removed by renaming
Dependence in loop
*
Do-All loops
* if dependence
crosses iteration boundary
L No dependencies fully parallelize
than it is loop carried
DO I=2,N
and loop can't be parallelized
A(I) = A(I)+1
Iterations independent
*
loop carried Dependence
L when dependence crosses iteration boundary, Does prevent parall
DO I=1,N
A(I+1) = A(I)+B(I)
*
loop-independent Dep
L occurs with same iteration, doesn't prevent parall
DO I=1,N
S1
A(I) = ...
// write
// read
S2
= A(I)
S2 depends on S1 with same iteration
```

## Page 14
### Formalizing Dependences
#### Iteration space and vector
#### Distance vector & Direction vector
```text
Formalizing Dependences
L we use mathematical constructs like vectors, to analyze dependences
Iteration space and vector
It space: set of all possible combination of loop index values or
all possible iteration values.
It vector: single entity in iteration space
Do i= 1,2
Do j= 1,2:
S1 : A[i] = A[i-1]
It space = i=1 j=1 (1,1)
so Iteration space = { (1,1) (1,2) (2,1) (2,2) }
i=1 j=2 (1,2)
iteration vectors
(2,1)
i=2 j=1
3rd iteration
i=2 j=2
(2,2)
vector
Distance vector & Direction vector
L describes dependences among iteration
defines direction of code / loop
2 thing used
source = (earlier statement of dependency)
sink = latest statement)
Distance = sink - source
write
A[1] = A[0]   source=0
e.g
A[2] = A[1]  read  so -> Antidependence
loop carried
sink=2
```

## Page 15
```text
Direction vector ( step size = 1 for distance vec)
L will be
'<' if distance vector > 0
= 0
''
'='
''
''
< 0
if direct vector
(<)
then
loop carried
=
then
loop independent
example:
Do I = 1,6
A[2*I] = B[I]+1  S1
C [I]
= A[I]  S2
Iter=1
A[2] = B(1)+1  S1[1]
Iteration
I
S1
S2
C(1) = A(1)   assigning two different A index
1.
A[2]
1
A[1]
2=
A[4] = B(2)+1
2
2
A[4]
vector
A[2]
C(2) = A(2)
write and then
read
3
3
A[6]
=3
A[6] = B[3]+1
C(3) = A[3]
Dependency
Array elements
=4
A[8]
S1[1] S2[2]
A[2]
A[4]
S1[2]
S2[3]
A[4]
Direction
Sink=2 Source=1
2-1=1
<
sink=4 source=2 4-2=2
<
so loop
Direction
loop carried
Distance vector varying = *
= <
```

## Page 16
#### Eliminating Dep
```text
a[2] = b[2]+c[2]
so
d[2] = a[3]
a[i] = b[i]+c[i]
source
d[i] = a[i+1]
a[3] =
= a[4]
a[4] =
I
S1
S2
= a[5]
2
2
a[2]
a[3]
a[3]
a[4]
3
3
4
a[4]
a[5]
4
S2[1]
S1[2]
8
S1 at iteration 2
S2 at iteration 1
2
-1
S1[3]
&
S2[2]
Distance vector
L
3-2 = 1
iteration vectors
so Dist v = 1 and Direction '<'
4-3 = 1
so loop carried
Eliminating Dep
1. Anti
Do I=1,N
A (I) = A(I+1)
read before write
so transformation
safe transformation = same meaning
as original
DO I=1,N
program
A2[I] = A[I]
DO I=1,N
A[I] = A2[I+1]
```

## Page 17
### Program Transformation
#### Loop interchange
#### Loop Distribution
#### Loop Normalization
```text
Distance = sink - source
Direction = (<, =, >) if Dist = (2,0,-2)
Program Transformation
L reorder code to improve performance while preserving dependences
* Loop interchange - safe if no loop dependence   Dont add /remove statement
carried
e.g DO J=1,N
as
or same direction for all
DO I=1,N
->
B(I,J)=5
transformed to
Do I=1,N
DO J=1,N
improves data locality if B stored row major
B(I,J)=5
column major = B[i,j), B(i+1,j)...
target
* Loop Distribution : Split into multiple loops
dependencies dont exist
if cyclic
S1 : A[I+1] = B(I) + C
S2 : D(I) = A(I)+E
DO I=1,N
DO I=1,N
* Loop fusion
Loop Normalization
L transforms loop with arbitrary bounds, stepsize to standard
- loop start at index 1
- loop has stepsize 1
- original loop index expressed as function of normalized index
Benefits
Simplify Analysis
Enable transformation
Improve Code Generation :
```

## Page 18
#### Algorithm to Normalize
```text
DO I = L,U,S   stepsize (S)
Lower
Upper
bound
(L)
Algorithm to Normalize
Step1 : Replace loop header with adjusted header
Do i=1 , (U-L+S)/S
Step2 : Replace each reference to I with the loop by
i*S - S + L
Step3 : insert finalization Assignment after loop
I = i*S - S + L
Q1, DO I = 0,10,2
i*2
A[I] = A[I+1]
(i*S-S+L)+2 = (i*1+101)*2
L=0, U=10, S=2
202 - 2i
Step1 : Do: i=1, (10-0+2)/2 => i=1,6
step2 : A(i*2 - 2+0) = A(i*2 - 2+1)
Step3 :
Do i=1,6
A(i*2 -2) = A(i*2 -1)
enddo
I = i*2 - 2 + 0
not 2
Q2,
for( int i=100 ; i>2 ; i--)  S=-1
A[i*2] = A[i-2+10] + A[P-2];
for( int i = 1 , (3-100-1)/-1 = 98 , i++)
equal to or less than
so i<=98
x2
A[(i*(-1)-(-1)+100)*2] = A[((i*-1+1+100)-2)+10] + A[P-2]
so A[ 201-2i ] = A[i-
```

## Page 19
#### Loop Distribution (splitting)
```text
Loop Distribution splitting
DO I=1,N
DO I=1,N
A(I+1) = B(I)
A(I+1) = B(I)
->
D(I) = A(I)+E
DO I=1,N
D(I) = A(I)+E
S1 d S2
S2 d S1
e.g
DO I=1,N
* Fails if cyclic dependence  L if mutual dependency b/w statements S2 depends S1, S1 depends S2
S1 : A(I+1) = B(I)+C
S2 : B(I+1) = A(I)+E
S1 to S2:
S1 write A(I+1)
S2 reads A(I+1) to compute B(I+2)
True Dependence
Direction vector < loop carried
S2 to S1
S2 writes B(I+1)
S1 reads B(I+1) to compute A(I+2)
next iteration
True Dependence : S2 d S1
Direction < loop carried
2) Do I=1,N
S1 : B(I) = A(I)+E
S1 to S2 : write B(I)
S2 : A(I+1) = B(I)+C
read B(I) same
True
Direction vector '=' loop-independent dependence
S2 to S1:
S2 writes A(I+1)
True Dependence
Direction <
S1(I) -> S2(I) -> S1(I+1) acyclic so split loop
```

## Page 20
### Polyhedral Model
```text
Polyhedral Model
L map each statement of loop and its relationship, Done by computer, then transform
loop based on it , dependency test : several maths method validate the transformation
and then code generation
Dependency Graph L each node = 1 statement
Polyhedral model
L each point
Do i=1,5
e.g
j= 1, 10
50
TODO -> understand this below, do loop fusion.
e.g
for ( i=1 ; i<n ; i++)
S1 : a[i+1] = b[i-1] + c[i]
(S1)
S2 : b[i] = a[i] * K
S1 to S2:
S3 : c[i] = b[i] - 1;
S2 reads
True Depen
Direction <
(S2)
S2 to S1:
S2 writes b[i]
(S3)
```

## Page 21
### Dependence Analysis (Distance and Direction Vectors)
```text
check for location which are written at.
Q1)
for(i=0;i<N;i++)
for(j=0;j<N;j++)
a[i+1][j-2] = a[i][j] + a[i-1][j-2]
we need to find Dependance
means one iteration needs to wait for another because they
use same memory location
so find → which loop depends
Memory Access Pattern
→ How far apart they are (distance vector)
i=0 a[1][-2] = a[0][0] + a[-1][j-2]
→ Whether they go forward or back (direction v)
a[1][-1] =
j=1
a[1][0]
a[1][0] written then read = True dep
check for written variable as 'w' is must for any dependency
i=1
a[2][-2] = a[1][0] + a[0][-2]
read at a(i+1,j)
a[2][-1] = [1] 1   0 -1
written at a(i-1,j+2)
a[2][0]
Dist = (1,-2)
Direction = (<,>)
current read a[i-1][j-2] at (i,j)
i=2
a[3][-2] = a[2][0] + a[1][-2]
previous write at a[i-1][j-2] at (i=2, j)
a[1][-1]
so
source-sink
Direction
Q1
Distance vector = (+2,0)
Direction = (<,=)
```

## Page 22
### Loop Distribution and SCC
```text
Q) for( i=1, i<3
for(j
x[i,4*j-2] = x[i,4*j+1] + y(i,j)
Y[i+1,j-3] = X[i,2*j] + y(i,j)
x[1,13]
x[1,10]
= y(1,8)
y(1,6)
y[2+4,3]
+ y(1,6)
= x[1,6]
y(1,3)
j=7
j=8
j=9
x(1,10]
j=10
dependence
for i=1, j=9
RAW
i=1
for i=2, j=
x[1,10] = x[1,13]
j=3
y(1,3)
Y[2,0] = x[1,6] + y(1,3)
for j=5 x[1,10] so RAW
i=2
i=2
y[2,5]
j=5
Q) Apply loop distribution/fusion after computing SCC
y[2,5]
anti A(i)
RAW
i=1 to N)
A[i] = A[i] + B[i-1]
Anti B[i]
B[i]
for
A(i)
B[i] = C[i-1] * x*y
B[i] true
write circular
1/B[i]
Anti C[i]
S3
C(i)
D[i] = sqrt(C[i])
C[i] True
for
D[i]
```

## Page 23
### AVX / Intrinsics
#### SSE, AVX2, AVX 3.2
```text
#include <xmmintrin.h>
__m128 Avec = _mm_load_ps(&A[i]);
Q
AVX/Intrinsics
__m128 result = _mm_add_ps(A[i], b[i]);
Q1
_mm_store_ps(&B[i], result);
SSE: 128,4
A[S] -> Rand.....
AVX: 256,8
B[S] -> Rand.....
for int i=0 to n
B[i] = (A[i]+b[i]) / A[i]
Convert code to i) SSE ii) AVX2 iii) AVX 3.2
128 bits = 4 floats
256 = 8 floats
512 = 16 floats
Approach
→ Initialize Array
→ Vector loop: Process 'n' elements in (4,8,16) steps using floats
→ Intrinsics: Use Load, add, divide, and store
so
S = rand() % 100
for(int i=0; i<S; i++){ A[i] = rand()%100; B[i] = rand()%100; } //initialize
random
SSE so i+4
__m128 Avec = _mm_load_ps(&A[i]); //load into vector
__m128 B_vec = _mm_load_ps(&B[i]);
operation
__m128 sum = _mm_add_ps(A_vec, B_vec);
__m128 result
= _mm_div_ps(
}
_mm_store_ps(&B[i], result);
// store result
AVX2
→ for(int i ... ; i+=8)
__m256 Avec
// rest is same
AVX 3.2
for(int i ... ; i+=16)
__m512
```

## Page 24
### OpenMP
#### Reduction
#### Atomic Example
```text
OpenMP
int n=10, t=0;
omp_set_num_threads(2); must set no. of threads
#pragma omp parallel private(j) firstprivate(t){
static =
5 6 7 8
for (i...){ }
9 10 11 12
//pragma omp master{
for m += s_data+i
(static,1) =
2 5 8 11
}
#pragma omp for schedule(dynamic)
3 3
#pragma omp parallel if(thread_id != 0)
cheatsheet:
#pragma omp for ... private(j) : '0' uninitialized
chunks of 3 divided, assigned
single
firstprivate, lastprivate (initialized)
master
lastprivate
to free thread
schedule(static,3)
critical[name]
round robin
atomic: single operation
it used where to specify data type of every
barrier : all wait
ordered : operation
reduction(+: total_sum)
variable
Reduction : combines result  #pragma omp parallel reduction(*: product) num_threads(10) {
int local_value = rand() % 5
*
product = local_value
max
} //each thread gets a random value 1-5, product contains total 10 pt
min
Atomic example
#pragma omp parallel {
int i = 2
#pragma atomic
sum += local
```

## Page 25
### MPI
#### Advanced MPI Collectives
```text
MPI_Send() - can be ...
MPI_Isend()
not blocked
MPI_Wait()
#include <mpi.h>
MPI MPI
MPI_Recv
MPI_Irecv()
int main(){
MPI_Init(NULL,NULL)
int rank, size;
MPI_Comm_rank(MPI_COMM_WORLD, &rank)
" " _size( " " &size)
float *num_array;
if (rank == 0) { //send
MPI_Send(*msg, count, MPI_Char, dstrank, message tag, MPI_COMM_WORLD)
send buff
}
else { MPI_Char buffer
MPI_Recv( . . .
same
MPI_Status_ignore
}
MPI_Finalize();
}
Advanced
int MPI_Bcast(buff, count, MPI_Datatype, int sendrank, MPI_comm world
0
root to all (all data of root to all)
int MPI_Scatter( . . . datatype, *recv buffer, recv count, recv Datatype, int root, ..)
sends part of send buffer to each process
MPI_Gather( same as scatter )
starting position
root receives data from all
(0,5,9,12)
send count
MPI_Scatterv( sendbuff, count, int displs[]
variable sized scattering
MPI_Gatherv
MPI_Allgather( ) - same as gather but result available to All procs
MPI_Alltoall( ) - each process knows buffer of all other
```

## Page 26
#### MPI_Barrier and MPI_Reduce
```text
int MPI_Barrier(MPI_Comm comm) : All processes reach barrier till then wait
no count
int MPI_Reduce( sendbuf, recvbuf, count, type, MPI_Op op, int root, comm)
MPI_SUM, PROD, MIN, MAX
LAND, BAND, XOR, ...
Allreduce( . . )
result available to all.
```

## Page 27
### OpenCL
```text
OpenCL
app.c
device-code.cl
Host = setup environment + manage kernels
clEnqueueNDRangeKernel();
5 step
convert context (CL_Device_Type)
cl::Command Queue queue context
create, build program
setup memory
Program program(context, kernelsource, me);
Define kernel
cl::Buffer d_a(context, h_a.begin, end, true)
string
submit run
buffer
d_b
for
d_c
exchange
read only
cl::make_kernel< buff . >
size_t globalsize
localsize
globalsize
clEnqueueNDRange(queue, kernel, 2, Null, ...)
local size
Null
cl::enqueueReadBuffer(
```
