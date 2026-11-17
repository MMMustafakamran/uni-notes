# Information Security Notes (transcription)

Auto-transcribed from `Infosec.pdf` (OCR + AI correction). Diagrams/tables are approximate.

## Page 1
```text
```

## Page 2
```text
Info sec
```

## Page 3
### Intro to Infosec
#### Objective
#### Challenges
#### Protection
#### Terms
#### Risk mitigation
```text
1) Intro to Infosec
Hashing
L convert data into fixed
Objective:
length hash, any change
A
L so Integrity
C
Availability of Data
confidentiality
accuracy
DDOS prevention
Security
• Hashing
- Load Balancers
• Configmap
convenience
- Software Backup
• checksum (CRC)
Authentication
: verify user
Authorization
: permissions
Accounting
: Track Activity
ABC
Challenges:
Personal security
Information security
Authentication
Authorization
Auditing
Accounting (Read usage)
Terms
Asset
Threat
Threat Agent
Threat Likelihood
Risk mitigation
Avoidance
Acceptance
Mitigation
Deterrence (inform attacker
of consequences)
Transference (transfer risk to 3rd
party)
if you find Vulnerability
Bug Bounty (tell victim company
Zero Day Broker : sell bug to people
Black Market : sell bug directly
```

## Page 4
### Ploutus ATM
#### Mirai botnet
```text
Ploutus ATM-
ATM jackpotting
variant
backdoor malware Trojan
encryption vs hashing
Mirai botnet
IP camera into botnet used to launch DDOS
Scans IPv4 space - weak login credentials
L password guesses
AAA
auth Authorization
Accounting
```

## Page 5
### Advanced Persistent Threat (APT)
#### Cyber kill chain
#### Defence
```text
Attacker
Advance
Persistent
APT advance persist
L stealthy, long term attack
cyber Kill chain
Real
1. Recon
- gather info about vulnerability
Wild
2- weaponization
- creating Malware /exploit
Days
3- Delivery
- Transmitting weapon to target
Eat
4- Exploitation
Ice
attacker installs malware/backdoor
Cream
5- Installation
malware
6- Command & Control
malware/compromised system communicates
with the attacker server
7- Actions on objectives
ultimate goal eg data theft
Hacker
Grey
White
Black
Cyber
L script kiddies
Defence
Layering related : firewall
to avoid single
point
of failure
Diversity
Surface
Simplicity
: reduce error in security system / easy to manage, reduce attack
Obscurity
- encrypt data / hide internal systems
Limiting
- access control
```

## Page 6
### Carbanak Malware APT
```text
Carbanak Malware APT
L backdoor trojan - targets finance institutes through
spear phishing emails
Capabilities : Surveillance, remote control, data theft
2013, 1 billion US
Microsoft word 97 -2003 redirection
shellcode decrypts, executes a backdoor
remote backdoor
L minimal person
Malware
Carberp
Anunak
= Carbanak
software
malicious
acting as customer
cve = common vulnerability & exposure of word  • Spear phishing
targeted
bypasses
filter of gmail
go to & window32 \system32, rename itself svchost.exe + reverse shell
not detected by Antivirus
surveyed Admin employees
Screenshot (20second)
Key logging + desktop video sharing +
+ http form grabbing
software
hardware
was used
payload
+ can destroy OS
+ outlook Account
L function that performs malicious attack
```

## Page 7
### Malware
```text
Logic Bomb/Rootkits
Spyware
Ransomware
Malware
Worm
Trojan
Virus
Look like
Succosandbox
needs
human
legit software
flare vm
intervention
but spys/steals data
intervention
No Human
phone
VMware
e.g Link
autoconnects c&c server, deliver
to Wifi, forces payload
delete/edit listed
Virus Total Antivirus
Data
in the network
Signature Base
Adware
Behaviour Base
screen crash, buffer overflow
bypassable
fork bombing
Manual
Ransomware - encrypt pc ask ransome
Root kits - hide malware by altering OS, logic bombs  Both hard to detect
Man in middle
Document Based
macro
Computer virus
document Virus
Program Virus
Clicks
Boot section Virus
executable
infects
files
has the hidden keylogger can
Encrypt payload
Packer
Payload
Android -> sandbox -> secure
```

## Page 8
### Malware Analyst
```text
Virustotal -> Database
Benign.
Malware Analyst
L Notepad ++
L PEiD Scan exe, magic bit tell if malicious
1) Signature based (code chunk in DB matched) {
Fast
2) Behavior based L Analyzes what programs do in sandbox
malware bazaar
can detect new
Original Program
Makes it
Entry
easy
point
Oligomorphic detects
pool of decrypt
Poly morphic detection
avg
malware changes  Metamorphic encryption
code
harder to make
Avg
and detect
rewrites own code entirely
Hardest to detect
```

## Page 9
### Code Red Worm
```text
Code Red Worm
L White house DOS
Made 100 threads
L static IPs,
Trojan
```

## Page 10
### Social Eng Attacks
### Cryptography
```text
Premixed
Social Eng Attacks
-> Phishing (Digital/Technical)
filters add in spam (text)
-> spear phishing (D/T) : target to small group, specific
g00gle.
phishing
-> image phishing (D/T),
similar URL e.g g
-> whaling (D/T) - Physical : target high profile eg CEO, deep research
-> vishing
trash, recycle bin
(D/T) voice phishing, use voice call impersonate
-> Typo squatting / URL hijacking (D/T)
-> Dumpster Diving (Both) -> Baiting(P)
-> Tailgating / Piggy backing (Physical) -> Impersonation (both)
access to restricted areas
-> Pretexting (Both): create fake scenario eg Posing as HR to collect data
-> Pharming : redirect user from legit to evil websites
Crypto Graphy
A -> 0
Z -> 25
Text encryption
, video Encryp -> steganography
plain text -> cypher text
plaintext
decrypt
Decryption
encryption
key
K1
x
E
Algo
Algo
cypher Text
x = (Y, K1)
PT
Y(x, K1)
secure PT
```

## Page 11
#### Types of cryptogram
#### Classical Cipher
#### Caesar cipher
#### ROT13
```text
XOR = 0 if bit same
1 if bit diff
key = 123
XOR
10 rounds
Apple -> XYZ
-> 1st round
AES256
4 subrounds
Sbox
advance encryption standard
rotation
to prevent Man in the M attack
XOR
Types of cryptogram.
collision
loophole
1° Symmetric Key crypto (1 key = secret) - AES/DES
2° Assymetric (1 public + 1 secret) - RSA, ECC
3° Hashing
L one way protocol/irreversible
SHA256
SHA 512
cipher
Classical Cipher  monoalphabet = same character replace same character
of plain
x = URooJ -> RAZZx,
Substitutional
Transpositional
CT = PT + Key mod
cipher plain
26
matrix - change position (Transpose)
x = URooJ -> OROJU
y =
JUMP ->
J -> J+3 = M
doesnt work for digit, space
Reverse = PT-3
U => X
M => P
P
=> S
ROT13
rotate 13 character
A - Z
25
Key = 13 always
J = 12 mod 26
Letter(26) + space + digits(0-9) + dot
J+13
(a+k)%.38
```

## Page 12
#### Classic ciphers
```text
13/26
Cryptography
Classic ciphers
Substitutional
Transposition
L) Caesar cipher
L) Railfence
ROT13
Affine cipher
L) Columnar transpositional cipher
vigenere cipher
if K not defined
E(x) = x + K % 26
K = 3
Crypt analysis
condition for a, b
breaking of cipher
if a,b unknown
a -> cannot be 13 or even no
a, b between 0-26
Ex = ax+b % 26
coprime of 26
a
GCD(a,b) = 1
formula
e.g 3,7
17, 20
E = ax+b % 26
Divisors 1,3
1,7
and
Comm 1
E = (ax+b) % 26
(17 x 16 + 20) % 26
GCD
1
don't put a = even no
```

## Page 13
### Affine Cipher
#### Vigenere cipher
```text
Affine
(n-b)
a
-> add b to result for Final Cyphertext
AFFINE CIPHER
(n-b)
a
26
PT = TWENTY
Q)
a=17, b=20
string
E(x) = (ax+b)%26
find enc string
or
a cant be
even
Ans)
T=19 so
(17(19)+20)%26 =
5 = f
and ≠ 13
condition for
a
Decryption
• must be
D(x) = a^-1 (x-b)
coprime
minus b
gcd = 1
multiply x a^-1
a^-1 doesn't exist
a^-1 . a mod 26 = 1
2. b must
case I
given
be integer
Hit trial for a^-1 calculation
case II
a^-1 not given
(a^-1 . a) mod 26 = 1
(a . 17)%.26 = 1
Vigenère
(17.17)%.26 = 3 X
} Hit and Run
(23.17)%.26 = 1 ✓
Vigenere cipher
L introduced character Key
eg PT = HELLO
Key = XYZ
Poly
H
E
position of plain text
X
X
Y
Z
E(x) = PT+K/26
D(x) = (T-K/26)
if short
Ci = (Pi + Ki) mod m
if longer
Pi = (Ci - Ki) mod m
restart
key cut it
```

## Page 14
#### Railfence
```text
plaintext
A
B
C
D
H
A
B
Key
C
D
E
Y
Z
E
Railfence
Jump over the River
depth=2
M
T
E
J
O
E
E
P
V
R
H
R
V
R
First row
CT= J M O E T E I E U P V R H R V R
depth=3
E
U
O
P
R
M
V
```

## Page 15
#### Columnar Transpositional
```text
Columnar Transpositional
PT= JUMP over the River
K = secret
column = key
number of c
18
4
2
19
S
E
C
R
E
T
row flexib
J
U
M
P
O
V
E
R
H
E
R
R
G
G
garbage, buffer
smallest c=2
CT = QIMFE URV OE G PH
Q1)
Find a^-1 if a=5
so 5.a^-1 %.26 = 1  so solve 5.x = 1 %.26
divide and take remainder
Use extended euclidean Algo
26 = (5x5)+1
• Divide 26 by 5
1 = 26-(5x5)
• rearrange to express 1
1 = 26+(-5)(5)
• identify coefficient of 5 = -5
-5 mod 26 = 21
• verify 5.21 %.26 = 1
```

## Page 16
```text
• In Decryption Cypher
P = a^-1 (C-b) mod m
26
if space exist = 28
Negative Number
if
C-b = negative add m till positive
so C-b = 2-8 = -6 +26 = 20
a=3, b=7 find a^-1
Q1)
a^-1 . a %.26 = 1
a^-1 . 3 %.26 = 1
value/26 } remainder must be 1
a^-1 . 3 = 27
so
27 = 1
so
a^-1 = 9
26
Q2)
a=5, b=7 find a^-1
or it
a^-1 . 5 %.26 = 1
value
Rem
26
so 26x1=26, 26x2=52, 3=78,
so (5.x)
remainder = 1
104
5.x = 105
a^-1 = 21
```

## Page 17
### CryptoAnalysis
#### Frequency Analysis
```text
CryptoAnalysis
-> secret Key
-> Recover plain text
OTP
-> unconditionally secure
-> computationally secure: AES, RSA, ECC
, blockchain
reverse encryption
distributed system
AES
+ decentralised
all node
same data
51% blockchain
Cryptanalyser
1 for computation
L Attacks
algo - votes
Nonplaintext
attacks
eg guess key from known Algorithm
(2^81)
on
space
26+1+1 = 28 = 2^28 = 2^22
=> exhaustive key search
us
if
bits
keys
time
brute force
to guess
E
highest freq very
Frequency Analysis
L cypher text given
L count all letter
open character rule
high freq (B)
LOSS A BBB
replace with E,
highest freq
EEE
```

## Page 18
### DES
```text
follow Rules
vowels
th, ing, etc.
DES
data encryption standard
symmetric key block cypher
1970 Lucifer (block cypher)
-> NIST (NBU) 1977 DES
Budget of Datacom
-> 1990's Data crack ($250,000)
L Algo that broke Des
L so upgrade DES -> 3DES
LUCIFER = 128 bits
L shrink to 64 bits  NBU changed it
16 rounds involved
keysize -> 64 (shrink to 48 bits)
I/O 64 bits
initial permutation
Key
48 bits
expansion
Round 1
K1
Round 2
48 bits
K2
Round 16
Final Permutation
64 bit output
```

## Page 19
#### Round function
```text
Round
64 bits
32 bits
32 bit
32 bits
F(R bits, K)
32 bit
xor
64 bits
F(R bits,
Function
ki)
32 bits
32 bits
expansion
48 bits
XOR
48 bits
Compression
32 bits
```

## Page 20
### AES
#### AES128
```text
AES
-> 2001 by NIST
symmetric Key,
block cypher
(e&d 1key)
->
3 variants
AES256
AES128
AES192
10 Rounds
14 rounds
192 bits
256 bit
128 bit Keysize
12
AES128
Input block size = 128 bits = 16 bytes = 4 words -> 1 word = 4 bytes = 32 bits
Key size = 128 bits
key given by user
128 bits PlainText
128 bit remain keysize
K0
Key
expansion
Total Keys =
algorithm
Total Round + 1
Round 1
K1
Round 2
K2
Pre round Transformation
RN
128 bit CT
```

## Page 21
### AES (Input Array and Rounds)
```text
Input Array
PT = Hassaan
is a good boy
1. use hexadecimal value
K = Ammar
instead of letter from table
64 bit
doesnt agree
'also space', dot
key will be 16 bytes always
2- Make 4x4 table input block
if letter more
than 16 make
new block
1 byte
3- make 4x4 key block of key too
4- Make 4x4 state Array
W0 W1
W2
W3
S0,0
S0,1
S0,2
S0,3
S1,0
S1,1
S1,3
S1,2
S2,0
S2,1
S2,3
S3,0
S3,1
S3,3
eg Find 2nd byte of 3rd word = so W3
S1,3
S2,3
Add Round key
128 bit PT
State array (SA)
Substituted values from S-box
Table
Substitution-bytes
Key expansion
R1
Shift Row
Mix Columns
K1
Add Round Key
K0
K1
Total Keys = 10+1 = 11
LAST Round doesn't have Mix columns
Total words = 11x4 = 44
```

## Page 22
### Cryptography & PKI
#### Public Key Crypto
```text
Cryptography & PKI public key infrastructure
used in encryption, digital signatures, key exchange
secret key : used in symmetric encrypt
both used together in practice
each user
private
has his
own
public
public key certificate: binds identity to public given by CA (certificate authority)
PKI
manages key & certificates
CIA
Public Key Crypto
sender encrypts using receivers Public key (Confidentiality)
then sender encrypts using own Private key (integrity)
Receiver
decrypts using public & private key
Symmetric
Assym
key pair (public & private)
keys
single shared
out of band
in-band
Scalability
low
high
Bulk encryption
small data
security
confidentiality, Integrity
CIA authentic
```

## Page 23
### RSA
```text
assymetric
RSA rivest shamir Algo
Step
1-> p, q choose prime no such that p≠q
2-> n = p x q
3-> Φ(n) = (p-1)(q-1)
4-> choose e such that
1. 1<e<φ(n)
2. gcd(e, φ(n)) = 1
coprime no factors other than 1
5) compute d  (d x e) mod φ(n) = 1
or d x e % φn = remainder 1
public Key = {e,n}
private
{d,n}
Encryption :
C = p^e mod n
P = c^d mod n
De
Q1)
p=13  q=11
n = 13*11 = 143
φ(n) = 12*10 = 120
e =
GCD(2,120) = 2 x
e=7
(3,120) = 3 x
(4,120) = 4 x
(5,120)
= 5 x
(6,120)
= 6 x
7,120
= 1 ✓
(d x e) % 120 = 1
d x 7
(20*7) % 120
d=103
so public key = (7,143)
private (103,143)
```

## Page 24
### Diffie-Hellman
#### Find g if p given
```text
symmetric
Diffie-Hellman
not for encryption but to make key for shared encryption
assym RSA is strong but slow for bulk data
Symmetric (AES) fast but needs shared key
Diffie securely creates that shared key over an open channel
Step
1- Public Numbers (shared)
P = prime , generator g = primitive root of p
ensures
means
if p=7 so
3^1 % 7 = 3
3^2 % 7 = 2
1) R1 = g^x mod p
x = senders secret value
3^3 % 7 = 6
y = receivers secret value
3^4 % 7 = 4
changes
2) R1 sent to receiver
3) R2 = g^y mod p
4) R2 sent to sender
5) K = (R2)^x mod p at sender
6) K = (R1)^y mod p at rcv
7) shared secret key (K) = g^xy mod p
Find g if p given
1) p given (eg p=17)
prime
2) find prime factor of p-1, (1,2,4,8,16)
3) compute g^((p-1)/prime factors) mod p for every possible value of g
4) g range is given, g < p alway
5) stop when you get 1 in Ans
6) if don't get one then value of g is primitive root of p
```

## Page 25
#### RSA big numbers
```text
Q p=17 , find g  11<g<17
Prime factor = {2} -> single q
g^(16/2) mod p => g^8 % 17
for
g=12   12^8 % 17 = 16 -> primitive
g=13   = 1 -> not primitive
14   = 16 -> primitive
15   = 1 -> not
so G=12 (x=3, y=6)
R1 = 12^3 % 17 = 11
R2 = 12^6 % 17 = 2
K = 2^3 % 17 = 8
Shared key = 12^18 % 17
RSA big numbers
p=11, q=5
n=55
φ(n)=40
e=7
d=?
Use EEA (extended Euclidean algo) to solve e*d mod φ(n) = 1
Next page
```

## Page 26
#### Euclidean Algo
#### Back Substitution
```text
(d*e) % 40 = 1
Euclidean Algo
Division step
Remainder
Quotient q
remainder
40 = 7x5 + 5
7 = (5)x1 + 2
1
it 1 comes
2
go to
5 = 2x2 + 1
next step
Back Substitution
start with 1
start from 1
1 = 5 - 2(2)  expand substitute
make subject of
division eq
1 = 5 - 2(7-5)
expand prev Remainder
5 - 2(7 - (40 - 7x5))
with eq
so
1 = 3(40) - 17(7)
find no that multiplies with 7 small no
put
if negative then φ + (negative no) = Ans = d
```

## Page 27
#### Q2 RSA with EEA
```text
Q2) P=71, q=67, e=79    m=80, n=4757, φ(n)=4620
Find d  use EEA
Quotient
Re
move remainder below
Division step
4620 = 79(58) + 38
58
79 = 38 x 2 + 3
2
3
38 = 3x12 + 2
12
2
3 = 2x1 + 1
1
Back Sub
1 = 3 - 2x1
1 = 3 - (38 - 3x12) = 3 - 38 + 3x12
36
= 3(1+36) - 38
sub 3 = 79 - 38x2   so   1 = 3(79 - 38x2) - 2
1 = 3 - 2x1
sub 2 = 38 - 3x12   so
1 = 3 - (38 - 3x12)x1
1 = 3 - 38 + 3x12
1 = 3(20) - 38 + 3x12
sub 3 = 79 - 38x2
1 = -35 + (79 - 38x2) x 12
sub 38 = 4620 - 79(58) => 1 = -35 + (79 - (4620 - 79(58))x2)
```

## Page 28
```text
1 = 3 - 2x1
1 = 3 - (38 - 3x12)   subbed
3 x 13
1 = 3 - 38 + 3x12
so 3 + (3x12) - 38
1 = (13x3) - 38
1 = 13x(79 - 38x2) - 38   subbed
1 = 13x79 - 38x13x2 - 38
1 = 13x79 - 26x38 - 38 = 13x79 - 27x38
sub
1 = 13x79 - 27(4620 - 79x58)
-27(4620) + 27(79x58)
1 = 13x79 - 27x4620 + 27(79)(58)
-27(4620) + 13x79 + 1566x79
1 =
-27(4620) + 79(1579)
d
d = 1579
So encryption
So 79 x 1579 = 1 mod 4620
80^79 % 4757
Use exponential Table
calculation
value after mod 4757
80^1
80
80^2 = 6400
1643
80^4
1643^2 = 2699449
(1643x1643) = 2513
80^8
2513^2
2610
now square the remainder and than mode
80^16
2610^2
3756
80^32
3756^2
789
80^64
789^2 = 622521
622521 % ... = 1234
79 = 64+8+4+2+1  multiply residue & take % 4757
use CTR for decryption
chinese remainder theorem
2594^d = 1579
=> 2594^1579 % 4757
So Ans C = 2594
```

## Page 29
#### Diffie Hellman big
```text
2) Diffie Hellman big
p=97, g=5
a=36  b=58
A = g^a % p  use squaring Table
Value mod 97
5^1
5
5
5^2
5^2 = 25
25
5^4
25^2 = 625
625 % 97 = 43
5^8
43
5^16
5^32
1296
35
5^64
A = g^a % 97
= 5^36 % 97
36 = 32+4
(35 x 43) % 97 =
58 = 32+16+8+2
B = 5^58 % 97
58 = 35 x 36 x 6 x 25  12600 % 97 x 6 x 25
```

## Page 30
### AES example
```text
Add
Sub
Shiftrow
Mix col
10 round
AES example
1) 4x4 word input matrix
or 8 hex
40 55 48 41 40
40
input matrix
40
55
48
41
key
49
30 30 30
49 32 32 31 30 30 30 30
49
30
30
32
30
30
30
30
32
30
30
bitwise XOR
55
48
41
XOR
40
0100 0000
0100 1001
1001
Same = 0
50
0000 1001
so result = 9
09
```

## Page 31
### Cryptographic Standards
```text
2nd, 9am
Cryptographic Standards
Stages
1- Initial Negation
(CIA)
Sender
P
Hashing
P + hash
P + Hash
2) Authentication stage
encrypt -> C ---- send ---> C
C
3) Keying stage  verify if hash same message (I) integrity
Receiver
Sender
P hashing
P + Hash
Private key (sender)
P + Hash
decrypt (public
P + Signature
Decrypt (receiver private key)
send
C
1- Digital signature
2- HMACS
verified by sender public key
less computation
no repudiation
```

## Page 32
#### Verification of D-Signature
#### No repudiation
```text
Check CA signature - by using CA's public key
check valid period
check for revocation
sender cant deny he sent msg
D-signature provide Non repudiation as public key
Hash does not
Digital signature
Authentication
I
key
Non repudiation = sender cant deny sending msg
How works
1. Hash message
2- Encrypt Hash with Private key making it Signature
3- Send message + Signature
4- verify Signature
decrypt using public
matches Hash
HMAC (key Hashed msg authentication codes)
use symmetric key (only Private)
Doesnt provide nonrepudiation
as both parties share secret key
sender can claim msg forged
```

## Page 33
### Access Control
#### Protection
#### Authentication method
```text
Final
Access Control
access modes = read write append execute delete create search
access control = policy driven limitation of access to system & data both physical & logical
Protection
identification (1:N)
compare with entire DB
Identification
"who are you"
uniquely identify user
verification (1:1)
Authentication
"Are you this person"
verify identity
password / biometric card
Authorization
permission on roles
Auditing
logs of access activity
Accountability
hold user responsible for action
Non Repudiation
prevent denial of action by user
by logs, authenticity, D.S
Authentication method
credentials based on what you know, have, are, do
Password
one time P (OTP)
vulnerable
to social eng!
Reusable
Policies : complexity, duration, uniqueness
```

## Page 34
#### Access cards & Token
#### Biometric
#### Multifactor Auth
#### Authorization models
```text
Access cards & Token
magnetic strips cards
USB Key/Rolling code generator
use RFID (radio freq id) for proximity access
loss/theft address by cancellation
Biometric
finger, iris, face
error rate : Accuracy when user not trying to deceive
Deception rate : likelyhood of deception
error rates:
FAR (false acceptance rate)
Performance Analysis
FRR (false rejection rate)
FTE (failure to enroll)
Multifactor Auth
2> auth e.g Code + Pin
Vulnerable to Trojan House, MiTM
Authorization models
Individual Access control :- user permission based
by system
Role based Access control :- role based
Alice has/owns
Mandatory access control (MAC) :- Strict, centrally controlled, system defined
File1 is top secret - confid
Discretionary all (DAC) :- flexible, owner enforced
Multilevel / security
Alice make file F1
e.g
owner
Alice gives Bob read permission for F1 of
can remove it
Access matrix
File1   F2   F3
R/W
own/read
- Alice can read, write on File1
Alice
Read
Joe
R/W
own/read
Trump
R
```

## Page 35
#### Access control structure
### Network Security
#### Security controls
#### Threats
#### Denial of Service (DOS)
```text
Access control structure
ACL (access control list)   eg
Trump
Joe
Biden
File 1 ->
own
W
R
Network Security
Set of rules/tech for CIA triad
Security controls
Firewall
: Filter traffic
Network Segmentation
: Isolate Network section to limit breach impact
Access control
: Trust none / verify everyone
Remote Access VPN (SSL VPN)
: Secure Remote connection
email security
Data Loss Prevention
Intrusion Detection
Sandboxing
: Test sus files in a environment
cloud Network security
: Protect cloud resources
Threats :
Denial of service (DOS)
Goal: overwhelm network/ syst to make unavailable
How : Flood Target with traffic, consume resources,
Impact : disrupt service, reputation, etc
Targets : web servers, DNS servers, Email servers, Network Bandwidth, Application
servers
```

## Page 36
#### DDoS
#### Botnet
#### Categories of DDoS/DoS
```text
Distributed
compromised
DDoS
what: DOS from multiple systems
coordinated via
Botnet
Harder to mitigate as distributed resources
BOTNET
network of infected computers (bots/zombies) controlled by a attacker (botmaster)
used for:
DDoS, Spamming, Traffic sniffing, Keylogging, spread Malware
Ad fraud, ID theft..
Botnet creation -> malware infection
Device becomes part of Botnet
Awaits commands
Botnet ecosystem
attacker buys/develops botnet from market
central server sends commands to bots
Botnet consists of
Trojan command
to create malware
& control centre
to send int
to bots
Volumetric attack
Protocol Attack
Application layer Attack
consume bandwidth of target network
consume other types of resources like
consume resources of application
flood attacks, bits per second
eg connection state table
eg load balances, firewalls
request per sec
techniques
packet per second
UDP flood
Techniques
Techniques
SYN flood
HTTP Get/Post
ICMP flood
fragmentation attack
Ping of death
Pulse wave
Slowloris attack
```

## Page 37
#### UDP Flood
#### ICMP Flood
#### Ping of Death
#### Smurf Attack
```text
attacker sends spoofed UDP packets high size
UDP packet
to random Host port
flooding causes server to check for nonexistent
applications at port
legit application say "error reply"
ICMP
but icmp "Destination unreachable".
error
packet
destination
unreachable
ICMP flood
ICMP usually used to IP troubleshooting
echo req
ICMP flood = send icmp echo req large amount
overwhelm victim, normal req not catered
echo reply
To prevent : set threshold limit
Ping of Death
sends oversized packets using ping command
ore.g 65mb which is over limit = crash
Smurf Attack
Attacker spoofs source IP address with victims IP & send large
ICMP echo req to IP broadcast Network
```

## Page 38
#### SYN Flood
#### Countermeasures of DDoS
#### Mitigation
#### Prevention
```text
3 way handshake
SYN Flood
attacker sends lots SYN req with false IP source to victim
victim send back SYN/ACK but for & waits for ACK but doesn't get ACK
as false IP source
for 75 seconds listen queue
Countermeasures of DDOS
1- Absorb : use Additional capacity
but requires planning & additional resources
2- Degrade service : stop non critical & maintain critical services
3- Shut Down service : shut down all services attacked
Mitigation
1- Load balancing - increase bandwidth of critical servers
- Replicate servers
- balance load on each server
2- Throttling - set router to access server with logic to throttle incoming traffic
to be safe
- filter legitimate traffic
3- Dropping - servers & routers drop packets when load increases
- cause request to solve captcha before continuing
Prevention
consumes memory & computing
1- Egress filtering : scans headers of packets to filter malicious traffic
2- Ingress filter : prevents source address spoofing
3- TCP intercept : features in routers protect TCP servers from SYN flood
4- Rate limiting : control rate of outbound or inbound traffic
```

## Page 39
#### ARP spoofing
```text
ARP spoofing
address resolution protocol protocol used for resolving IP address to MAC address
ARP packets can be forged
to send data to attacker
- ARP spoofing = making forged ARP req, reply packet to overload switch
- switch is in forwarding mode after ARP table flooded with spoofed ARP table
attackers can sniff all the network packet
ARP poisoning = corrupting ARP tables with false IP mapping
o Attacker tells victim "I am router"
result both send their traffic to attacker
o Attacker tell router "I am victim"
(MITM)
attacks
```

## Page 40
### SQL injections
#### Types of sqli
#### Union Based
#### Blind SQL
#### Boolean Based
```text
SQL injections
malicious sql code ran into queries
75% web attacks are sqli
Normal input: 1221013 => select user where id = '1221013' and password = '...'
malicious : '; -- => select user where id = ''; --
Attack variations
end of line comment : -- , /* , #
piggy backed queries : chaining second command using semicolon => ; DROP TABLE USER
union based
Flags
Types of sqli
1) Union Based
purpose: extract data from tables
note: no of columns must match
code
$sql = "select name from products where category = '$cat'";
injection:
into cat variable
=> ' UNION select username, pass from users --
2) Blind SQL
web
server doesn't display Data or sql error on screen, attacker must ask database
"true/false" questions & observe how website reacts
A) Boolean Based
ask database T/F questions - if true = page loads normally
if false = page shows error
injection => ' AND substring(
(select pass from users where username = 'admin'),1,1) = 'a' --
code:
Select * From users where username = '$input'
```

## Page 41
#### Time Based SQL Injection
#### Error Based SQL Injection
#### Second Order SQL Injection
```text
close
AND SUBSTRING(value, position, length)
extracts 1 character
of string
(AND SUBSTRING( 'select pass from user where username = 'admin' ') = 'a'; --
returns password eg apple123
if true
page loads as
if false
attacker knows
2 B) Time Based
page returns
first letter='a'
normal
L if delay = condition true
else false
'; IF(1=1) WAIT FOR DELAY '0:0:30'; --
injection e.g
inject into $input
eg select * from product where ID = '$input'
write condition you want to confirm here eg
(AND
SUBSTRING...
2c) Error Based
L Trigger sql error to extract info
injection =>
(AND (select case when (1=1) then 1/0 else ('a') END) = 'a')
runtime
explanation : case
error
when condition then result
else result2
END
Second Order SQL inject
L malicious input stored in DB, later retrieved & executed in different context
vulnerable sites can be found by Google Dorking
```

## Page 42
### Technique for Advance Injections
#### Countermeasures
```text
Technique for Advance injections
-> Comment Variable
-> --
-> /*
*/
-> #
-> %00
Null byte terminating: in some older system it terminates strings early
-> Encoding Techniques
* Hex encoding ; some databases decode hex so write text in values
* Char() function
; creates chars using ascii value
* URL Encoding
Countermeasures
- Parameterized query
- Input validation
* white listing ( only alphanumeric values)
* Blacklisting
(remove risky characters ' -- *
- escaping characters
L use functions like mysql_real_escape_string() to neutralize ' or ;
Secondary Defense
L limit DB user permissions
Encrypt
blacklist
but Names like Peter O'Connor
```

## Page 43
### HTTPs
#### Security Goals
#### Interaction with Webservers
#### HTTP Request
```text
HTTPs
L hypertext transfer protocol ; an application layer protocol used to exchange data b/w client & server
request
client
server
messaging model
response
* Statelessness
L HTTP stateless = no way of recognizing same client from prev session
user would have to log in each page reload.
* Default port = 80
* Security Goals
Integrity: site A must not be able to use user session on site B
Confidentiality: site A must not steal info of user.
* Interaction with webservers
Resources on server identified by URL ( fast.edu/home.html )
Protocol : http, https, ftp, tor
Hostname / server : This is translated into IP address by DNS
Path to Resource : can be static / Dynamic
* HTTP request
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent : Mozilla /5.0
info of browser
tells type of current
client/service
Accept : text/html
Cookie : sessionid : abc 12   Connection: keep-alive - reuse TCP
stored session data
methods
data sent in URL
GET
; retrieve data
can be cached, bookmarked, remains in history, never use for sensitive
info
POST
; upload data to resource, DATA sent in msg body not URL
No cache, bookmark, no length data restrictions
PUT, DELETE, HEAD, OPTIONS
```

## Page 44
#### HTTP Response
### HTTPSecure
#### SSL/TLS Handshake
#### Web Security Threats & Defenses
```text
HTTP response
status code
2xx = success
3xx = redirection
HTTP/1.1 200 OK
4xx = client error   5xx = server error
Content-Type : text/html
Content-length : 1234
Set-cookie : session = xyz; secure ; HTTPonly
<html> ...... </ >
HTTPSecure
HTTP + SSL/TLS encryption
default port = 443   Provides : encryption
C
I   cant modify
A  Authentication   verify server identity
SSL/TLS Handshake
client sends 'ClientHello' with supported cipher suit
server responds with 'serverHello' certificate & public key
client verifies certificate, generates session key
encrypted communication begins
Web security Threats & Defenses
1) Downgrade Attack
Force protocol to use weaker encryption   Defense : Disable old TLS versions
2) mixed content
HTTPS page loads HTTP resource
browser blocks about insecure content   Defense : use HTTPS resource only
```

## Page 45
#### SSL Strip Attacks
#### Certificate Issue
### Cookies
```text
SSL strip Attacks
L MITM strips HTTPs -> HTTP
Defense : HSTS ( HTTP strict Transport security)
Certificate Issue
self signed certificates
Expired
Wrong domain
Defense : never bypass certificate warnings.
Cookies
as HTTP stateless
Cookies: small piece of info/data stored in browser sent auto with request by
matching Domain
"example.com"
Attributes:-
Domain document.cookie = "name = value; domain= ^
path=/dashboard
Path document.cookie:
- Expiration Date
- Secure Flag  eg set-cookie : sessionid=xyz; secure
- HTTPonly flag
; HTTPonly
Prevent Cross site cookie sending
- Samesite Attribute
How work
3 values -> strict, Lax, None
ex Client -> server: Get / login
server -> Client : set cookie : session id= abc123 ; HTTPonly
client -> server : Get/profile (cookie : sessionid=abc123)
Types
```

## Page 46
#### Types
#### Security Issues
#### Browser Fingerprinting
```text
* Types
Session cookie : Temporary, deleted when browser closes
- No expiry   Persistent : expiry eg Set-cookie id=abc; Expires: Wed 21, Oct 2025, 07:28:00 GMT
First Party : same domain as website
Third Party : from diff domain (ads etc)
modern Browsers block 3rd Party by default
* Security Issues
- Cookie Theft
L session hijacking
by
Network sniffing
XSS Attack
Physical Access to device
- Session Fixation
L Attackers set users session ID
L defense : regenerate ID every time
- Cross Site Request Forgery (CSRF)
L unauthorized command by trusted user
L can be prevented by samesite cookie
* Browser Fingerprinting
L Alternate to cookie
L collect browser characteristics
User Agent, Screen Resolution, OS
Installed Font, Plugins
Timezone, Language
Hardware e.g CPU, RAM, GPU
Behavioral - mouse mov, scroll, type rhythm
audio
Dangerous   Hard to detect, block, work in incognito
by tracking + delivering advertising
Defense: L TOR Brave
```

## Page 47
### CSRF
```text
CSRF
L cross site req forgery
How work?
browser stores
1-> User logs in to 'bank.com'
get session cookie
2->
User (victim) visits malicious site 'attackersite.com'
3-> malicious site sends contains hidden request to 'bank.com'
4- Browser auto sends request with user cookie
5- Bank process it req as legit user action
(iframe)
Google.com
* HTML iframes allow 1 website to embed inside another
but cross iframe communication not possible due to
bing.com
same origin Policy
security feature makes sure attacker website cant be
req to websites & read data if conditions dont match
conditions
so evil site cant read
- same domain
cookies or responses
give
google
from a legit site
me info X
attacker.com
but browser?
- same protocol
auto attaches
cookie with
e.g
http:// google.com:80
req
http:// attack.com: 80
port
protocol
domain
Detail working
X
legit money transfer req to server
The evil site:
Vulnerability
L The bank server
page contains a form that auto submits
POST /transfer HTTP/1.1
Host: bank.com
the form request came bank server
L uses cookie for authentication
and Browser attaches cookie stored
Doesn't verify where req
so: POST /transfer HTTP/1.1
cookie: session = ABC123
came from
to = alice &amount=1000$
Host: bank.com
Doesn't use CSRF token
cookie: sessionID = ABC123
```

## Page 48
#### Defense
#### STP (Synchronizer Token Pattern)
#### Double Submit Cookie Pattern
```text
Defense
STP
transfer
CSRF token
e.g
L when loading transfer page server includes token unique in the loaded HTML
<input type= hidden name = csrf-token value = "RANDOM123"> e.g
In the req HTML req CSRF token also sent :
POST /transfer   server matches token
cookie : s ...
to= alice &amount =1000 & csrf-token = RANDOM123
Samesite cookies
L browser doesn't send cookie on cross site req (browser based defense)
3 values - Strict (never)
L Lax ( send with top level navigation GET req)
None
e.g
set-cookie : sessionid=abc123 ; samesite=Strict
Referer / Origin Header Validation
check prev page URL
check Source domain
Limitation:
L Header can be spoofed/ommitted
L Privacy concerns
* STP (synchronizer Token Pattern)
L Secret also called secret token
L Most effective
if it is CSRF token
Double submit cookie Pattern
L Variation of STP without server side storage
L How work?
CSRF
- set random token as cookie
server receives csrf token in the cookie & matches
it with the csrf in the form
verify cookie token = form token
Header
```

## Page 49
### XSS
#### Reflected XSS
#### Stored XSS
```text
XSS
L cross site scripting
JS code into inputs
can steal cookie
change HTML, event
Types
1- Reflected XSS (Nonpersistent/nonstored)
e.g
legit
Hello user
Hello
Hello
Enter name:
Mustafa
GET /?name= input
<h1> Hello Mustafa </h1>
Server
injection : <script> alert(1337) </script>
<h1> Hello <script>alert(1337)</script> </h1>
alert 1337
hello user
Server
2) Stored
L input stored in DB, dangerous, showed to all users you read
e.g Youtube comment section
1- Attack comments "<script> alert ("Attack is here") </script>"
this get stored in DB
2- victims visits comment, loaded from DB
result.
```

## Page 50
#### DOM XSS
#### Defense
```text
* DOM XSS
L clientside JS processes unstructured data unsafely
L No server involvement
L entire attack on browser
Defense
XSS maybe
HTML tags
Input Validation
whitelist
event handler
L only alpha numeric
Javascript protocol
Blacklist
L HTML purification
Output Encoding
prevent script to run when displaying user input
sent from legit website
encode special chars before showing them
exploit trust client browser has from
e.g < becomes &lt
from
CSP Content security Policy
modern defense to control what you can run on site
sent from other evil website
implemented via HTTP header
exploit trust of server of data
cookie
rules / Directives include
sent from the browser(client)
default-src : allowed for all resources
script-src
; allowed script sources
Style-src
img-src
connect-src
frame-src
; allowed iframe
report-uri
; url sent if violation report
example:
content-security-Policy:
default-src 'self'; script-src 'self'; object-src 'none';
=> allows scripts
& content from
own site
HTTP only cookies
L Prevent javascript from stealing Cookie
Set-cookie : sessionid= ABC123 ; HTTPonly; secure
only HTTPS
Input length limits
L username <20 char
Regular expression Filtering e.g <script>
```

## Page 51
### Cryptography
#### Types
```text
Cryptography
L protecting info from unauthorized
Confidential
Integrity
Authentication
Freshness : expires if time
Non Repudiation : sender cant deny sending ( Digital Signature)
Types
- Symmetric crypto (Private key)
Same key for encryption decryption   Fast efficient for large Data
cons: if key leaks X
AES, Des , (Modern)
classic
- substitutional ceasar cipher (3:key), Rot13(13), Affine, Vigenere   - transpositional railfence, Columnar Trans
- Asymmetric (Public key)   1 Public + 1 Private
solves key distribution problem   Slower
RSA, DH , Digital Signature
hashing
HASHING
L oneway process / irreversible
L eg Hash a value, if value changes hash changes = Integrity
SHA
```

## Page 52
#### Affine Cipher
```text
Classic
L Substitutional
Affine Cipher (monoalphabetic)
A -> 0   Z -> 26
1. multiply
+ Add into plaintext
=> encryption : E(x) = (ax+b) % 26
L or total no of alphas
* a, b are given
* a & m are co prime (GCD = 1)
So that
the modulo inverse
of a exists
Whats GCD?
Ans) largest no that divides two numbers exactly
eg GCD(8,12) = 4
so GCD(a, 26) = 1
L if a = 1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25
all even
nos
2 get them
divides 26
P(x) = (a^-1 . (E - b)) % 26
=>
Decryption :
L First '-b'
L multiply by a^-1 - To find a^-1
a . a^-1 % 26 = 1
find using Hit & trial
Q1 find a^-1 to decrypt ZEBBW if
a = 7, b = 2.
1) (ZEBBW - 2) =
->
(a^-1 . 7) % 26 = 1
L if a^-1 = 4 then (.7) mod 26 = 2 X
so a^-1 = 11
2) (a^-1 . a) % 26 = 1
3) ..
a^-1 = 7
= 4 X
a^-1 = 11
= 1
a^-1 = 14
= 6 X
```

## Page 53
#### Vigenere Cipher
#### Transposition
```text
Vigenere Cipher (polyalphabetic)
L uses keyword to shift encrypt PT, add keyword to it
encryption: Ci = ( Pi + Ki) % 26
eg P = Hello, Key = xyz
so
H E L L O
+
x
y z x y
repeat if short
Subtract for decryption => Pi = (Ci - Ki + 26) % 26
to avoid
negative
no
Transposition
L Railfence
L plaintext written on diagonals
eg P = INFORMATION, Key/depth = 2
so
R1
R2
cipher = IFRAIN NOMTO
R1
R2
* Issues
L first & last letter remain same
L Key just a no that divides total length
L Columnar Transposition cipher
L Key is word
(2)
(1) (4)
(3)
L Key in alphabetic order
N
R
M
blank replaced by _, letter not placed if key letter repeats
A
T
N
Key = secret
e.g
Cipher = FI NT KORN
```

## Page 54
### Cryptanalysis
### DES
```text
Cryptanalysis
L breaking ciphers
* Types of Attack
L Ciphertext only
Known PT
Chosen PT
Brute Force
L try all combo
Frequency Analysis
L A known table of frequency % of all letter
L some letter appear more e.g vowels 'e'
DES data encryption standard
symmetric (1 private key)   works on fixed size of Plaintext (64 bits)
Keysize = 64 bits, 8 bits are parity, 56 effective
No of Round = 16
* High level steps
1) Initial Permutation (IP)
L 64 bit PT permutated according to Fixed table
2) Split into left & right halves   L after IP split in Left(L0), Right(R0) block, each =32bits
3) 16 Feistel Rounds
for each round i=1 to 16
1. Expand 32 bit(R) to 48 bits using expansion table
2. mix with round Key: XOR expanded R with a 48 bit sub key Ki
3. Substitute using S boxes (8 boxes each converts 6 bits -> 4 bits)
4. Permute result with P-box
5. XOR output with Left (L)
6. Swap halves L<->R
7. After 16 rounds swap last time
```

## Page 55
#### Key Schedule
#### Decryption
```text
4) Final Permutation (IP^-1)
* reverse of initial permutation
* produces the final 64 bit ciphertext
Key schedule
L 16 subkey (Ki) rounds from original 56 bit key
each round key is generated by left-shifting halves of key & permuting
(PC-2 table)
Decryption   Total Table
L reverse
- PC1
- PC2
- Expansion table
- Substitution Table
Aes skipped
```

## Page 56
```text
```
