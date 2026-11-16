# Compiler Construction Notes (transcription)

Auto-transcribed from `Compiler conc.pdf` (OCR + AI correction). Diagrams/tables are approximate.

## Page 1
```text
Compiler Constructor
GAY
MUSHI
PUSHI
Majid Hussain.
Booooo!
```

## Page 2
### Lexemes to Tokens
#### DFA of code
```text
Lexems → Token
1, literals : int, return
Source Diagram
name of variable
2, identifiers : main, x, a, b, c, print
3, punctuators : (, ), {, }, , ;
4, constant :
2, 3, 5, 0
5, Key word / special Key  "The value of x is %d"
6, operators : % = , +, *
int main() {
int x, a=2, b=3, c=5
x = a + b * c
printf(" the value of
%d", x);
return 0;
}
DFA of code
keyword - int, return
L separate DFA for each class
1. identifier
number (0-9)
else
identifier
```

## Page 3
#### Literal
#### Number
#### Operator
```text
(a-z|A-Z|0-9|_)
f
S
a-h
Literal
RE = (") (        )(")
FA
not
Number
RE :
FA
means can be null
Operator
RE = +(+|=)? | -(-|=)? | *(=)? | /(=)?
```

## Page 4
#### Floating point
```text
Not Token ?
2
printf(" i = %d, &i = %x", i, &i);
string counts
identifier
as one.
Total count = 10
Floating point
structure : [sign] digits [dot digits] [exponent]
RE: (+|-)?(0-9)*(.)(0-9)*(e)*?
(+
if it should be a variable not identifier
2: iden
3: if
a-z
Start → 1
3) JFlex.de
L lexical analyzer
1)
Eclipse
2)
JDK, JRE
```

## Page 5
### Sessional 1
#### Phases of Language Processing
```text
Sessional 1
# Tutorial Point YT
Compiler Design
- Intro
- FA and Formal Language
- Lexical Anal
- Parsing Tech
- Automated construction of Elf
- Storage Allocation
- code optimization intro
- code generation
Phases of Language Processing
src program
File inclusion e.g #include
Macro expansion e.g #define PI 3.14
① Preprocessor
replace all PI with 3.14
② translates to assembly code
② Compiler
③ converts assembly to machine code
L relocated
memory not fixed
③ Assembler
⑤ linker
links machine code with external libs
Relocatable machine file
⑥ loader  loads executable program into computer memory to run
④ Linker/Loader
library
files relocatable
object files
Target machine code
```

## Page 6
#### Compiler vs Interpreter
#### Hybrid
```text
interpreter
compiler
- line by line
- slow
Intermediate code generated
- No intermediate code
more memory required as
- less
Everytime
Program not need compile everytime
- Error displayed after every line
Hard Debugging
- easy
- python, ruby
Ex: C++, C
Hybrid
src
compiler
intermediate
Virtual machine
output
input
(interpreter)
byte code (platform independent)
compilation
e.g Java — src code →
JVM (virtual machine)
bytecode
```

## Page 7
#### Phases of Compiler
```text
Phases of compiler
src code
target program
error handler
symbol table manager
Source Prog
Lexical Anal
holds info about identifier, content, usually identifier
Syntax Anal
displays error
symbol
Semantic Anal
Handle
Error
table
manager
Trace scope of variable
Code optimizer
1) Lexical Analysis (Tokenization)
Src code → Token — identifier
, if src code text not recognized as either than error
operator
keyword
punctuator
2) Syntax Anal (Parsing)
- Check if token sequence follow syntax rules of programming language by
- construct Parse Tree based on grammar of language and then verify if token appear in that order.
```

## Page 8
#### Data Structures Used
```text
3) Semantic Anal
logically
- Ensure parsed code make sense semantically
Process
L Type checking e.g int + float X
L Check operations
L No division by 0, etc
4) Intermediate code Gen
Translate high level code to → IR (intermediary representation)
L machine independent
common in Three Address code form → AST - abstract tree
no unneeded info of pure
5)
Code optimization
tree
Techniques, loop invariant elimination
+
e.g t=t+2
eliminate repeated calculations
<id,x> <number,2>
a = t → a = 6
6) Code Gen
by
L Convert optimized Intermediate code → Target code
Process
L Assign register
Data structures used
1, Tokens
L as value of enumerated data type kept by scanner
L single global variable or array of tokens
2, Syntax tree
L pointer based
each node represents info collected by parser may be allocated in symbol
Table
3, Literal Table
4, symbol table .... done previously
5, Intermediate code  L array of text strings
6, Temporary file → hold intermediate steps, solve memory constraints
```

## Page 9
### CH#2 Syntax Directed Translator
#### CFG
```text
CH#2
Syntax Directed translator
Content
Syntax Definition
L definition of grammar
Parse Tree, Ambiguity, Associativity, precedence
Syntax Translation
infix → postfix
Tree Traversal
Parsing Techniques
L Top Down
Left recursion
Lexical Analysis
CFG
lexical syntax semantic
IR
Backend
machine
Src code
Front
end
code
errors
CFG
L syntax of man languages made using CFG,   G = (S, N, T, P)
start symbol
Non terminals  terminals
set of production
rules
1, goal → expr
2, expr → expr op term
3,   | term
S = goal
4, term → number
N = number, id
5,
| id
T = expr, goal, term, op
6,
op → +
P = {1,2,3,4,5,6,7}
7,
| —
```

## Page 10
#### Parse Tree
#### Backend
```text
a)
x - 2 - y
make
Result
Production
goal
1.
expr
goal → expr
expr op term
2.
expr → expr op term
5. term → id
expr op y
7. op → -
expr - y
expr op term - y
2
expr → expr op term
expr op 2 - y
term → number
op → -
expr - 2 - y
expr → term
x - 2 - y
Parse Tree
goal
expr
expr
op
term
expr
op term
(id,y)
-
(number,2)
term
too much detail so in IR AST-abstract tree used as
(id,x)
a IR (intermediary representation)
+
number 2
-
Backend
machine code
Instruction
Register Allocation
Instruction
IR
scheduling
selection
- to produce fast
L put operands
code
in register
as faster than
keeping in memory
```

## Page 11
#### Three Pass
#### Tokens
#### Scanner
```text
executable
object code
Linker
Assembler
Backend
Frontend
Lexical Anal
assembly
Register Allocation
Parser
syntax tree
Code optimizer
tokens
Code optimizer
Semantic Anal
Intermediate code
unallocated
Target independent
Instruction
assembly
syntax tree
selection
src code
Three Pass
Tokens
operators
= + - > ( { := == <> * ! 5 -- ++
keywords
if while for int double, int, float, return
pi, main, a|b, printf, func
identifier
43   6.035   -3.6e10   0x15F3A
constant / numeric literals
char literals
'a'
'\'
string literals
Punctuation symbol
comma, semicolon
1) Scanner (ignore comments)
e.g
pos = init + rate * 60
lexemes
<id,1><=><id,2><+><id,3><*><60>
so
<id,1>
pos
=
<=>/<op>
init
<id,2>
<+>/<op>
rate
<id,3>
+
*
<*>/<op>
60   <id,4> <60>/<const>
```

## Page 12
```text
(left to right) + BODMAS
2)
Parser
Abstract syntax tree
=
<id,1>
<id,2>
<id,3> <60>
3)
Semantic
L typecasting int to float for 60
4) Intermediate code
t1 = inttofloat(60)
t2 = <id,3> * t1
t3 = <id,2> + t2
<id,1> = t3
5) optimize
t1 = <id,3> * 60.0
<id,1> = <id,2> + t1
6) Target code assembly
ld R1, id3
mulf R1, R1
addf
x+ = one or more
x? = optional expression
[a-zA-Z],[0-9] = range of characters
. = single character
```

## Page 13
#### RE to NFA
```text
RE to NFA
eg (a+ba)* ba
seperate
ba
q0
b
a
write * as selfloop so
a
seperate
+ sign
(ab)* + (a+ab)b*(a+b)*
ab
(a+ab)*
b(a+ba+abb) (ba(a+b)*)
a
a+b
ba
ba
ba
abb
NFA to DFA
Next Page
```

## Page 14
#### NFA to DFA
```text
a
a,b
Q1
Convert NFA to DFA
∧
q2
step1 : starting from q0, join it
with state we can go if
so  ∧ closure of q0 = q0q1
input is '∧'
DFA initial state =
q0q1
step2: where can we go if input
q0q1
'a' in initial state of DFA   so
q0 → q0
q1 → q2
q0 a
q1 -
→ q1 (case a=∧)
so
∪
q2
q0q1
union
⇒
q0q1q2
So
q0q1
a   q0q1q2
step3: repeat for b for initial state
so  q0q1 →b→ b(q0) ∪ b(q1)
q1  ∪  q1
q1
q0q1
a
q0q1q2
b
q1
q1q2
step4: repeat for second initial state
q0q1q2 →a→ q0q1q2 (same no other state)
q0q1q2 →b→ q1q2 (add state)
```

## Page 15
#### Minimize DFA
```text
5. repeat for q1 (third initial state)
q1 →a→ q2 (add)
q1 →b→ q1 (same)
Minimize DFA
inputs
a
state
b
q0
a
a
q0
a
q2
b
a
q1
b
b
q3
q4
q2
a
q3
q5
q3
b
q3
q1
q5
q5
q6
q2
q6
1. remove unreachable state from initial
L q6 removed
2. Divide state in classes
accepting
(Final)
π0 = {q3,q4,q5}, {q0,q1,q2}
3. If input of one class goes to same class Divide further
q0 →a→ q1 same ,  q0 →b→ q2 same ✓
1.
q1 →a→ q3 ✗ Diff
q2 →a→ q3 ✗ Diff
π0 = {q0}, π = {q1,q2}
for group 2
q3 →a→ q3, q3 →b→ q1 ✗
q3 ✗
q4 ✓
q5 ✓
{q3} {q4,q5}
```

## Page 16
```text
π1 = {q0}, {q1,q2}, {q3}, {q4q5}
G11
G12
G21  G22
5, Divide further by checking input again
{q0}
G12 → q1 →a→ q3 ✓
q2 ✓
cant divide further
b
6, put q0 as starting state
q0
a
q3
a
a,b
q4q5
b
Thompsons construct
subset construction
L NFA → DFA
Minimize
L(r) is all the strings acceptable by R.E (r)
eg if r = a*b the L(R)
= ab, aab, aaab
```

## Page 17
#### Double Buffering
### Week 3
```text
Double Buffering
L Scanner instead of reading src char by char
load block of chars into memory
2 buffer
when 1 read
other is reloaded
L add EOF marker at end of both buffers
1. initialize both buffer
fill them with N chars
L place sentinal (EOF) at end
2. scan buffer 1, with pointer at first
if pointer == EOF
if(more input)
L move pointer to buffer 2
L refill buffer 1
Week 3
Grammar
Syntax
Parse
Topdown
bottomup
LR(1)
Table
LL(1)
(table)
driven
operator
precedence
(hardwritten)
Recursive-descent
(hardwritten)
semantic
```

## Page 18
#### BNF (Backus-Naur Form)
#### Derivation
```text
BNF (Backus-Naur Form)
::= (→)
E ::= E+T | T
term
so
T ::= T*F | F
factor
F ::= id | constant | (E)
Expression
empty rules
A → B ε or A → ε  useful in Top Down
Derivation
S → Aa
A → Ab | c
S → Aa
cbba
⇒ so
A
Ab
A ⇒ a
A derives a in 1 step
A ⇒* a
" a in zero or more
A ⇒+ a   a one or more
```

## Page 19
#### Abstract vs Parse
#### Left vs Right Derivation
```text
Abstract vs Parse
statement → if-stmt | other
if-stmt → if (exp) statement
| if (exp) statement else statement
exp → 0 | 1
If(0) other else other
Q1)
Parse
Syntax Tree
statement
if
0
if (exp) statement else statement
other
A → aA | b
S → ABC
how to parse abbbc
B → Ab | a
Rightmost
leftmost
C
A
vs
A
B
B
a
b
2 grammars equivalent if describe same lang
or more
grammar producing 2 or more parse trees for same sentence is Ambiguous
```

## Page 20
#### Eliminating Left Recursion
#### Indirect Left Recursion
#### Eliminating Left Factoring
```text
as top down parsers can enter into infinite loop.
Eliminating left recursion
L when nonterminal refers itself on left side of one of its production
⇒ A → Aα | β
1,
E → E+T | T
so
T → T*F | F
E
+ T
. dont know where to stop
F → (E) | id
Indirect Left recursion
E + T
· happen when nonterminal lead back to itself on left
A → Aα | β   if it is in this form
eg A → Ba | b
B → Aβ | ∧
A → βA'
A' → αA' | ∧
Q1) solve it
A → Ba | b
B → Ac | d
E → E+T | T
so
· Sub B into A
A → Aα | β
3) A → (Ac | d) a | b
A → Aca | da | b
so
E → TE'
elim generate direct recursion now
E' → +TE' | ∧
so
A → αA'
E → TE'
A
E' → +TE' | ∧
A → βA'
T → FT'
A' → αA' | ∧
T' → *FT' | ∧
F → (E) | id
Eliminating left Factoring
L process of factoring out common prefix
e.g A → αB1 | αB2
Non Deterministic
same prefix different output B1,B2, left factoring = both production start with
same symbol α
A → αA'
A' → B1 | B2
```

## Page 21
### Dangling Else
```text
stmt → if (E) then stmt
e.g
if (E) then stmt else stmt
stmt → (if(E) then stmt) S'  Substitute the statement after prefix.
S' → ^ | else statement
Dangling Else
Problem :
stmt → if (E) then stmt
| if (E) then stmt else stmt
Q) if x>0
Parse Trees :
stmt
if E the stmt
then z=1
if E the stmt else stmt
or
stmt
if E then stmt else statement x
if then statem
Solution:
stmt → (if(E) then stmt)
stmt → matched stmt | unmatched stmt
matched stmt → if (E) matched statement else matched stmnt | other
unmatched → if (E) statement
| if (E) matched stmt else unmatched stmt
```

## Page 22
### Recursive Descent Parser
#### Indirect Left Recursion
```text
Recursive Descent Parser
we backtrack
S → cAd
A → ab | a
we want cad
so
buffer = cAd
S → cAd
buffer = cAd
a b
✓ × — backtrack in next option
buffer = cAd
buffer = cAd ✓
code
p func S(){
Indirect left
S → Aa | b
A → Ac | Sa | ε
A → Ac | Aad | bd | ε
A → β1A' | β2A'
```

## Page 23
### Precedence
### Associativity
```text
Precedence
lower rule = higher precedence
Associativity
E → E + E | id  always big as L+R recur.
```

## Page 24
```text
```

## Page 25
### Sessional II: First and Follow
#### First
```text
Sessional II
* Find First and Follow - used Topdown parser = LL(1)
Bottom up Parser = LR, LALR, SLR
First(A) contains all terminals present in first place of every string
derived by A
1) S → abc | def | ghi
S
find first for all (abc), (def), (ghi)
2)
First (terminal) = terminal
(abc) def ghi
first first first
3)
First (ε) = ε
a d g
4)
First (nonter) = First (nonter)
1) S → ABC | ghi | jkl
find first
A → a | b | c
a, b, c
B → b
for S → ABC | ghi | jkl
D → d
d
4) start from bottom so D → d
2) S → ABC
everything cut because of ε so ε
⇒ a, b,
c, d, e, f, ε
A → a | b | ε
⇒ a, b, ε
B → c | d | ε
⇒ c, d, ε
C → e | f | ε  e, f, ε
start from bottom
S → ABC
First(S) = First(A)
E → TE'
id, (
E' → * TE' | ε
*, ε
T → FT'
id, (  = first of F
T' → ε | + FT'
ε, +
put instead of A, move
F → id | (E
id, (
if A contains ε
so
S → εBC
First(ε), First(B)
```

## Page 26
### Follow
```text
Follow
Follow(A) contains a set of all terminals present immediate in right of 'A'
Rules:
1. Follow of start symbol is $  so FO(A) = { $ }
2. S → ACD
Note Follow(A) = first of next
C → a | b
find FO(A) ⇒ First(C) = { a, b }
FO(D) = Follow(S)
d has nothing ahead so 'ε' so in this case
3. S → asbS | bSaS | ε
check
Follow ⇒ $, b, a
it where the variable occurs
Right
summary
nothing ahead so
① if right of variable has Terminal
'ε', follow never
contain ε so
that will be follow
② if right = variable
↳ find first
1) S → AaAb | BbBa
③ if right = ε
A → ε  ab
↳ follow of left
hand side of
B → ε,
find FO(A) so S → AaAb
FO(A) = a, b
FO(B) = FO(B) = b, a
2)
S → ABC
FO(A) = First(B)  ∩ S → ABC
A → DEF
First(B) = ε so
S → AεC
B → ε,
so
B or ε so FO(A) = First(C) = ε, so S → A
C → ε
D → ε
E → ε
F → ε
FO(A) = follow(S)
```

## Page 27
### Parsers
#### Check if LL(1) Grammar
```text
* Parsers
Parser
Topdown Parser
Bottom up
works on some
ambiguous grammar
Recursive
LR(k)
descent
predictive
left to right scan
operator precedence
input string
LR(0)  LR(1)
LALR
most powerful
least
leftmost derivation
1 look ahead
left to Right string scanning
* Check if LL(1) grammar
o Find First, Follow for all production
t1 t2 t3 $
o build Table with production, terminals
P1
P2
e.g
o for each production fill, for P1 ex Find first and for the terminal result
write production number there in the cell
t1
t2
P1
1
o if 'ε' is the result of first
P2
P3
then for that production go to left hand side
and find follow of that, fill table cell with follow
o If any cell has more than 1 value that not an LL(1) grammar
```

## Page 28
```text
Follow
Follow(A) contains a set of all terminals present immediate in right of 'A'
Rules:
1. Follow of start symbol is $  so FO(A) = { $ }
2. S → ACD
Note Follow(A) = first of Next
C → a | b
find FO(A) ⇒ First(C) = { a, b }
FO(D) = Follow(S)
d has nothing ahead so 'ε' so in this case
3. S → asbS | bSaS | ε
check
Follow ⇒ $, b, a
variable occurs
Right
summary
nothing ahead so
① if right of variable has Terminal
'ε', follow never
contain ε so
that will be follow
② if right = variable
↳ find first
4) S → AaAb | BbBa
③ if right = ε
↳ follow of left
A → ε  ab
hand side of
B → ε,
production
find FO(A) so S → AaAb
FO(A) = a, b
FO(B) = FO(B) = b, a
2)
S → ABC
FO(A) = First(B)  ∩ S → ABC
A → DEF
First(B) = ε so
S → AεC
B → ε,
so
B or ε so FO(A) = First(C)
= ε, so S → A
C → ε
D → ε
E → ε
F → ε
FO(A) = follow(S)
FO(A) = $
```

## Page 29
```text
* Parsers
Parser
works on some ambiguous grammar
Topdown Parser
Bottom up
Recursive
LR(k)
operator precedence
descent
predictive
input string
left to right scan
LR(0)  LR(1)
LALR
least
1 look ahead
* Check if LL(1) grammar
o Find First, Follow for all production
t1 t2 t3 $
o build Table with production, terminals
P1
P2
P3
o for each production fill, for P1 ex Find first
and for the terminal result of First
write production number there in the cell
t1
t2
1
o if 'ε' is the result of first
P2
P3
then for that production go to left hand side
and find follow of that, fill table cell with follow
o If any cell has more than 1 value that not an LL(1) grammar
```

## Page 30
#### LL(1) Parsing Table Examples
```text
Fill table with
first of each production
S → asbS | bSaS | ε
ε
1)
with follow(LHS)
First : a, b, ε
- No conflict = LL(1) ✓
Follow : $, b, a
$
terminals
a
b
if first = ε then
S
1
2
production
$ so S → first ⇒ a, first = b, & first = (ε)
means S → asbS...
fill follow : $, b, a
follow fill
so
a b $
1/3 2/3 3
S
more than 1 entry X not LL(1)
2) S → (L) | a
①
2
$,
2)
(, a
L → SL'
(, a
L' → ε | , SL'
first
follow : Fo(S) = $, (first(L') = ε, ,) , ($, , , follow(L)) → { $, , , ) }
put in so
FO(L) = { ) }
FO(L') = follow(L) = { ) }
(
a
S
1
2
L
3
3
L'
4
5
first(L') = ε, ,
so follow(L') = ')'
```

## Page 31
#### Shortcut to Check LL(1)
```text
Shortcut to check LL(1)
condition 1. find first for production if disjoint (No common) element then LL(1)
e.g S → aSa | bS | c
first = a, b, c ✓  LL(1) ✓
2. if first 'ε' then still if follow is disjoint then LL(1) ✓
S → iCtSS1 | a
= i, a
e.g
S1 → eS | ε
first = e ✓, ε,
C → b
= b
Follow S1
Fo(S1) = Fo(S)
Fo(S) = $, first(S1)
Fo(S) = e, $
disjoint so LL(1) ✓
```

## Page 32
### LL(1) Parser: How It Works
```text
Gate Smashers Lecture 10 : What is LL(1), how it works
leftmost
left to right
derivation
meaning
S → AA =
A → aA
a' A'
1 Lookahead
Q1) S → AA ①
A → aA ②
is this accepted by LL(1) parser ? by input string a b a b $
A → b ③
1. make Table
$
a
b
a
b
S
S → AA
1
or
S
A
2
3
write production no.
A
A → aA
A → b
2. Make stack, read string Left to Right
1. push symbol
a b a b $
Now look ahead is - watching
last will have dollar
'a' from input so for S row go to a column (Table)
↳ Rule1
↳ S → AA
in reverse
order
push
and
cut S
pushed here
push start symbol
first symbol is $
2. Now read top of stack = A, input is still a, Table ⇒ aA push, cut A
3. Now 'a' is top of stack, matches 'a' input string so go to next input b
4. 'A' stack top, b input, Table = b, push b
5. 'b' stack top, b input, match move input  6. 'A' stack top, a input, push Table = aA
```

## Page 33
```text
7. stack top = a, input = a, cut a, move a
input a b a b $
8. stack = bA, inp = b, Table = b push
9. stack = b, input = b, cut
10. stack = $, input = $ cut
Finish Accepted
```

## Page 34
### LR(0) Parser
```text
they work by expanding
Rightmost derivation
in reverse
E ⇒ E+E
= E+(E+E)
right
= E+(id+id)
= id+(id+id)
LR(0) - gatesmasher
↳ bottom up parsing
e.g
↳ make canonical items
E → T+E | T
T → id
add dot
step 1 : Introduce extra variable $ E' → .E
↳ means we have to process element on right
E' → .E  • means process E so E → .T+E | .T
↳ means process T so T → .id
combined
accept state
state number
step 2 : make items by '.'
E
E' → .E
E' → E.
E → T+E.
reduced 1 production state
E → .T+E
T
E → T.+E
+
E → T+.E
E → .T
reduce
E → T.
T
E → .T+E
means put dot on every E
T → .id
E → .T
id
T → .id
item / stage 0
reduced
arrow
goes back
reduced state
state 3
↳ dot reaches end
acceptance
↳ dot reaches end of E'
state
id
+
$
E
T
reduce state
with augment for a new production
0
S3
1
2
make Table
1
Accept
-
-
shifts
2
R2
S4
R2
R2
3
R3
R3
state 2 contains
4
S3
5
2
R2 in any cell
5
R1
R1
o for NonTerminal cell add S for shift
If Table has more than 1 entry, then not accepted
```

## Page 35
#### LR(0) Through Stack
```text
S → A.  R1
S → .A
A → .(A)
(
A → (A.)
4
)
2
A
A → (.A)
A → (A).
A → .a
a
5
R2
A → a.
3
R2
a
A
$
A
Table :
State
(
a
0
we go to S3 not R3
1
S2
S3
1
2
3
R2
R2
R2
4
S5
start with $0, read input e.g id so Table state 0 → S2
id
→ S2 add in stack
5
R1
R1
R1
if reduce then substitute
if no state ahead, check prev
instead
and reduce B3.
LR(0) through Stack
state, traverse table, add state
e.g
remove number
So
C3B :
remove letter
Action
stack
input
$0
id = id * $
$0 id 2
= id * $
r4 → id
$0 4
```

## Page 36
```text
```

## Page 37
### SLR(1)
#### Limitation of LR(0)
```text
SLR(1)
↳ same states as LR(0)
Difference : Parse Table Shift is same, Non Terminal same
reduce is diff
↳ LR(0) we wrote Reduction in full row of table
↳ in SLR(1) we write Reduction in
the follow of LHS of production
Previous Ex
follow
$
E → T+E / T
* Blue is same
T → id
+, $
accept
E' → E.
E' → .E
E
4
T
+
E → T+E.
E
E → .T+E
+
E → .T+E
T
E + T+E
E → .T
E → T.
E → .T+E
5
T → .id
T → .id
id
id
T → id.
id
id
+
$
E
T
S3
0
1
2
Accept
LR(0) had conflict
for
S4
R2
here but SLR(1)
doesn't
follow of E = $ so
3
R3
R3
2
So
This grammar is SLR(1)
5
R1
SLR(1)
(LR(0))
* limitation of LR(0)
1 - Shift-Reduce
S → x.by
S → xb.y
B → ab.b
B → abb.
2 - Reduce Reduce
S → x.b
S → xb.
can't be
B → ab.b
B → abb.
both reduce
```

## Page 38
#### SLR(1) Example
```text
follow
Q1) S → xX | ay
a) create LR(0) DFA
$
X → xXy | Y
b) specify conflict of LR(0)
Y → a
c) create SLR table
3
S' → S.
y
x X x
S' → .S
S → .X
X → x.Xy
y
S → .ay
X → .xXy
a
Y → a.
X → .xXy
Y → .a
X → .Y
X
S → X.
Y → .a
a
Y
1
S → a.y
X → Y.
Y → a.
y
S → ay.
1. Shift Reduce conflict
states
x
y
a
$
X Y S
0
S2
S5
3 4
1
accept
2
S2
S7
6 4
3
R1
R1
R1
R1
R4
R4
R4
R4
S8/R5
5
R5
6
7
8
9
```

## Page 39
#### SLR Stack
```text
simple LR(1)
SLR stack
State
a
b
c d e
$
A
S
0
S2
S' → S
S → CAd
A → ab | e
2
S4
3
S6
4
S7
5
Stack
Input
Action
$0
ced$
Sc → 2
$0c2
ed$
Se → 5
$0c2e5
d$
rd → 3 so A → e
substitute
d$
$0c2A
2A → 3. Find number
through table
$0c2A3
d$
r1 → 1 so S → S/cAd
$0c2A3d6
$
$0S
$01
Accept
0 S → 1
Shift S → Accept
Parse Tree, start from lowest of stack table, build by looking at reduced
S
C A d
A
e
```

## Page 40
### LALR(1)
#### CLR Example
```text
Finals
Look ahead LR(1)
LALR(1)
↳ same as CLR but merging
↳ same as LR(0) but lookahead symbol
CLR Example
follow(S') = $
CLR
LALR
Q1) S → AA ①
A → aA | b ②③
lookahead symbol
step 1. S' → .S, $  lookahead of S' is $ always
lookahead
first of symbol
after .A[ ]
S → .AA, $
Follow(A) = first of
{A, $} = a | b
S → AA., $
so
S' → S., $
A
S' → .S, $
A → a.A, $
2
A → .aA, $
A
A → .b, $
S → A.A, $
S
S → .AA, $
b
A → .aA, $
A → b., $
A → .aA, a|b
A → .b, a|b
A → aA., a|b
A → a.A, a|b ②
A
a
b
A → .aA, a|b
a
A
A → b., a|b
A → .b, a|b
b
$
A → aA., $ ④
3, 4
```

## Page 41
#### Merge for LALR
```text
Parsing Table write where look
ahead symbol is
a
b
$
S
A
states
S3
S4
0
1
2
Accept
S6
S7
2
5
S3
S4
8
4
R3
R3
4th state reduce = A -> b., $ | b | a
write in lookahead symbols
5
R1
R3, reduce of 3rd production
5th state reduce = R1 at $ lookahead
6
S6
S7
9
R3
7
R2
8
R2
9
R2
Merge state with same item/production and different lookahead
Rule
* Merge for LALR
e.g A -> a.A, $
A -> a.A, a|b
A -> .aA, a|b
A -> .aA, $
-> merging state 3, 6, merge entries of table at row 3, 6
A -> .b, $
A -> .b, a|b
same
different
a|b|$|S|A
36
89
A -> b., $|a|b
A -> b., $
also mergable. thus
check for conflict so
combine 4,7 from table
conflict?
A -> aA., a|b
A -> aA., $
also
a|b|$|S|A
mergeable
R3
R3
R3
89
state
R2
R2
0
-> Steps: iterating from state 0
so final LALR table =>
check if any other state
2
has same item, diff lookahead
LALR valid
36
-> merge check conflict
47
-> merge other, check conflict
89
o If no minimizing/merging possible, then CLR = LALR parser
n7, n2 not states
not state in LALR
```

## Page 42
### CH#6 Semantic Analysis
#### SDT (Syntax Directed Translation)
```text
* Attributes
properties or values associated with nodes of tree. They represent
type of variable
value of variable : x.val = 5
Size, location
CH#6 Semantic Analysis (3rd phase)
Constraints
whether exp can be assigned a value
(Lvalue
vs Rvalue)
SDT (Syntax Directed Translation)
synthesized - S Attribute
Grammar + semantic Rules
inherited
Applications
Semantic Anal
Annotated Parse Tree
Grammar
Rules
Q1
S -> S # A | A { S.val = S.val * A.val; }
A -> A & B | B { A.val = A.val + B.val; }
B -> id
{ B.val = id.lval; }
given input string 5#3 & 4, find output
Make parse tree for input using Grammar + Rules
S
hash will be * according to rule
#
& = + according to rule
A
B
A
id
B
4
3
5
```

## Page 43
#### Parsing SDT
#### How to Evaluate Arithmetic Exp
```text
Parsing SDT
Top Down
Bottom up
S -> AS { printf(1) }
output depends on rules
S -> AB { pf(2) }
A -> a { pf(3) }
B -> bC { pf(4) }
a 3 | a B
B -> dB { pf(5) }
b
C -> c { pf(6) }
output = 132354 X
output = 3364521
input = aadbc
output = 3364521
find output?
T = T-F
E =
How to Evaluate Arithmetic Exp
E -> E & T { E.val = E.val * T.val }
&
| T { E.val = T.val }
T -> T @ F { T.val = T.val - F.val }
| F
{ T.val = F.val }
F -> num { F.val = num }
input = 4 & 8 & 8 @ 5 & 7 @ 3
use rules
to reduce
Top
Final E answer = 48 & 2
```

## Page 44
#### Types of SDT
```text
if parent takes
value from child e.g A -> XYZ
if child takes
value from
from sibling
sibling
Types of SDT
parent
* S-Attribute SDT
* L-Attribute SDT
L> Based on synthesized
L> Based on both synthesized and
L> use bottom parsers
inherited attribute (Parent or left only
sibling)
L> Semantic Rules always written
in rightmost position
L> Topdown Parsing
L> semantic rule anywhere in RHS
A -> XYZ { semantic Rule }
A -> X Y Z
semantic rule
1) A -> LM { L.i = l(A.i), M.i = m(L.s), A.s = f(M.s) }
2) A -> QR { R.i = r(A.i), Q.i = q(R.s), A.s = f(Q.s) }
L taking value from A
A take from M
(inheritance)
(inherited)
(synthesized)
R takes from A
Q <- R (right siblings)
(inherit)
(synthesized)
inheritance
1,2 is not S attributed as inheritance
1) is L attributed but 2 isn't as right sib
Type system, symbol Table, Dependency Graph
```

## Page 45
#### Dependency Graph
#### Type system
```text
Simple reflex Agent (simple)
environment + action
e.g
vacuum room = on
reflex agent with state
, if clean = go to other room
e.g vacuum if dirty
on
goal based agent
utility based agents
goal evaluated e.g 'less fuel, less time, safety' car
represent flow of info among attributes in parse tree
used to determine order of attributes in parse tree
Annotate Parse Tree = shows values of Attributes
graph dep
how values can be computed
E -> E + T    E.val = E.val + T.val
5+12=17
3*4=12
E -> T
=
T -> T * F
= T.val * F.val
T -> F
=
F.val = digit.
T=5
T=3
F -> digit
5 + 3 * 4
F=5
3
digit.val=5 digit
L Needs to know
syntactic constructs of lang
Basic Type of Lang
Rules for assigning type to construct
```

## Page 46
#### Key concepts of Type system
```text
Purpose, catch errors
enable optimization: help generate efficient code knowing data size & operations
Key concepts of Type sys
Type Expression
describes type of Lang such as variable, func, exp
Basic Types (Primitive)
integer
real : decimals
boolean
char
void : No value (functions)
L> type constructors
L build complex types
e.g
Syntax
Array
array(index,type)
array(1...10, integer)
Record
record(Field : type)
Function
domain -> Range
L> Type declaration
L> Recursive Type
Union
e.g
typedef unsigned long ulong;
* typedef struct Node{
typedef struct {
int data;
struct Node* next;
char name[20];
int
}
L> Type equivalence determines when two types considered same by compiler
1. Name equivalence
L if names same e.g }
2. structural equivalence
struct S1 { int x, float y }
e.g
struct S2 { int x, float y }
```

## Page 47
#### Type inference & type checking
### CH#7 Runtime environment
```text
* Type inference & type checking
auto determine type of exp
verify operation uses compatible type
based on context
Key comp
o verify compatibility with type Equal
and symbol table lookup
CH#7 Runtime environment
L system to manage program execution
- Allocate/manages memory for variable
- Handle procedure exec (func, recursion)
Compiler makes code for runtime environment
- Optimizes execution for target machine
3 types - 1 Fully static
memory preallocated at compile time, no changes in runtime
Fixed memory, no dynamic or recursion
simple + fast but no dynamic/recursion and waste of
2- Stack based
memory it left
empty
L uses stack, allows recursion
each func creates activation record on stack
storing local variables, parameters
memory layout
content
code
execution instruction
global
Static Data
variable, constants
Activation records, local var
Heap
Fully Dynamic
Dynamic allocated obj
L memory allocated at runtime using heap
Free space
supports dynamic data st. eg linked list
global + static
heap
```

## Page 48
#### Heap Allocation
#### Garbage collection
#### Parameter Passing
```text
Stack
n*f(n-1)
n*f(n-1)
fact(int n){
if(n<=1) return 1;
else
return(n*fact(n-1));
24*4
24*5=
n*f(n-1)
input => n=5
output = 120
Static
f(n)
f(n)
n*f(n-1)
f(n)
n
n*f(n-1)
0 4 3 2 1
f(n)
n*f(n-1)
f(n)
output = 1
Heap Allocation
memory required (malloc(100)) - heap manager search for free block
+ size
memory free ( free(ptr) )
divided
marked free
header stores
block
adjacent memory coalesced to reduce fragmentation
calls when malloc fails
Garbage collection
Mark and Sweep
Stop and copy - Divide
divide heap into active/inactive
space, copy object to new space
inactive
Generational (recently made) likely to become garbage
Before call
x=5
Parameter Passing
e.g
Function increment (num)
Copy in num gets
num++
copy of x=5
call by Value
exec: num++ so num=6
by reference
main:
x=5
increment (num x)
call by value result
print(x)
of num(6)
copied back
call by Name
if call by
value it would be x=5
```

## Page 49
### Intermediate code Generator
#### Methods to Generate IC
#### 3 address code
```text
CC contin.
Intermediate code Generator 4th phase
L Generate machine independent code
code that works on
e.g
LA
SA
different PCs you dont have
for using code in
PL
to go through LA, SA again
Intermediate code runs on it.
* Methods to Generate IC
e.g (b*c)+(b*c)
1.
Abstract
syntax
Tree
2. Direct Acyclic graph
3
1
3. Postfix
bc* bc* +
L> max three address used
t1 = b*c
4.
3 address code
t3 = t1+t2
3 addr,
(Ways to write /syntax)
then you optimize it.
Assignment
x = y op z  e.g x=a+b
x = -z
x = op z
x = z
Jump
L conditional if x relop y go to L
e.g
if(x<y) goto to
line number
unconditional goto L
Array
x = y[i]
L
x[i] = y
x = &y
L
x = *y
convert postfix = (a+b)*(a+b+c)
= (ab+)*(ab+c+)
= ab+ * (ab+c+)
= ab+ab+c+*
```

## Page 50
#### Representation of 3 address Code
```text
Representation of 3 address Code
Quadruples, Triples, Indirect Triples
-(a*b)+(c*d+e)
Quadruples
Triple
Indirect Triple
t1 = a*b
operator
op1
op2
result
operator
op1
op2
instruction
address
t2 = -t1
a
b
t1
0
a
b
100
(0)
t3 = c*d
1
-
t1
t2
(0)
101
(1)
t4 = t3+e
2
c
d
t3
*
c
d
102
(2)
t5 = t2+t4
3
+
t3
e
t4
3
+
(2)
e
103
(3)
t5
4
(4)
(4)
4
+
t2
t4
(1)
104
can move statement / rows order
Less space
can move
but 2 memory
references
For (i=1; i<=10; i++)
If (a<b)
make 3 address code &
x = y+z
0) if a<b goto (2)
x = y+z
else
0) i = 1
P = Q+R
1) goto (5)
1) if i<=10 goto (4)
2) t1 = y+z
2) goto (9)
3)
x = t1
4) goto (7)/exit
3)
t1 = i+1
5) t2 = q+r
i = t1
4)
6)
P = t2
5) goto (1)
7) END
6) t2 = y+z
7)
x = t2
8) goto (3)
9) End
```

## Page 51
### Code optimization
#### Loop Optimization
```text
Dead code
Code optimization #25
indep Techniques
1- Register Allocation
2- Use of Addressing modes
L> loop optimization* Loop unrolling, code movement, frequency
reduction, loop jamming
3- Peephole
a) Redundant LOAD/STORE
b) Flow of control opti
c) use of machine idioms
-> constant folding - eg π = 22/7
-> constant prop e.g πr² = 3.14*r² evaluate at compile time not run time
-> Common subexpression elimination
Strength reduction
a = b*c
x = b*c
->
x = a
Loop Optimization
Algebraic simpl
Deadcode
most time utilized in loops
1) Code Motion (frequency reduction)
a = 100
Shift outside loop so less frequency of calculation
while(a>0){
x = y+z   evaluated 100 times but not used in loop so
same result each time
if(a%x==0){
printf("%d", a);
}
make sure logic not affected
loop fusion
2)
int i, a[100], b[100]
Combine loops
O(n)
for(i=0, i<100, i++){
O(n+n)
a[i] = 1;
for ( same)
b[i] = 2;
```

## Page 52
#### Loop unrolling
```text
3) loop unrolling
for(i=0,i<5,i++){
printf("vacuum")
Print("Vacuum")
Print("Vacuum")
Print(...
Print(...
Print(...
Theory of
code
Qs,
for( i=0, i<n
a) contains loop invariant comput
for( j=0, j<n
b) a common subexpression eliminated
c) scope of strength reduction
if(i%2){
d) scope of deadcode elimination
x+=(4*j+5*i)
for( i...
put t=5*i
dont need to calculate
it again in J loops
for(j...
move it
up no point
if(i%2){
of running
x+=(4*j+5*i)
i%2==0
True
for(
for(
z = 4*j
True
x+=(4*j)+5*i);
y+=(7+4*j)
Strength Reduction = shifting high time consuming operation with low time consum
instead of z = 4*j
True
left shift so z =
2 times
less computing
```

## Page 53
#### Basic Blocks
```text
Loop optimization Gatehub
1- Detect loops by using control flow analysis using program flowgraph
2- For PGF we need Basic Blocks
d) deadcode
sequence of 3 address statement
where control enters at
Doesn't participate in code
the begining and leave only
at end with any jumps or halt
False all code takes part
code:
TAC
i=1
if(i<=10) goto
3
TAC -> loop - control flow Analysis
optimization
Basic Blocks
B1
-> to find BB find leader in TAC, BB will start from
basic block
B2
1 leader to next leader
but dont include next leader
Leaders:
L> 1. First instruction of TAC = leader
o If cycle found loop detected
2. Any instruction that is target of conditional/uncon jump = leader
3. Any instruction that follows a cond/uncon jump = leader
control
C code: fact(n){
TAC
f=1
L4
int f=1;
for(i=2,i<=n,i++){
if(i>n) goto 8
f = f*i;
t1 = f*i
B2
f = t1
B3
i = i+1
B4
go to calling f
B2
cycle of
i=1
entry
B1
j=1
t1 = 5*i
t2 = t1*j
t3 = 4*t2
t4 = t3
a[n]=1
i = j+1
B3
local: apply to basic block
Global: across basic block
10
i = i+1
if( ) goto 2
peep-hole: Apply across boundary
```

## Page 54
#### Machine Independent Optimizations
#### Strength Reduction
```text
Skipped for now
Q1,
A = b*c + (-a)/e
Ans,
Machine Indep
Constant folding = replacing exp that can be computed at compile time by its value
C = 2*3.14*r => C = 6.28*r
also if a<b goto L1 -> goto L1
if a,b known
at compile time
Strength Reduction:
Cheaper
Expensive
Tail recursion elimination
x*x
L replace recursion with iteration
x2
to avoid stack frame
2*π
x+x
x/2
x*0.5
B = A*2
B = A<<1
Algebraic Simplification
x+0 = 0+x = x
, x-0
x*1 = x
x/1 = x
Constant Propagation: temp4=0
replace constant value assigned
f0 = temp4
f0 = 0
->
temp4=1
f1 = temp4
f1 = 1
copy propagation
t2 = t1
t3 = t1*t1
t3 = t2*t1
t5 = t2+t1+t3
t4 = t3
t5 = t3*t2+t4
```

## Page 55
#### Peephole optimization
```text
Peephole optimization
Machine Dep
Register
1)
Redundant LOAD/STORE
a = b+c => Load Ro,b
a = b+c
Load
Ro,b
d = a+e
Add
Ro,c
d = a+e
Store
a,Ro
Add
Ro,e
Ro,a
Store
a,Ro
Add
Ro,e
Store
d,Ro
3) eliminate Dead code
2)
Avoid Jumps on Jumps
L1 : jump L2
L1 : jump L4
Directly
jump to L4
optimized
L2 : jump L3
4) Use of Machine idioms e.g increment
L3 : jump L4
i = i+1
Load Ro,i
Add Ro,#1
L4 : x = a+b+c
Store i,Ro
inc i
```

## Page 56
#### Liveness Analysis (Register Allocation)
```text
not included
Liveness Analysis (Register Allocation)
L Assigning multiple variables to single register w/o changing logic
Question 1) while (x1,E1) S1
S1 for (x2 E2, x3 E3, x4 E4) S2, y
initialized variable
condition
loop operation
E1
3
3rd
2nd 2
E1.val -> E1.code
E1.code -> E1.val = x1.val
S1.code -> FOR.code
1st code & 2nd
1st
E2.code -> E2.val = x2.val
E3.code
E1.code
E4
Label L2
S2.code -> y.code
if E1.code.val false
go to End
3 For.code = E2.code // initialize variable
label L1:
S1.code -> E2.code
E3.code
Label L1
if-false E3.val go to
label End
E2.code
S2.code = y.code
E4.code
// loop increment
Go to L1
```

## Page 57
```text
while(x1)
E2.val -> E2.val = x2.val
(for x2 x3 x4)
E3 . . .
E4 . . .
S2.code = y.code
2nd
FOR code
while
E2.code
Label L1:
E1
if false E3.val go to End
x1
S2.code = y.code
E3.code
S1
E3
E4
S2
Goto L1
x2 x3 x4
y
Label End:
3rd E1.code -> E1.val = x1.val
S1.code = FOR.code, S1.val = FOR.val
while 4th, write Label L0
Loop
if E1.val False goto End
End code:
E1.code
S1.code
goto L0
Label End:
Q) convert to TAC if(a<b)
x = y+z
else
P = Q+R
t1 = a
if a>b go to else
t1 = y+z
x = t1
Label else:
```

## Page 58
#### Stack Runtime
```text
Stack Runtime
int x=2;
global/static
y
void g();
Activation rec of MAIN
void f(int n){
m=2
AR of g
control link
static int n=1;
return address
g(n)
n=1
AR of f
control
x--;
}
void g(int m){
m=1
AR call to g
control
return address
int y=m-1;
y=0
if(y>0){
f(y); n--; g(y);
free space
}
main(){
g(x)
Stack frame layout
Parameter 1
4
calling seq
1- compute arguments and store in new A.R
return address
-4
local var1
2- Store fp as control link in new A.R
local var2
12
3 - change fp so it points to beginning of the
Q1 int fib(int n){
4- store Return address in new Activation record
int a,b;
local var x
main
return address
if(n<=1) return n;
n=9
a = fib(n-1);
AR of fib(9)
a =
return a+b;
n=8
}
main(){
int x = fib(9)
return 0
}
```

## Page 59
### Cheatsheet
#### LL(1) check
#### LR(0)
#### SLR(1)
```text
Cheatsheet
First => first(F) = first(T)
if ε comes go next
* Follow(X) => look right side of X, if t
if T take first
if ε take follow of LHS
* LL(1) check
S -> ab | aA
1
2
find follows of all production e.g
if first not common for a production e.g
1 x
conflict
if first = ε, LHS follow, fill table check conflict.
input 'a, b, c'
Stack
1. Push S
if 'a' matches, move to next input
2. read input 'a'
match with
top of stack
$S
and cut
e.g S
if production
a
S
2
go to table and push production for 'a'
so
means S -> ac | b
push 'ac' and cut
* LR(0)
S -> .S
table
state | a,b,c $ , A, B
0
S
1
S/R
2
X
2) SLR(1)
L write
Reduction
in follow of LHS
```
