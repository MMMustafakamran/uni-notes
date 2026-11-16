# Numerical Computing - Handwritten Notes (transcription)

Auto-transcribed from `numerical_HandwrittenNotes.pdf` (OCR + AI correction). Matrices/diagrams are approximate.

## Page 1
### CH#05
#### Bisection Method
#### Convergence rate
#### Fixed point
```text
CH#05
Bisection Method.
If sign changes in interval
f(a),f(b) then Keep halving
if both
f(a) * f(b) = positive
then a = x
so def bisection (f, a, b, tol, err)
if( f(a) * f(b) < 0.0)
while ( (b-a)>tol):
x = a+b/2
if( f(a) * f(x) < 0)
b = x
< 0.0):
elseif
(f(x) * f(b)
a = x
else break
return x
error
Convergence rate
log
r =
e1
log
e2
Fixed point
e.g
x^2 - x - 1 = 0
write eq in terms of x
x = 1 + 1/x
put x_{n+1} in subject
x_{n+1} = 1 + 1/x_n
pick a value, plug in, keep plugging
plug x = 2
x_1 = 1 + 1/2
= 1.5
x_2 = 1 + 1/1.5
= 1.66
x_3
= 1.62
Rule of conv: if g'(root)<1 it conv
def fixedpoint(g, x0, tol, maxit)
g(x) = 1 + 1/x
error = 1
e.g
g'(x) = - 1/x^2
x_k = x0
g'(-0.3819) < 1 - so converges
while(error>tol)
error = x_k
f is original
x_k = g(x_k)
func, g is the
error = np.abs(error - x_k)
func where x is subject
return
def f(x):
y = x**2 - x - 1
def g(x):
return y
y = np.sqrt(x+1)
x subject
return y
```

## Page 2
#### Newton Raphson
#### Secant method
#### Scipy
### CH#06 - Interpolation
#### Lagrange
```text
Newton Raphson
repeat plugging
Pick x, find f'(x), plug into
x_{n+1} = x_n - f(x)/f'(x)
order of conv = 2.
Code.
: def Newton( f, df, x0, tol):
same as fixed just
x_k = x_k - f(x_k)/df(x_k)
return
def f(x):
def df(x):
same as Newton, substitute slope formula in f'(x) so x_{n+1} = x_n - f(x) / ((f(x_n) - f(x_{n-1}))/(x_n - x_{n-1}))
Secant method
slope
formula
Scipy
import scipy.optimize as spo
x = spo.bisect( f, a, b, (), tol)
x = spo.fixed_point( g, x0, (), tol, maxit)
x = spo.Newton ( same as fixed
)
x = spo.fsolve
CH#06 - Interpolation: find unknown values within set of known data points
doesn't contain x0
Lagrange
(x-x1)(x-x2) ... (x-xn)
(x-x0)(x-x2)(...
+
y_0
y =
(x0-x1)(x0-x2) ... (x0-xn)
(x1-x0)(x1-x2)
Q1
find f(4)
x
0
5
y
for x=4  y=?
(4-2)( 4-3)....(4-6) * 5 + (4-0)....
2
3
5 6
10
(0-2)(0-3)......
12
Newton Method
7
```

## Page 3
#### Newton Method
#### Linear spline
#### Least square approx
#### Hermite
```text
Newton Method
(x0,y0)=(1,2) , (x1,y1)=(7,10) , (x2,y2)=(8,12)
Δy
x
P(x) = a0 + a1(x-x0) + a2(x-x0)(x-x1) ...
2
4/3
7
10
2
2/21
P(x) = 2 + 4/3 (x-1) - 2/21 (x-1)(x-7)
8
10
Linear spline
f(x) =
y0 +
y1 - y0
(x-x0)
61
x1 - x0
Q, find f(61)
x 22 | 52 | 82 | 100
y 4187 | 4186 | 4199 | 4217
61 b/w 52, 82 so
x0  x1
4199-4186
(x-82)
61
52
f(x) = 52
+
gradient at first
82-52
x0
first point
input
second point
Least square approx
(2+3+4+5+6)^0
( )'
Σx^0   Σx^1   Σx^2
Ab=c
20
90
y
9
Σx^1   Σx^2   Σx^3
Σx^3
20
90
29
Σx^2
Σx^4
440
62
5
126
A
215
1279
Σx^0 y
2273
Σx^1 y
441
Σx^2 y
50
C
Hermite
Hermite
```

## Page 4
### CH#07 - Integration Approx
#### Midpoint
#### Newton Cotes
#### Trapezoid Rule
```text
CH#07 - Integration Approx
Midpoint
y = x^2
8-0
= 2 | stepsize
Q1
find area of
curve till ∫_0^8 x^2
sum area of rectangle = 2*midpoint + (4-2)*midpoint 2 ...
n=4
for approx
8
2
4
A = stepsize *
Σ f(x_i)
interval
midpoints
i=1
n=4
0 2 4 6 8
use 4 points
Newton cotes
takes area under
each straight
line to approx
b
a
Trapezoid Rule
∫_a^b f(x) = ∫_a^b f1(x) dx
f1(x) = f(x0) +
f(x1)-f(x0)
(x-x0)
x1
organic Q1
T_n = Δx/2 [ f(x0) + 2f(x1) + ... + 2f(n-1) + f(xn) ]
∫_0^10 x^2 = ? where n=5
use 6
pts
Δx = (b-a)/n = (10-0)/5 = 2 so
first and last dont have 2
T_5 = 2/2 [ 0 + 2(4) + 2(16) + 2(36) + 2(64) + 100 ]
T_5 = 340
```

## Page 5
#### Composite Simpson
### CH#02 Banded Matrix
### CH#03
#### Finite Precision
#### Catastrophic cancel
#### Machine epsilon
#### Underflow vs Overflow
```text
Composite Simpson
f(x0) + 4(f(x1)) + 2(f(x2)) + 4(...) + ... + f(xn)
S_n = h/3 [
alternating 4, 2 except for 1st and last
CH# 02 Banded Matrix
convert to banded form
A =
for j in range (n)
m = max(1, j+1-u)
l = 1
u = 2
m = min
upper bandwidth
CH#03
1. Finite Precision
limited memory
so Floating point
1.1+0.1 = 1.2000002
2. catastrophic cancel
'-' of nearly equal numbers
= 0
3. machine epsilon
smallest no when added 1,
result in value drift from 1
x = 1
while (x+1 != 1)
x = x/2
3
eps = 2*x
4. Underflow vs Overflow
Numbers greater than max or less than min = inf, NAN
Numbers
smaller than
'tiny' are zero
```

## Page 6
### Python Syntax
```text
Python Syntax.
write in scientific notation 1.3x10^-2 cm
Python list can have diff data types
e.g
['R', '1', 'Hello']
Tuples are constant list
x = ('R','a','h','a','t')
x = (3,) comma must
print(x[0])
print(x[-1])
// Last index printed.
len(x)
// length of x
Adding to list will append
grades = [9,6,7]
grades = grades + [6.2, 8.2, 5.9]
print(grades)
output => [9,6,7,6.2,8.2,5.9]
':' is slice operator
Python includes 2
grades [2:4]
[i,j) ✓ python
but excludes 4
[i,j] x
output:- 7,6.2
(i,j) x
grades [:4]
output :- 9,6,7,6.2
grades [4:]
:- 8.2,5.9
'=' causes deep copy
// changing grades will change list2
list2 = grades
list2[0]=14
print both :-
14,6,7...
14,6,7...
'[:]' cause shallow copy
list2 = grades[:]
list2[0] = 14
..9,6,7
14,6,7
```

## Page 7
#### Matrices
#### Loops
#### Conditions
```text
Matrices
A = (1 2; 3 4)
A = { [1,2],[3,4] }
Loops
for i in [0, 1, 2]:
i=0
output= hello
hello
i=1
print('Helloworld')
i=2
hello.
for animal in [cat, dog, bird]:
:- cat
dog bird.
print (animal)
Range: is range [ start,stop, step]
for i in range (5):
0,1,2,3,4
for i in range(2,10,3):
2,5,8
Python is case, space sensitive
Conditions
• a = 1<2
true so a=true
• if a != true :
print (Not true)
• x = int (input ('Give me x='))
// cin
type (int(a))
5! factorial
!5 not
```

## Page 8
#### Functions
#### Lambda / alternative Func Definition
#### Recursive Function
```text
Functions
max( )
swap( )
def double(x):
y = 2*x
return y
calling func :- r = double(x) + 1
If, else
if x >= y :
return x
else :
return y
Ternary operator
y=2 if x>3 else y=3
Lamda / alternative Func Definition
f = lambda x: f(x)
e.g
f = lambda x: x+1
print( f(1))
output :- 2
Recursive Function
```

## Page 9
### The Library Numpy
#### Vectors
#### Special matrices
```text
The Library Numpy
import numpy as np
Matrix 3x2
A = np.array([[1,2],[3,4],[5,6]])
// array, only num allowed.
Directly add scalar without loop
slicing
A[:,0]
//extracts the first column.
Mean
Vectors
print
(a.shape)
// prints shape of vector.
a.reshape(1,3)
// reshape 3x2 vectors to 1x3
Special matrices
A = np.zeros(3,4)
// gives 3x4 matrix
A.transpose.
I = np.eye(3)
//
```

## Page 10
#### Triangular matrix
#### Performance
```text
Triangular matrix
1 2 3
4 5 6
7 8 9
upper triangle
L = np.tril(A)
U = np.triu(A)
1 2 3
shallow copy
B = A.copy()
Add matrix, multiply/Divide with scalar.
A = B+C
Performance
import time
A = np.random.rand(100,100)
// random 100x100 matrix generated
B = np.ra...
t0 = time.time()
C = A+B
numpy
lowest time
t1 = time.time()
print('Python', t1-t0, 'Seconds')
time for C = A+B
C = add(A,B)....
time for C = add(A,B)
t1 = time.time()
print( ; t1-t0 )
time for C = addv(A,B)
second
iteration
```

## Page 11
#### Multiplication
#### Extra Functionality
```text
Multiplication
first col x first row
for i=1:n
for j=1:p C(i,j) = A(i,:) . B(:,j)
End for
End for
For Dot product of matrices e.g a.b , Numpy automically transposes
a . b
it so a . b
If A x B
C = A * B // this will cause elements to be multiplied
C = A @ B // matrix multiplication
// Dot product if same dimension
E = np.dot(A,B)
Extra Functionality
import numpy.linalg as npl
A_squared = npl.matrix_power(A,2) // whole matrix power
npl.power(A,2)
// elemental power
npl.det(A)
A A^{-1} = I
A_inverse = npl.inv(A)
```

## Page 12
#### Linear Systems
#### Eigenvalues/Eigenvectors
```text
Linear systems
A =
B =
x1 + x2 + x3 = 1
2x1 + x2 + x3 = 2
so
1x1 + 1x2 + 1x3 = 3
from numpy.linalg import solve
x = solve(A,B)
Eigenvalue/vectors
from numpy.linalg import eig
(w,v) = eig(A)
list of
eigen
eigen vectors
values
from numpy.linalg import eig
print('w='); print(w)   :- [-1, 2]
print('v=')
[[1, 2]
[2, 4]]
```

## Page 13
### CH#5 - Roots of Equations
#### Fixed Point
```text
Numerical Computing,
Roots of eq, find x values for eq f(x)=0:
CH#5
1 o Fixed point
2 o Newton method (Newton Raphson)
3 o secant Method
4 o
scipy.optimize
5 o Application in Astrophysics
Fixed point
5.1
o write eq in terms of x
o put it = x_{n+1}
o Keep plugging value
Q1)
x^2 - x - 1 = 0
x^2 = x + 1
x^2 - x = 1
x = x/x + 1/x
x(x-1) = 1
x =
1/(x-1)
x_{n+1} = 1 + 1/x_n
x_{n+1} = 1/(x_n - 1)
plug x=2 // random value
plug x=1.6
x_2 = 1 + 1/2 = 1.5
x_2 = 1/(1.6-1)
= 1.66
doesn't
= 1.5
x_3 = 1 + 1/1.5 = 1.66
converge
= 2
= 1.6
= 1.625
= 1.6125
converges
```

## Page 14
```text
| g'(root) | < 1
converges if
Rule of convergence =
g(x) = 1 + 1/x
g(x) = 1/(x-1)
-1/(x-1)^2
g'(x) = -1/x^2
g'(x) =
g(root) = |-2.618| > 1
= |-0.3819| < 1
= doesn't
= converges
Code:
def fixedpoint (g, x0, tol=1.e-6, maxit=100):
error = 1
iteration = 0
x_k = x0
while (error > tol and iteration < maxit):
iteration++
x_k = g(x_k)
error = np.abs(error - x_k)
return x_k
def f(x):
y = x**2 - x - 1.0
return y
def g(x):
y = np.sqrt(x+1)
return y
x = fixedpoint (g, x0, tol, maxit)
```

## Page 15
#### Newton Raphson
```text
5.2 Newton Raphson
o Pick x near root
o find f'(x)
x_{n+1} = x_n - f(x)
o plug into
f'(x)
o repeat until converg
f(x) = x^2 - 10
Q1)
f'(x) = 2x
x_{n+1} = x_n -
x_n^2 - 10
2x_n
x0 = 3
3^2 - 10
x1 = 3 -
= 2.767
6
= 2.67
x2 =
Code:
def Newton( f, df, x0, tol, maxit)
error = ''
iteration = ''
x_k = ''
while('' ):
iteration++
err = x_k
x_k = x_k - f(x_k)/df(x_k)
// same
Order of convergence = 2
```

## Page 16
#### Secant Method
```text
Secant Method
5.3
o Same as newton guess no derivative required
f(x_n) - f(x_{n-1})
just
substitute
slope formula
f'(x) =
x_n - x_{n-1}
in f'(x)
slope
x_{k+1} = x_k - f(x_k) . (x_k - x_{k-1})
f(x_k) - f(x_{k-1})
Q) Find root, perform 4 intervals of secant,
x^3 + x^2 - 1
code:
def secant (f, x1, x2, tol, error)
while ( err > tol ... )
x_k1 = x1
x_k = x2
iteration++
err = x_k1
x_k = x_k - ((x_k - x_k1) / f(x_k) - f(x_k1))
error = np.abs(err - x_k1)
x1 = x2
def f(x):
def
```

## Page 17
```text
f(x) = x^2 - 4, actual root = 2
Q,
initial guess x0 = 3
f(x0) = 5
x1 = 2.5
f(x1) = 2.25
secant form
x_n - x_{n-1}
x_{n+1} = x_n - f(x_n)
f(x_n) - f(x_{n-1})
so
x_1 - x_0
x_2 = x_1 - f(x_1) .
f(x_1) - f(x_0)
x_2 = 2.5 - 2.25 (
2.5 - 3
2.25 - 5
= 2.095
x_3 = x_2 - f(x_2) . f(x_2) - f(x_1)
f(x
```

## Page 18
#### Scipy Module
```text
5.4 Scipy Module
-> Bisection code:
import scipy.optimize as spo
def f(x):
''
x = spo.bisect (f, a, b, (), tol)
-> fixedpoint
import scipy.optimize as spo
def f(x)
def g(x)
x0 , tol, maxit
x = spo.fixed_point (g, x0, (), tol, maxit)
-> Newton
import scipy.optimize as spo
def f(x)
def df(x)
x0
x = spo.newton (f, x0, df, tol, maxit)
->
fsolve (Hybrid work on broader spectrum)
import ..
def f(x):
def df(x):
x0
x = spo.fsolve (f, x0, fprime = df, xtol=1.e-4)
```

## Page 19
#### Application
```text
anomaly of planet
5.4
Application
theta = psi + e sin(theta)
eccentric
eccentricity
anomaly
o use fixed point
def g(theta):
e = 1.e^-6
psi = np.pi/6
return = psi + e * np.sin(theta)
f0 = np.pi/6
f1 = spo.fixed_point (g, theta0)
```

## Page 20
### CH#6 - Interpolation
#### Lagrange Polynomial
```text
way to find unknown value within set of know
CH#6
Interpolation
data points
1 - Monomial Basis
2 - Lagrange polynom
3 - Failure of Lagrange
4 - Newton method
5 - Hermite
6 - Spline
7 - Least square
8 - Polynomial fit
9 - Non Poly Fit
10 - Scipy
Lagrange Polynom
2)
Degree of Poly = n-1
No of Data points
x - x_K
y_j
Π
Σ
x_j - x_K
K=1
j=1
K≠j
summation
product
Notation
```

## Page 21
```text
(0,5)
(2,1)
find f(4)
Q
x
y
5
y0
x0
7
2
x1
y1
8
y2
x2
3
5
10 y3
x3
for point 0 => x0,y0
12 y4
x4
6
y = {(x-x1)(x-x2)....(x-xn) . y0
Formula =)
Ax4
{(x0-x1)(x0-x2)(x0-..)...(x0-xn)
x0 - everything
(x-x0)(x-x2)(x-x3)... y1
(x1-x0)(x1-x2)...
so solving for x=4 find y
y = (4-2)(4-3)(4-5)(4-6) . 5
+
(0-2)(0-3)(0-5)(0-6)
(4-0)(4-3)(4-5)(4-6) . 7
(2-0)(2-3)(2-5)(2-6)
y = 8.89
```

## Page 22
```text
Code:
def lagrangeBasis (z,x):
no of nodes  n = len(x)
no of points to calculate
basis = np.ones ((n,m))
for i in range (n) : //iterate node
for j in range (n):
if i != j :
basis[i,:] *= (z - x[j]/x[i] - x[j])
return basis
def lagrange_interpol (z,x,y)
n = len(x)
m = len(y)
P = np.zeros(m)
basis = lagrange_basis(z,x)
for i in range(m):
P += basis[i,:] * y[i]
return P
def f(x):
z = np.linspace (1,4,100)
x = np.array ([1, 1.5, 4])
y = f(x)
yz = lagrange_interpolant (z,x,y)
plt.plot (z, yz, 'z-')
plt.plot (x,y,'o')
plt.plot (z,f(z), '-')
plt.legend
plt.xlabel, ylabel
plt.show()
```

## Page 23
#### Lagrange Failure
#### Newton Method
#### Divided Diff
```text
Lagrange Failure
known
for too many points
Lagrange
Actual
Newton Method
Q1
24
28
32
36
40
find
f(33)
y
28.06
30.19
32.75
34.94
40
y = y_n
y_{n-1}
v(v+1).1
+
+
y_{n-2}
y_{n-n}
1!
2!
gradient
x - xn
v =
h
v = (33-40)/4 = -7/4
v =
n=4
so
x=33
xn = 40  so
Divided Diff
x
Δ²y
Δy³
y
Δy a1
Δ²y a2
x
a0
a2
30.19-28.06
"
24
28.06
"
28-24
28
30.19
"
"
32
32.75
"
36
34.94
"
40
40
R
P_n(x) = a0 + a1(x-x0) + a2(x-x0)(x-x1)
```

## Page 24
#### Newton's Forward Form
```text
150-100
5-3=h
-30
find f(4)
3
5
Q1)
7
9
o x point must be equispaced
y
180
150
120
90
o Newton forward - if 4 in beginning
of data point
Δy
Δ²y
Δ³y
in this
x
y
a1
case
backward-
-end
a2
a3
for forward
3
180
-30
0
0
-30
5
150
x1
for backward
7
120
-30
x2
90
x3
9
1/2 = 0.5 = V
4-3
V = x - x0
=
2
h
diff in x values
+1 for backward
Newton's forward form
Δy0 +
v(v-1)
....
v
1!
2!
y = 180 + 0.5/1 (-30) + 0.5.(-0.5)/2! .(0) +
0.5(-0.5)(-1.5)/3! .(0)
3!
y = 180 - 15 = 165
P(x) = 180 + (-30)(x-3)
+ 0(x-x0)(x-x1)
P(x) = y0 + Δy0 (x-x0)
Δ²y0 (x-x0)(x-x1) +
P(x) = y0 + Δy0 . (x-x0) +
y0
code to interpolate at np.linspace (ex 3,9,20).
z = np.linspace(3,9,20)
x = [3,5,7,9]
a = [180,-30,0,0]
p = a[4];
for k in range(1,4+1)
p = a[4-k] + (z-x[4-k])*p
```

## Page 25
#### Spline Method
#### Linear Spline
#### Cubic Spline (Skipped)
```text
Hermite Interpolation Skipped
Spline Method
1) Linear spline
2
3
x
1
2
y
0
8
S_i(x) =
y_i + (y_{i+1} - y_i)(x - x_i)
x_{i+1} - x_i
S1(x) =
y1 + (y2-y1)(x-x1) = 0 + (1-0)(x-0)
1-0
x2-x1
Formula:-
f(x) = y0 + (y1-y0)
(x - x0)
x1-x0
61
Q1)
x
22
42
52
82
100
find f(61)
y
4187 | 4178
4186
4199
4217
between
52
- 81
x0
x1
gradient of first
y0 = 4186
y1 = 4199
first point
so f(x) = 52 +
(4199-4186) . (x-82)
82-52
input
f(61) = 52 + 0.433 . (61-82)
Cubic Spline Skipped
```

## Page 26
#### Least Square Method
```text
AX = B
x = BA^-1
Least Square Method
x =
a2
a1
a0
so L(x) =
+ a2 x^2
Q
x
1
2
5
6
7
3x3
1.5
3.8
6.7
9
11.2
13.6
16
4x4
Σx^0
Σx^1
Σx^2
xy
x^2
1.5
1
2
3.8
7.6
Σx^2
Σx^2 Σx^3 Σx^4
3
6.7
20.1
9
Σ
4
9
36
16
7
5
11.2
56
25
A
13.6
6
81.6
36
7
16
Mat A
112
49
314.8
140
Σx^0 y
28
61.8
B
Σxy
Σx^2
Σx^2 y
sum
Σx
Σy
column
Σx^2 y
S
q
p
Ax = B
r
s
x = A^-1 B
so y =
q
N+1
b
total no
A
b
points
use calculator
S P
find x so
[P N+1]
P(x) = a0 + a1(x-x0) + a2(x-x0)
a2
P(4.2)
(x-x1)
a1
a0
```

## Page 27
#### Midpoint Integration
```text
Midpoint Integration
b
2π
sin(x) dx
2π
0
h=4
1/4π
x0
x1 x2 x3
b - a
(4)
= 1/2 π
= f(x0)*h + f(x1)*h + f(x2)*h + f(x3)*h
sin(1/4 π)*1/2π + ... app
error
Absolute error
Relative =
exact
```

## Page 28
### CH#09 - Solving Linear Equations
#### Naive Gaussian Elimination
```text
CH#09
Intro / overview
Solving linear eq using computational methods
e.g
6x + 2y = 4
so A =
6
2
x
1
b
4x + y = 5
4
y
unknowns
constants
A X = b
Solve for x
coefficients
o Direct Methods
pivoting
1. Gaussian Elimination: transform A to upper triangle and solve x
2. LU factorization: Decompose A into LU (lower upper triang)   3. Choleksy Factorization: if symmetric and positive decompose A into LL^T
o Iterative methods
1- Jacobi Method: update variables simultaneously based on prev iteration
all
2- Gauss Seidal Method: update each variable immediately as it's computed
leading to faster convergence..
o Sparse Matrices (scipy tools for efficiency)
: Kirchoff's law (circuit)
o Practical Implementation
Naive Gaussian Elimination.
Steps)
1. Forward Elimination: (Eliminate elements below main diagonal to make upper Triangle)
2. Back substitution: starting from last row, calculate each unknown.
x
y
forward Eli
z
-2
1
-1
1
1 -1
1
2
e.g
5
1
-1
2 -1 1
1
-1
-3
-1 2 2
2
1
0
1
2
z = 2
y+z = -3  so y+2 = -3
(y = -5)
x+y-z = 2  so x-5+2 = 2 , x = 5
```

## Page 29
#### Gaussian Elimination Algorithm
```text
a d g
b e h
c f i
Algorithm:
eliminating b => mik = b/a
then
b - a(mik) = 0
import numpy as np
def Gaus_elim (A, b):
n = len(b)
for K in range (n-1):
for i in range (K+1,n):
if A[K,K] != 0.0:
mik = A[i,K] / A[K,K]
A[i, K+1:n] = A[i, K+1:n] - mik * A[K, K+1:n]
b[i] = b[i] - mik * b[K]
# backward sub
for K in range (n-1, -1, -1):
b[K] = (b[K] - np.dot(A[K,K+1:n], b[K+1:n]))/A[K,K]
return b
4 -2 1 | 11
1- 4 must not be 0
-2 4 -2
-16
2. 4/-2 = mik => ans = -2
1 -2 4
17
3. Row 2 = Row 2 - (0.5) * row 2
do for b too
so -2 = -2 - (-2 * -0.5)
= 0
e.g2)
2
3
2
3
4-(2*2)  -1-(2*3)
4 -1
-7
0
```

## Page 30
#### LU Factorisation
```text
LU Factorisation
U =
L =
triangle such that
LU = A.
so
lower
Steps)
1. start L as identity matrix, U as copy of A
2. Elimination:
By Hand method:
1. Use gaussian for upper triangle 'U'
2. collect multipliers of row operation for 'L'
R3 <- R3 - R2/(4)
-2
R2 <- R2 + (3)R1
a)
-8
-3 -2
-2
8
0
-2
8
-2
A =
31/4
0
0
-3
L =
0
0
+1/4
Algorithm
Modify
Gaussian for 'U'
and 'L'
Use
after this
U
# A
so
def LU(A)
n = len(A)
for K in range (n-1):
for i in range (K+1,n):
mik = A[i,K]/A[K,K]
A[i, K+1:n] = A[i, K+1:n] - mik*A[K, K+1:n]
for U
A[i,K] = mik   // L assigned here
return A
```

## Page 31
#### Solving LU
```text
main();
B =
LU(A)
np.tril(B)
L =
U =
np.triu(B)
Solving
LU
Ax = b
(LU)
x = b
Ly = b
Ux = y
Dont make change
e.g
1
1
1
x =
x1
C =
to C in LU not needed
3
-1
4
x2
6
3
3
R2 - (+4)R1
R3 - (+3)R1
R3 - (-2)R2
1
1
1
4
3
1
0
y
3
3
1
1
1
-1
U =
0
0
0
Assume
y =
y1
Ly = b
y2
y3
original C =
-2
y1 = 1
y2: 4(1) + y2 = 6
so y2 = -2
y3 = 5
so
Ux = y
solve
```

## Page 32
#### Pivoting
#### Gaussian Partial Pivot
```text
Pivoting
error if
A2 =
gaussian
normal
fails ass
so solution is pivoting change order of rows
Gaussian Partial Pivot
before
elimination of below elements to zero
check for Highest No, swap its row.
def pGauss_(A, b, tol=1.0e-15):
n=len(b)
for k in range(n-1):
p = np.argmax(np.abs(A[k:n,k])) + k
find pivot row (row with largest
value in current column)
if np.abs(A[p,k]) < tol: // if pivot too small
raise ValueError("Matrix is singular or nearly singular")
if p != k:
// swap rows
A[[k,p]] = A[[p,k]] // swap row in A matrix
// swap row in B
b[[k,p]] = b[[p,k]]
for i in range(k+1:n): // elimination same as gauss
same mik...
if np.abs(A[n-1,n-1]) < tol: // if last pivot element too small.
raise error("Matrix singular")
Backsubstitution same
rest same
```

## Page 33
#### LU Pivoting
```text
LU Pivoting
LU Pivoting
PA = LU = b
permutation
identity const
matrix
swap
R1 <-> R3
R1 <-> R2
A =
R3 + 2R1 -> R3
R3 - 3R2 -> R3
R3 + 3R2 -> R3
= P
P initially =
2 put in R3
R3 - 2R1
this element
removed by
-3R2 so
so PA = LU
unlike prev
To solve
Dont multiply
result = b[P[i]]
points
to element
instead
before
LUx = Pb
as
Ly = Pb
so
Ux = y
```

## Page 34
```text
Code:
def rowswap(v,i,j):
def LUpivot(A, tol=1.0e-15):
n=len(A)
eye(n)
perm = np.eye(n) // Pa identity matrix
for k in range(0,n-1):
maxrow p = np.argmax(np.abs(A[k:n,k])) + k
find row with max value in current column
if np.abs(A[p,k]) < tol:
"Singular matrix"
if maxrow p != k:
rowswap(A,k,p) // swap rows, A
rowswap(perm,k,p)
in Perm too
for i in range(k+1,n):
Lower = b/a
if A[i,k] != 0.0
Upper = normal elimination
mik = A[i,k] / A[k,k]
return A, perm
def solve(A,b,perm):
n=len(A)
x = b.copy
for i in range(n)
x[i] = b[perm[i]]
for k in range(1,n)
x[k] = x[k] - np.dot(A[k,0:k], x[0:k])
x[n-1] = x[n-1]/A[n-1,n-1]
for k in range(n-2,-1,-1):
x[k] = (x[k] - np.dot(A[k,k+1:n], x[k+1:n])) / A[k,k]
```

## Page 35
### Cholesky's Decomposition
#### Cholesky's Decomp
```text
To solve engine error
-> LX, LT
-> a^2 ab
-> find values of L
Cholesky's Decomp
condition
1- A is symmetric ie
A^T = A
2- A is positive definite
Steps
1. Ax = B
2. A = L x L^T
3. LY = B
4. L^T x = Y
By Hand:
Q1)
4 10 8
144
x1
128
10 26 26
x2
8
26
61
x3
214
X
B
A
condition 1. ok
determinant
2. Positive definite ok
4 > 0
A = L . L^T
step 2)
Transpose
for this
use calculator
for direct
4 = a^2
ab = 10
2 = a
2b = 10
d = 4
b = 5
c = 1
e = 6
f = 3
put into L, L^T
```

## Page 36
```text
so
L, L^T =>
L =
L^T =
Step3)
LY = B
let y =
so
solve for Y
L^T x = Y
solve for x.
Algorithm:
Diagnol elements
square root of difference b/w from all prev
d^2 + e^2 + f^2 = 61
elements in row
f = sqrt(61 - (e^2 + d^2))
Non Diagnol
For i=1:n
Main
L(i,i) = sqrt(A(i,i) - sum_{k=1}^{i-1} L^2(i,k))
Diagnol
for j=i+1:n
L(j,i) = (A(j,i) - sum_{k=1}^{i-1} L(j,k)L(i,k)) / L(i,i)
```

## Page 37
#### Jacobi Method
```text
(P,L,U) = spl.lu(A)
LU
or
(LU,P) = spl.lu_factor(A)
x = spl.lu_solve((LU,P),b)
H = spl.cholesky(A)
cholesky
y =
spl.solve_triangular(H, b, lower=True)
x = spl.solve_triangular(H, y, trans=1, lower=True)
Jacobi Method
Condition for convergence:
Ax=b, A should be diagonally dominant ie
|Aii| >=
|Aij|
A
B
j=1, j!=i
Q1)
must be dominant or coefficient must be biggest in row after even summing other elements
27 > |6|+|1| ok
15 > |6|+|2| ok
so applicable
54 > 1+1 ok
Divide A into
A = D + N
matrix
matrix A
with diagonal zero
with diagonal
so
Ax = b
(D+N)x = b
Dx = -Nx + b
D x^(k+1) =
-N x^(k) + b
so
x^(k+1) = D^-1(-N x^(k) + b)
```

## Page 38
```text
x_i^(k+1) = 1/a_ii (sum a_ij x_j^(k) - b_i)
A
=> condition (Diagonal Dominant ok)
x = 1/27 (85 - 6y + 1z)
now.
y = 1/15 (72 - 6x + 2z)
z = 1/54 (110 - 1y - 1x)
x0 = 0, y0 = 0, z0 = 0
so
# First Iteration =
x' = 85/27
y = 72/15
z = 110/54
# second Iteration
x = 1/27 (85 - 6( ) + 1( ))
code:
```

## Page 39
#### Gauss Seidal
```text
uses newly found
values immediately
Gauss Seidal
Dont confuse
L Same condition as Jacobi
dominant diagonal or symmetric positive definite
with gaussian elimination
condition for convergence
L if not met still can be applied but no guarantee
A = LU
x^(k+1) = L^-1(b - (U.x^k))
computing steps
b
x0 = 0
y0 = 0
z0 = 0
initial
x1 = 1/2 (7+0) = 3.5
y1 = 1/2 (1 + 3.5 + 0) = 2.25
z1 = 1/2 (1 + 2.25) = 1.625
y2 = 1/2 (1 + 4.625 + 1.625)
2nd It:
```

## Page 40
```text
Code:
def gauss_seidal(A,b,x, tol=1e-5, maxit):
n=len(b)
err = 1.0
iter = 0
xnew = np.zeros_like(x) // initialize initial guess x0
M = np.tril(A) // extract lower triangle from A
U = A-M // extract upper T
while(error > tol and iter > maxit)
iter++;
xnew = np.dot(np.linalg.inv(M), b - np.dot(U,x))
err = np.linalg.norm(xnew-x)
return x
Skipped Rest.
x^(k+1) = L^-1.(b-(U.x^k))
```

## Page 41
### CH#10 - Best Approximation
#### Least Square Problem
#### Moore Penrose Inverse
```text
CH#10
Best Approximation
L Obj: Minimize sum of squares of residuals
Least Square Problem
Ax = b has no solution so use Least square - approximate sol
A^T A x = A^T b
Compute A^T A, A^T b
1.
Write in matrix eq A^T A x = A^T b in RREF
2.
3.
Solution is least square.
code:
import numpy.linalg as npl
(x, residual, rank, s) = npl.lstsq(A, b, rcond=None)
Moore Penrose Inverse
x = ((A^T A)^-1 (A^T) b)
tmp = npl.inv(np.dot(np.transpose(A), A))
Amp = np.dot(tmp, np.transpose(A))
```

## Page 42
#### Gram Schmidt
```text
Gram Schmidt
Generates
orthonormal vectors
original
V1, V2, V3 -> U1, U2, U3
basis
U1 = V1
U2 =
V2 - V2.U1
U1
|U1|^2
or
V3 - V3.U1 . U1
V3.U2 . U2
U3 =
|U1|^2
|U2|^2
x1 =
x2 =
x3 =
1) Apply
Gram to
make orthogonal vector
U1, U2, U3
2) use U1, U2.. compute to orthonormal V1, V2, V3
U1 =
U2 =
U3 =
U3 =
36-9+36
4/9
-2/9
5/9
```

## Page 43
#### QR factorization
```text
|| = Magnitude
so if U1 = [a b c]
|U1| = sqrt(a^2+b^2+c^2)
ii)
Normalize
U2 = U2/|U2| = 1/3
Code:
QR factorization
A = QR
upper triangle
orthonormal
To calculate R
matrix
(A -gram schmidt-> orthonormal)
Q^T A = Q^T Q R
Q^T A = R
code
from numpy.linalg import qr
Q, R = qr(A)
```

## Page 44
#### SVD
```text
SVD:
A = U Σ V^T
orthonormal matrix
eigenvectors of A A^T
rectangular diagonal matrix containing sqrt eigenvalues
orthonormal matrix containing eigenvectors of A^T A
[ | | | ]
Steps:
1- A^T A
2- use characteristic eq to find λ => |A^T A - I λ| = 0
so
3- find singular value σ1 = sqrt(λ1), σ2 = sqrt(λ2)
4- for eigen vector
[A^T A - I λ1][ ] = 0 (v1)
- normalize it divide
by magnitude
[A^T A - I λ2][ ] = 0 (v2)
so
V = [[ ]v1 [ ]v2]
Take Transpose for V^T.
Code:
import numpy.linalg as npl
A = np.array([.....])
U, S, V = npl.svd(A)
```

## Page 45
#### Image Processing
```text
Image Processing
import imageio, numpy, numpy.linalg
# Import necessary Libraries
photo = imageio.imread("Newton.jpg") # read image
Red[:,:,0] = photo[:,:,0]
extract RGB channels to seperate matrics
U_r, S_r, V_r = svd(Red)
get U,S,V from each channel using SVD
U_g, S_g, V_g = (Green)
Rank = 100, set of eigenvalue/vectors, higher K = more detail
K = 100
U_r_c = U_r[:, 0:K]; V_r_c = V_r[0:K,:]; S_r_c = np.diag(S_r)
perform
compression
by extracting
top K
comp_image_r = np.dot(U_r_c, np.dot(S_r_c, V_r_c))
compute
each channel
from
compressed
components
comp_image = np.zeros(row, col, 3)
initialize result matrix
comp_image[:,:,0] = comp_image_r
Add RGB channel to result.
comp_image[comp_image<0] = 0 ; comp_image[comp_image>1] = 1
plt.show(comp_img)
show image
plt.show
```

## Page 46
### CH#09 - Leftover
#### Sparse Matrix
#### Sparse Gauss Seidel
```text
CH#09 leftover
Sparse Matrix
from scipy import sparse
sparse_mat = np.array([[2,-1,0,0
[0,0,0,0
[1,0,0,1]])
A = sparse.coo_matrix(S)
coo = non zero stored in an array and i,j store in diff arrays
B = sparse.csr_matrix(A)
coo output
csr output
[2,-1,-10,1,1] => print(S.data[:])
(0,0) 2
[0,1,4,7,8] => S.indptr[:]
(0,1) -1
print(A)
(1,0) -10
[0 1 1 3 2 4 5] => S.indices[:]
indice
value
Spar Gauss Seidel
x_new = L^-1 (b - U x^k)
store A in csr
def sparse_Gauss(A, b, x, tol, err)
code is same just for
n = len(b)
operation on A we access
xnew = np.zeros_like(x)
through sparse.linalg.inverse etc
L = sparse.tril(A, -1, format=csc)
U = sparse.triu(A, +1, format=csc)
for loop
csp
A = np.array([[1,0,1,0,0]
b=
S = sparse.csc_matrix(A)
X = linalg.spsolve(S,b) } solves
```

## Page 47
### CH#08 - Differentiation
#### First order Finite difference approx
#### Second order derivative
#### Richards Extrapolation
```text
CH#08
Differentiation.
Content
1- First order Finite difference approx
f(x0+h) - f(x0)
f'(x0) =
Forward
f(x0) - f(x0-h)
Backward
f'(x0) =
h
f(x0+h) - f(x0-h)
Central
f'(x0) =
2h
2- Second order derivative
f''(x0) = f(x0+h) - 2f(x0) + f(x0-h)
+ O(h^2)
Approximation =
h^2
error
Big O
3- Richards Extrapolation
concept : D = D(h) + ch^p
D = d(h) + E(h)
error
derivative
approx eq
Take two approximation to reduce error
subtract
D = d(h2) + ch2^p
equation
final equation
D = 2^p d(h1/2) - d(h1)
2^p - 1
In forward diff code
d1 = (f(x0+h) - f(x0))/h
Take two
derivative
d2 = (f(x0+h/2) - f(x0))/(h/2)
D2 = h/2
final = D2 x 2
derivative =
2 . d2 - d1
```

## Page 48
#### Euler Method / Runge Kutta 1st
```text
Euler method / Runge Kutta 1st
y_{n+1} = y_n + h f(x_n, y_n)
func of dy/dx
Ex) solve
dy/dx = x + y
with boundary value condition y = 1, x = 0.
find approx value of y for x = 0.1
h = (x^final - x^initial)/steps = (0.1 - 0)/5 = 0.02 = h
5 } assume
Need to calculate
x0 = 0
y0 = 1
x1 = 0.02
y1 = ? = 1.02
x2 = 0.04
y2 = ?
x3 = 0.06
y3 =
x4 = 0.08
y4 =
x5 = 0.06
y5 =
Calculate y1
dy/dx = x+y
y1 = y0 + h f(x0, y0)
y1 = y0 + h(x0 + y0)
y1 = 1 + 0.02(0+1)
= 1.02
y2
y2 = y1 + h(x1 + y1)
y2 = 1.02 + h(0.02+1.02) = 1.0408
y3
= 1.0624
y4 = 1.0848
y5 = 1.1081
```

## Page 49
#### Improved Eulers / Runge Kutta Second
```text
Improved Eulers / Rungekutta second
y_{n+1} = y_n + h f(x_n, y_n)
put the answer
into this eq
y_{n+1} = y_n + h/2 [f(x_n, y_n) + f(x_{n+1}, y_{n+1})]
```
