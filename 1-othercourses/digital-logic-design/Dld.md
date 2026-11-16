# Digital Logic Design Notes (transcription)

Auto-transcribed from `Dld.pdf` (OCR + AI correction). Diagrams/tables are approximate.

## Page 1
```text
```

## Page 2
### Digital Logic Design
```text
Digital Logic Design
Proteus software to make virtual circuit
Base = allowed digits
Chapters
- Number System
- compliments (for subtraction)
1st sessional easy after mid circuit designing starts
- Combinational circuits = easy
- sequential circuit = hard.
Morris Mano Exercise Qs
```

## Page 3
### Number System
```text
24th Jan 2023
Number System
Radix = base
Radix
decimal
0-9
10
Binary
2
(0,1)
Octal
8
(0-7)
Hexadecimal
16
(0-9)(A-F)
Decimal Numbers =
7392
10^3 10^2 10^1
10^0
weight of digit
7×10^3 + 3×10^2 + 9×10^1 + 2×10^0
when converting (any base value) ---> (base 10)
use weightage formula
Conversion to
r=2
r=10
Decimal
(101)2
1×2^2 + 0×2^1 + 1×2^0 = 5
a) Memorize 2^6 tak powers
(10111) ---> 2^4×1 + (2^3×0) + 2^2 + 2^1 + 2^0 = ( )10
b) (418) X octal doesn't have 8
base=8
b) (417)8 -> ( )10 = (417) = 4×8^2 + 1×8^1 + 7×8^0 = ( )10
c) (412)5 -> ( )10 = 4×5^2 + 1×5^1 + 2×5^0
Any base could be given
d) (ABD)16 -> ( )10 = 10×16^2 + 11×16^1 + 13×16^0
```

## Page 4
#### Decimal to Any Base
```text
Decimal to Any Base
417.38
Different methods for both parts to be converted.
For Integers
(reverse of pichla method (Divide)
Divide decimal number with required base, keep
track of remainder
1) (13)10 -> ( )2
Remainders
LSB
so
2
13
6
2
2
3
= (1101)2
1
1
MSB
2) (333)10 -> ( )2
333
2
333
2
166
1
2
83
3) (333)10 -> ( )5
5|333
66
3
13
= (2313)5
1
2
3
2
```

## Page 5
#### Octal Number System
```text
(3596)10 -> ( )8, ( )5, ( )2
8
3596
449
4
56
= (7014)8
1
7
0
7
5|3596
719
143
4
3
28
3
= (13341)5
5
3
Octal Number System
r=8
( )8
radix
2^3 = 8
Q1) Why is it needed
Word size compress
Binary -> Octal
a) 010
110 001 101 011 . 111 100 000 110
must be
3 bit group
5
7 4
0
6
2
6
= (26153.7406)8
Octal to Binary
b)
(3542.146)8 -> binary
(011 101 100 010 . 001 100 110)
```

## Page 6
#### Hexadecimal
#### Decimal (Fractional Part)
```text
Hexadecimal
a) (10 1100 0110 1011 . 1111 0010)2 -> ( )16
00
=)
2 C 6 B . F 2
2^3
2^2
2^1
2^0
0
= 0
0
0
0
0
1
= 1
0
0
1
0
= 2
0
0
1
= 3
0
0
0
0
0
1
0
0
1
Hexa to Octal = Hexa to get binary to octal
Decimal (Fractional Part)
Q1) (0.6875)10 -> ( )2, ( )8, ( )16
fraction
0.6875 × 2 = 1.375
integer
coefficient = a-1
a4 a3 a2 a1 . a-1 a-2
0.375 × 2
= 0.75
a-2
```

## Page 7
### Compliments
#### DRC (Diminished Radix Compliment)
```text
1.5
0.750 × 2 =
0.5 × 2 =
1.000
Until zero come,
integers = 1011
so after point . 1011
divide 42 wala method
Q) What if zero doesnt come
e.g
0.0333
4 d.f so divide 4 times
Compliments
Diminished Radix compliment . (r-1)'s
Radix Compliment r's
Decimal (r=10)
diminished '''' = 9's = (r^n - 1) - N
DRC
1) (5467)10 find 9's compliment
r = given base = 10
N = given number = 5467
n = no of digits = 4
So
(10^4 - 1) - 5467
= (10000 - 1) - 5467
= 9999 - 5467
= 4532
```

## Page 8
```text
b) (1101)2 find D.R.C or 1's compliment
= (r^n - 1) - N
= ((2^4 - 1) - N
=) 16 - 1 - 1101
pichla wala was 4 9's
make it Binary
=)
1111 - 1101
=)
Not gate on this shortcut
=)
0010
Shortcut
Just invert / Not gate the given number
1 -> 0
and
c) ( )8 DRC
0 -> 1
inverts
a) (021398)10
b) (546700)10
c) (1011000)2
d) (0101101)2
a) 999,999 - 021398 = 978601
b) 999,999 - 546700 = 453299
c) 0100111
d) 1010010
e) (512)8 find 7's compliment
777 - 512 = 265
```

## Page 9
#### RC (Radix Compliment)
```text
(r^n - N)
RC
n = non zero number
546700
Q1) (546700)10 find 10's compliment
leave all
1) First non zero least significant digit unchanged.
2) First non zero least significant digit is subtracted from
'10' and all higher digits are subtracted from 9
546700
453300
* Method 2 (preferred)
first find (r-1)'s compliment than +1
546700, D.RC = 999999 - 546700 = 453299 + 1
= 45300
(110100)2 find RC
1+1 = 0 carry to next
DRC = 001011 + 1 *
0
c) (532)8
DRC = (777 - 532) + 1 = 246
```

## Page 10
#### Addition of Binary
#### Subtraction with R's complement
```text
31st Jan 2023
Addition of Binary
1+1+1 = 3 = 11
1+1 = 2 = 10 in binary so
1100
shortcut = every pair of 1 generates a carry in next column
1001
101100
Subtraction with R's complement
(M-N)r
How to subtract via R's comp
step 1 • No of digits of M and N should be same
Q1) (72532 - 3250)r
Digits not same add zero
= 03250
step 2. The number that is negative (N) take its R's complement
Ans) 03250
R's compl = (99999 - 03250) + 1 = 96750
10's compliment
```

## Page 11
```text
step 4, Add calculated compliment to M..
Ans)
72532 + 96750 = 169282
Extra from end answer
step 5, check end carry   72532 + 96750 = 169282
5 digits + 5 digits = 6 digits
6th digit, Discard it.
Answer = 69282
Q2) (3250 - 72532)r
03250
10's compliment = (999,99 - 72532) + 1
= 27468
Add)
27468
it is in 10's compliment format
03250
30718
real answer is negative = - 6928
Note
If there is an end carry than
Representation of compliment
M>N
If no end carry N>M ; Ans = negative
of negative numbers is different
```

## Page 12
```text
(30718) take its 10's compliment again to reverse it
= (999,99 - 30718) + 1
= -69282
If no end carry
take compliment
and add negative
sign to it
Q3) a) (1010100)2 - (100011)2
base
compliment of N = [(2^7 - 1) - (100011)] + 1
= 1010100 + 0101011
2's compliment's
= 1011100 + 1
Invert bits and add 1
Add them
=
1010100
+ 1011101
10110001
```

## Page 13
#### Subtraction by R-1's compliment
```text
Q1) (72532 - 3250)(r-1)'s = 9's compliment
Case 1, M>N
No of digits same
= 03250
Take (R-1)'s of N
= (9999 - 03250)
don't add 1
= 96749
Add them
= 72532
096749
carry is always
169281
1 at end
add
= 69282
Q2) (03250 - 72532)(r-1)'s
Case 2) N>M
9's comp = 999,99 - 72532 = 27467
Add = 03250
+ 27467
30717
(No end carry) so
Take compliment
=>
99999 - 30717 = 69282
Q3
1010100
0100011
(invert)
= 1011100
1's comp
Add
1010100
1011100
0110000
0110001
=
```

## Page 14
### Signed Binary Numbers
#### Signed 1's Compliment
#### Signed 2's Compliment
```text
b) 0100011 - 1010100
comp = 0101011
add
=
0100011
0101011
Signed Binary Numbers
Signed-Magnitude
Signed-compliment-representation
representation
Signed 2's compliment
Signed 1's
leftmost signed bit
compliment representation
* signed bit repns +9 = 01001 magnitude
-9 = 11001
Default is unsigned binary, if signed binary used its already mentioned.
Signed 1's compliment
Note
+9 = 0000 1001
+ve numbers
-9 = 1's comp of +9 = 1111 0110
don't change
representation
in any format
Signed 2's Compliment
+9 = 0000 1001
(2's compliment of 9) -9 = 1111 0111
```

## Page 15
```text
8 bit representation
+6
+13
Add them
signed 2's complement system
+6 = (0000 0110) in representation signed 2's compliment
+13 = 0000 1011
0001 0011 = +19
Q b) -6 + 13
Add 1
-6 = 1st comp = 1111 1001 => 1111 1010
+13 = 0000 1101
Add them
1111 1010
0000 1101
1 0000 0111 = +7
carry
discarded
b) 6-13
+6 = 0000 0110
-13 = 1st
1111 0100 = 1111 0101
Add
No carry take 2's compliment
=
1111 1010
0000 0101 +1
=
0000 1110
```

## Page 16
```text
2nd Feb 2023
Signed Binary Numbers
Q1) -6 - (-13)
0000 0110 = 6
0000 1101 = 13
1111 1001 + 1 = 1111 1010
= -6
2nd com
1111 0010 + 1 = 1111 0011
= -13
Subtraction of 2's complement
M-N
method = take compliment and add.
```

## Page 17
### Binary Code Decimal (BCD)
#### Addition in BCD
```text
Binary Code Decimal (BCD)
cost and time effective
each of decimal digits with a binary code
4 bits represent each decimal digit
2^3 2^2 2^1 2^0 = 8 4 2 1
8421, code is a type of BCD
It is a weighted code
Although 4 bit can represent 16 number, in BCD only 10 used
6 combinations
1010, 1011, 1100, 1101, 1110, 1111 are invalid
Q1 a) 35 in BCD
BCD subtraction
0011 0101
= 00110101
b) 98 in BCD
10011000
c) 2469
0010 0100 0110 1001
Addition in BCD
Add two BCD using rules of Binary
if 4 bit sum is equal or less than 9 then valid
if greater than 9, or carry out 4 bit group generated
invalid result
* valid
a) 86 + 13
1000 0110
0001 0011
1001 1001 = 99
valid   valid
```

## Page 18
```text
Invalid
Q2)
9 + 4
1001
+ 0100
1101
Invalid BCD > 9
0110
Add 6
0001
0011
valid
= 13
1
3
Q3)
9 + 9
before
1001
if carry but came
add Six
carry
1001
invalid
0010
Invalid
Add 6
+ 0110
0001
1000
Digit added if num > 9, Add 6,
Q4) 184 + 576
After adding 6 the carry added to
184
next weight
0001 1000 0100
0101 0111 0110
576
1010 invalid
0110 Add 6
0000
carry
0111
Ans =
0111 0110 0000
```

## Page 19
### The Gray Code
```text
The Gray code
unweighted
can have any no of bits
only exhibits only a single bit change from one word to
next in sequence
used in axes of Karnough maps
0
0
00
1
01  2 bits changes
1
01  1 bit changing
2
10
2
11
3
11
3
10
Binary to Gray
discard
carry
m.s same
1+0
1+1 = 10
Binary
1
0
+ 1
1
0
Gray
1
1
Move left to
discard carry
Gray to Binary
1+1 = 10
0+0 = 0
Gray
1
1
0
1
1
Binary
1
0
0
1
m.s same
```

## Page 20
### ASCII
```text
ASCII
128 characters
symbols represented by 7 bit binary code
first 30 are unprintable e.g Null, Escape
65 - A
Table would be given
90 - Z
97 - a
122 - z
Binary representation also given, Binary -> Decimal -> char Ascii
TODO
2421
Excess 3
understand this
8, 4, -2, -1
2421, Excess 3 are self complementing
```

## Page 21
```text
```

## Page 22
### Duality Principle
```text
9th Feb 2023
Duality Principle
Every Algebraic expression deducible from the postulates
of Boolean Algebra remains valid if the operators and
the identity elements are interchanged
operation
e.g A + 0 = A
Duality A . 1 = A ~ rule is valid.
element
operator reversed identity reversed
changed
e.g A + A' = 1
Dual A . A' = 0
1, A + AB = A
A . (A+B) = A
complement
A + A'B = (A+B)
Q, x'y'z' + y + xy'z', reduce to 2 literals
= A(A+B) = A
10- Rule
11- Rule
= (A+B)(A+C) = A+BC
y'z'(x'+x) + y
y'z' + y = y+z'
b) x'y'(x'+z') + x'y + xyz
x'y'x' + x'y'z' + x'y + xyz
x'y' + x'y'z' -
x'y'(1+z)
```

## Page 23
```text
x'y'((x'+z')+1) + xyz
x'y'(1) + xyz
x'y + xyz
y(x'+xz)
Solution 1
x'yx' + x'yz' + x'y + xyz
(x'y) + (x'yz') + x'y
x'y + x'yz' + xyz
x'y(1+z) + xyz
x'y.(1) + xyz
x'y + xyz
y(x'+xz)
- Rule 11 A'+AB = (A'+B)
y(x'+z)
Solution 2
x'y(x'+z') + x'y +
xyz
A
B
A + xyz = x'y + xyz
y(x'+xz) - rule 11
y(x'+z)
```

## Page 24
```text
Q1,
(x+yz)' + (x+y'z')'
Demorgan (xy)' = (x'+y')
(A+B)' = A'.B'
x'(y'+z') + x'(y'+z')
x'((y'+z') + (y'+z'))
x'(y'+z')
Solution
[x'.(yz)'] + [x'.(y'z')']
= x'.(y'+z') + x'.(y+z)
= x'.((y'+z') + (y+z))
Q1)
(w'+x)(w+y)(x'+y)(w+xyz) reduce to 4
literal terms
(w+y)(w+xyz)
(A+B)(A+C)
= A+BC - Rule 12
so w + xyz = (w+xyz)
(w'+x)(x'+y)(w+xyz)
```

## Page 25
```text
```

## Page 26
### Standard and Canonical Form of Boolean Expressions
#### Minterms
```text
Standard and canonical form of Boolean Expressions
Boolean Exp
Canonical Form
Standard Form
Product of
sum of minterms
Max terms
product terms
OR terms
Sum of
products
(SOP)
(POS)
Number of variables
2^n
= Combinations of variables outcomes
e.g, 2 variables
x y y'
x'
2^2 = 4
00 01 10 11
xy x'y yx' y'x'
Minterms
AND terms / Product terms / Minterms
mi  Minterm
Mi
x y
z
any x,y,z all present
0
0
x'y'z'
m0
x+y+z
0
0
1
x'y'z
x+y+z'
• Minterm must have
m1
x+y'+z
0
x'yz'
all variables of the
x'yz
x'+y+z
function
0
1
0 0
xy'z'
0 1
xy'z
e.g y'z isn't a minterm
0
xyz'
xyz
m7
M7
Max
term
```

## Page 27
#### Max terms
```text
Max terms,
Sum of terms
Must have all variables
x'+y'+z =
1 1 0
= M6 (Pichla
page table)
Q1) f(x,y,z)
x
x,y,z
F
0 0 0
1
m0
0 0 1
0
0 1 0
1 m2
0 1 1
1
m3
1 0 0
0
1 0 1
1
m5
1 1 0
0
0
=) F(x,y,z) = m0 + m2 + m3 + m5
x'y'z' + x'yz' + x'yz + xy'z
b, F'(x,y,z) = Σ(1,4,6,7)
= m1 + m4 + m6 + m7
= x'y'z + xy'z' + xyz' + xyz
• Min term and Max term are compliments of each other
b, Product of Max term to find minterm jo may doesn't have
F(x,y,z) = M1M4M6M7
= (x+y+z')(x'+y+z)
= (x'+y'+z)(x+y'+z)
```

## Page 28
```text
*Shortcut
how many variables missing
= AB'C
+ A'B' + ABC'D
10
= 1 0 1
0
0 0 0 0
11 = 1 0 1
0 0 0 1
1
3
0 0 1 1
minterm generator
2^2 = combination
Σ(0,1,2,3,10,11,13)
Q,
F(x,y,z) = xy + x'z
Convert SOP -> POS (max terms)
x y  z missing
1 1  0
x'z
y missing
1 1  1
0 1
1
F(x,y,z) = Σ(2,3,6,7)
= Π
(0,1,4,5)
number from 0-7
that are not in
like summation but for product
Σ
• Important if question asks to solve using Boolean Law
SOP
Rule-12 {A+BC = (A+B)(A+C)}
POS
to break product
(x'+x)(x'+y)(z+x)(z+y)
(xy + x') = (xy + z) =
A
BC
```

## Page 29
```text
F(x,y,z) = x'y + xyz
x'y
x'y + xyz
x,y,z
xyz
write terms of minterm
where 1 comes.
x'y
x'y + xyz    F = m2 + m3 + m7
x y z
xyz
Function
0 0 0
Minterms where
(1)
0 0 1
1 0 0
1 0 1
1 1 0
1 1 1
```

## Page 30
### Karnaugh Maps
#### 2 variable KMAP
```text
16th Feb 2023
V. IMPORTANT
Karnaugh Maps
• Limitation = 5 variable functions
* 2 variable KMAP
x
• every row of truth table becomes a
y
0
m0
cell in K-map
0
0
1
m1
0
m2
m3
input
x
m0
xy
m2
m3
• If you move into adjacent cell, they only vary by
1 bit
only 1 bit changes
```

## Page 31
#### 3 variable K-map
```text
* 3 variable K-map.
yz
y'z'
y'z
yz
yz'
11 differ by 2bits
00
01
10
x
0
x'
000
001
010
011
m3
m0
m2
x
100
101
110
111
m4
m6
m7
m5
000
001
011
010
m0
m1
m3
m2
100
101
111
110
m4
m5
m7
m6
• KMAP is circular,
m0, m2 are also adjacent
m2's spot taken by m3
xy
z
m0
m1
m2
```

## Page 32
#### 4 variables
```text
* 4 variables
yz
wx
00
01
11
10
00
0000
0001
00
0010
m0
m1
m3
m2
01
0100
0101
0111
0110
m5
m7
m6
m4
1101
11
1100
1110
10
m12
1000
1001
1011
1010
m8
m9
m11
m10
• m1, m9 are adjacent
• m0, m8 are adjacent-
F = Sum of minterms
F(x,y,z) = Σ(1,3,5,7)
Q1, Fill Kmap with f(w,x,y) = Σ(0,1,5,6,8,9,10,11,
```

## Page 33
#### Implicants
#### Prime Implicants
#### Essential Prime Implicant
```text
Thursday  DLD
Implicants
All groups possible, doesn't have to be max size
* Prime Implicants
Those groups which are in their max possible size
2nd Prime
Implicant
prime implicant.
3rd prime implicant
4th implicant
* Essential Prime Implicant.
Minimum if doesn't overlap its a essential prime Implicant
a cell cant be of any other group
Group that doesn't overlap.
both
essential
prime
max size no overlapping
A'B'  A'B  AB  AB'
= B'D' + BD + AD + B'C
C'D'
essential
C'D
prime implicants.
```

## Page 34
#### POS from KMAP
```text
• Minimum groups
essential
POS from KMAP
Q, F(A,B,C,D) = Σ(0,1,2,5,8,9,10)
reduce F, using KMAP and give ans in POS
AB
A'B'  A'B  AB  AB'
• instead group
CD
0's
• Reverse compliments
from 0's grouping
F' = AB + CD + BD'
F = (A'+B')(C'+D')(B'+D)
b) F(A,B,C,D) = A'B + AB'C + CD
A'B'  A'B
AB  AB'
C+D
(D+A)(A'+C)(B+C)
A+B
= F =
A+B'
A'+B'
A'+B
```

## Page 35
### Logic Gates
#### Inverter
#### And
```text
Logic Gates
• Inverter
when input low, output high and vice versa
High (1)
High (1)
(0)
Low (0)
Low (0)
t1  t2
t1
t2
input pulse
output pulse.
And
AB
truth table
B
(AB+B)'
B
```

## Page 36
#### KMAP with Don't Cares
```text
• complement priority highest then demorgan
A  B  AB
AB+B  (AB+B)'
0 0
0
0
1
0 1
0
1
0
1 0
0
1
1 1
1
0
Circuit
Truthtable
Boolean
expression
F(A,B,C,D) = Σ(0,2,3,5,7,8,10,11,14,15)
Identify Prime, essential prime
essential
Prime
Prime
Prime
Prime
KMAP with Don't Cares
F(A,B,C,D) = Σ(1,3,7,11,15)
d(A,B,C,D) = Σ(0,2,5) given in Qs
assume x's 1 to make
size of group
Not needed
assume
to be 0
```

## Page 37
### Exclusive OR
#### Ex-NOR
```text
9th March 2023
x
y
Ex-OR
x ⊕ y = x'y + xy'
F
• if inputs different then
y
0
output 1
0
1
1
Ex-Nor
(x⊕y)' = (x'y + xy')' = xy + x'y'
F
• If input different output = 0
1
0
0
1
Properties
• x ⊕ 0 = x
• x ⊕ 1 = x'
• x ⊕ x = 0
• x ⊕ x' = 1
• x ⊕ y' = x' ⊕ y = (x ⊕ y)'
```

## Page 38
#### Odd / even functions
```text
• Commutative and associative property holds
Odd / even functions
A
B
* ODD Function
operations
operation
(A⊕B)⊕C = (A'B+AB')⊕C'
= (A'B+AB')'C + (A'B+AB')C'
(A⊕B)'
Ex-NOR = (AB+A'B')
= (AB+A'B')C + (A'B+AB')C'
open bracket
= ABC + A'B'C + A'BC' + AB'C'
111
001
010  100
minterms
7th
1st
2
4
F = Σ(1,2,4,7)
How odd = Binary representation has
odd no of 1's
e.g 7 = 111 = 3 ones
4 = 100 = 1 one
odd
• if F = Σ(1,2,4,7) then F' = Σ(0,3,5,6)
cell blank = odd
If first
then
BC
complement
even
A
is even
checker board
chess
configuration
board
(chess board)
- if KMAP is chess then apply
Ex-OR gates
```

## Page 39
#### Parity Generation and checking
```text
odd
CD
even
AB
AB
A ⊕ B ⊕ C ⊕ D     (A ⊕ B ⊕ C ⊕ D)'
Parity Generation and checking
Parity bit is extra bit included in a binary message
to make it even or odd
even
x
Parity bit
y
z
1 (1)
1 (2)
minterm
1 (4)
1 (7)
• parity is even function is odd
F = Σ(1,2,4,7)
x
circuit for parity generator
P
y
z
x ⊕ y ⊕ z
```

## Page 40
#### Checking
```text
Checking
P
C  checker
x
y
z
0 — No error
1 — Some error
1 — parity is even but output 1
circuit for parity
checker
z
If you put p=0, circuit would be of parity generator as p ⊕ 0 = p
```

## Page 41
### Combination Circuit
#### 2-bit Binary Comparator
```text
Combination Circuit
B
A
4
Gel
no
0
B
B1
BO
design a 2 bit binary comparator
≤ 2^n
n ≤ 2^n
input output
Q1. Make Truth table
A1 A2 B1 B2 G L E
E
1
0
0
0
0
0
1
```

## Page 42
### Design of Combinational Circuit
#### BCD to Excess-3
```text
Design to Combinational Circuit
BCD to excess-3
1) from the specification of the circuit determine the required
number of input, output
input BCD output excess Three
D
2) Derive the Truth table
Input 2^4 = 16 combination
A,,B
C
D
2
0
0
0
0
0
0
0
0
0
1
0
0
o
0
0
1
0
0
0
0
0
1
1
0
1
0
0
1
0
0
0
1
0
1
0
00
0
0
0
0
0
1
0
0
0
0
0
0
1
0
0
1
0
0
0
0
X x
X
X
0
1
xX
N > 9 not valid BCD
0
0
XX
X
X
1
0
1
X
1
0
X
X
1
X X
X
X
```

## Page 43
#### 4-bit Gray Code to Binary
```text
Design circuit
4 bit
b) Convert 4bit gray code to Binary
A
B
C
W
Y
2
T
0
0
6
0
0
0
0
0
0
0
0
0
0
1
&
0
1
0
0
0
1
0
0
0
1#
10
0
0
1
1
0
0
1
0
0
0
0
0
1
0
0
0
0
1
0
1
1
0
0
1
0
0
1
0
0
1
0
1
1
1
o
0
1
01
a
18
0
0
0
1
1
0
0
1
0
0
1
1
0
1
0
1
1
00
0
1
1
1
1
0
0
1
000
1
0
1
x1a
0
81
110
1
1
401211029
KMAP X
KMAP W
CD
-AB
AB
1
1
AB
1
AB
1
A
F
W = A
A'B + AB' = X
Dont need to plot as most significant
Bit same
ACHA2
wexzpk
```

## Page 44
### Half Adder
#### Full Adder
```text
21st March
Half Adder
0y
Truth Table
A B Carry Sum
coms
A
B
HA
0
0
0
0
0
0
1
8
A
H.A
S
0
0
0
KMAPS
Carry =
sum
B
B
B
A
B
S = x ⊕ y
A
C = xy
checkerboard
X
y
S
C
need to add
3 bits
A
so use
Full Adder
B
H.A
s
ACHAZ
```

## Page 45
### Adder/Subtractor Circuit
```text
(Adder/ substractor circuit)
control input
0 = adder
* 4bit adder / substractor circuit
1 = substractor
M
A11
A3
A2
Ao
CD
FA
FA
PA
FA
53
52
s1
so if substractor
Cy
c3
e
when M=0
so carry 0
when adder (control bit = 0), XOR Gate makes
no change due to property
A=1011
B=0111
2's compliment
B 1's comp = 1000, 2's comp = 1000+1
mD
1001
A
SDE
fA
FA
XOR GATE
C2S1
es
8B
ci
52
B0 ⊕ 1 = B0'
```

## Page 46
### Overflow Detection
```text
Overflow detection
+70 +80
01000110
10010110
-70 -80
carry bit
)
0111010
0110000
```

## Page 47
### Decoder
```text
Wednesday - morning
n input lines
2^n output lines
22
8
e
2
00 binary = 1
00
5
as 101= Sinbiag
2 input decoder
A| B
00|a1
Q2
10
A
0
0
0
1
0
0
B
0
)
0
1
0
0
0
0
0
Q
1
1
KMAPs =>  Q0 = A'B'
Q1 = A'B
Q2 = AB'
Q3 = AB
AB
B
Make circuit
Qs
L
4
D
1
```

## Page 48
#### Enable Input
```text
Enable Input
Used as a power button for an IC
use to combine smaller decoders to make a bigger decoder
1) Power Button
Active High Enable = when enable one IC on
En
Active low Enable = Turns on when enable low (0)
off when
En=0
Si
S2
0
Q2
Q3
bubble sign = Active low
En
En
0
X
X
0
0
0
1
0
0
1
0
0
0
1
1
0
0
0
0
1
1
0
0
0
1
0
1
1
0
0
0
1
Using NAND GATE to make circuit
Invert the output column, as AND and NAND are
compliment
Do
En
51
S2
Q
Q2
a3
X
0
1
1
1
A
0
0
0
1
1
1
1A1
0
1
0
1
A1
0
4
1
1
1
0
1
0
E
1641
En
A1
2x4
A2
```

## Page 49
### Encoder
#### Priority Encoders
```text
Encoder
Dolod
22
20
n
Ferceder
Do
taa
D2
D3
-0
if D0 on = 00
if D1 = 01, if D2 = 10, if D3 = 11
outputs
Do
D1
D2
D3
X
Y
x = D3 + D2
0
o
0
1
1
y = D3 + D1
1
00
0
c
1
a
a
0
0
e1
10
0
0
0
0
Priority Encoders
D0/ x
D3
2
y
0
0
0
0
X
X
0
0
0
1
0
D
more priority
of D1 so D0 loose
0
0
1
0
1
0
0
0
1
9
- More than 1 input on, encoder cant function
1
0
1
0
0
1
0
properly so give priority D3 > D2 > D1 > D0
0
1
0
1
1
could be different
0
1
0
1
0
1
0
1
1
1
1
0
0
0
1
1
Ds on so priority,
0
0
1
1
output controlled
0
0
1
1
1
1
0
0
```

## Page 50
```text
KMAP
make X, Y, make boolean eq, circuit
02
1
X
0
o
0
0
0
0
1
D3
0
0
1
X
D
1
0
D
koe
0
X
X
1
0
0
0
0
simplified
1
D3
D11 D0
N
a
0
0
X
0
0
0
0
0
0
0
X
Q
1
0
X
X
1
0
X
Q1, make Truth Table of Priority D0 > D3 > D1 > D2
Dont make Table with Random order, must be either ascending or descending
D3 D2
short and must have diagonal
D3/D2
DI
D0
X
X
0
0
X
G
k
o
0
X
1
X
0
1
1
0
1
0
Q
(
0
0
1
e
0
1
X
X
X
a
0
Dont care about Low Priority
Higher P must be 0
KAGH
```

## Page 51
### Multiplexer: Enable Input and Demux
#### Implementation of Boolean Function
```text
Enable input on Mux
if 1 mux is on
join 2 mux (Reuse Decoder)
If input output reversed
DeMux
Io
y
I{2
I3
s 10
Selector input define
where logic output (which to block)
2
51
3.
2,
I.
I3
0
0
0
0
0
0
0
0
0
O
1
0
0
0
0
Decoder
Table is same
(Decoder can act as a demux)
Implementation of Boolean function
Q1, Implement this Boolean F(A,B,C,D) = Σ(2,3,5,7,10,11,15)
Selector
input
2^4 = 16 Data input
16x1
```

## Page 52
```text
Reduce
3 inputs
from a mux
S3
So
S2
S1
A
B
C
D
0
0
Q
0
0
Io
I,
o
0
0
1x91
12
0
4:
I3
0
0
Different
I4
0
0
0
(e
Q
0
0
a
0
0
0
3.0
a
if 0001
I12
0
1
0
C
0
0
I
If you have
8x1 mux
2
4
8x1
3 input instead of 4, Dont add D as least priority
A B C
```

## Page 53
```text
c)
4x1 Mux
C
0
Io
I1 =
0
D
AB
for I0, Y depends on C, D,
Y = C
AB
I7
0
0
0
0
0
make kmap for I3 -> C D
4x1
so
```

## Page 54
#### Quadruple 2 to 1 Line Mux
```text
Quadruple 2 to 1 line Mux
4(2 to 1 mux)
-es
2x1
y
So
soy
to
Q
T1
so>o
4(2 to 1)
Az
B1
7Au
A_3
B1
03
B2
A1
B3
D
B
B4
Selector
selector
BA
has 4 bits
1 input - 4 outputs
B
```
