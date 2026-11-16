# Information Security Notes (Bilal) (transcription)

Auto-transcribed from `bilal_Info Sec Notes Complete compressed.pdf` (OCR + AI correction). Diagrams/tables are approximate.

## Page 1
### Chap # 1: Introduction to Information Security
#### Information Security
#### Objectives (CIA Triad)
#### Security v/s Convenience Trade Off
```text
Chap # 1 :- Introduction to Information Security
Tuesday
19/08/2025
Lec 1: Introduction to Information Security
Muhammad Bilal Khawar
22i-0786-G
Information Security
→ Protecting data in digital format
→ Securing data during storage, transmission, and processing
→ Blocking unauthorised access.
→ Weak Info Sec leads to breach of sensitive data resulting in a
compromised confidentiality
→ Web App Vulnerabilities can devastate global companies
→ SQL Injection is still a threat to security.
Objectives (CIA Triad)
→ Confidentiality (prevent unauthorized disclosure of info)
→ Integrity
(maintain accuracy, consistency, trustworthiness of data)
→ Availability (ensure reliable and timely access to info and resources)
Security v/s Convenience Trade Off
Convenience
Security
```

## Page 2
#### Challenges while securing Info
#### Summary
```text
Challenges while securing Info
* Personal Security (protecting individuals from physical/digital threat)
* Information Security (protecting electronic data of organizations)
→ No single universal solution
→ Wide variety of attacks
→ Defenses can be difficult
* Bot → Infected Device
* BOTNET → Network of Bots
Summary
* Info Sec is essential
* Real World Breaches
* CIA Triad
* Modern Challenges (IoT, AI risks)
* Security is a serious problem.
```

## Page 3
#### Example of Classic Data Breach
#### Phishing Attack
#### Three types of Information Security (CIA)
```text
21/08/2025
Example of Classic Data Breach
* Email recieved via phishing
* You provide data but it goes to malicious site instead of intended site
Phishing Attack
Prevention
→ detect phishing URLs & mark as spam
→ train employees to detect phishing.
→ encrypt files
Detection
→ identify that sensitive data has been accessed from off-site.
Response
→ Change password
→ Notify CTO
Three types of Information Security (CIA)
Integrity
→ Events leading to integrity breaches:
• accidentally deleting files
• entering invalid data/altering configurations
→ Countermeasures:
• Hashing
• Transmission Cyclic Redundancy Check (CRC)
• Config Mgmt
• Access Control
```

## Page 4
#### Protections to Secure Info
#### Terminologies
```text
Availability
→ Uninterrupted Access
→ Countermeasures:
• Load Balancing
• Software Backup
Protections to Secure Info
→ Identification (Who are you)
→ Authentication (Prove it)
→ Authorization (What can you do)
→ Auditing (Track Actions)
→ Accounting (Record Usage)
Terminologies
→ Asset :- Item of Value
→ Threat :- Actions/Events that have potential harms
→ Threat Agent :- Person/Element with power to carry out threat.
→ Vulnerability :- Flaw/Weakness that allows threat agent to bypass security
→ Threat Likelihood :- Likelihood that threat agent will exploit vulnerability
→ Risk :- A situation that involves exposure to some type of danger.
→ Countermeasures :- Measures taken to avoid/counter threats
* Assets are valuable
* Threat agents can create threats
* Threat leads to risk
* Countermeasures are taken to reduce risks.
```

## Page 5
#### Risk Mitigation Strategies
#### Mitigation Stages
#### 3 Options if you find Vulnerability
#### Why Organizations Care
```text
Risk Mitigation Strategies
→ Risk Avoidance (identify risk but not engage in activity) (not to keep valuable asset)
→ Acceptance
(accept that risk will come (ignore risk))
→ Risk Mitigation (attempt to address the risk by making it less serious)
→ Deterrance
(understanding the attacker and then informing him of consequences of his actions)
→ Transferance
(transfering the risk to a third party)
Mitigation Stages
→ Prevention (stop threat before it harms)
→ Detection (identify when a threat is active. Act accordingly)
→ Response (act to reduce damage)
3 Options if you find Vulnerability :-
1) Bug Bounty
(tell bug to company for the bounty)
2) Zero-day Broker (sell bug to people who sell it forward)
3) Black Market
(sell bug directly on dark web)
Why Organizations Care
Attackers
→ Hacker
→ Insiders
1) Preventing Data Theft
→ Black Hat Hacker → Cyberterrorists
→ White Hat Hacker → Hacktivists
2) " Identity "
3) Avoiding Legal Consequences
→ Gray Hat Hacker
→ State-sponsored
4) Maintaining Productivity.
attackers
→ Cyber Criminal
→ Script Kiddies
→ Brokers
```

## Page 6
#### Advanced Persistent Threat (APT)
#### Cyber Kill Chain - Stages of Attack
```text
2/9/2025
Tuesday
Advanced Persistent Threat (APT)
* Long-term, stealthy, sophisticated attacks
* Usually state sponsored/organized groups
* Target :- High Value Organizations
* Aim :- Data Theft, Disruption, Espionage
* Advanced → Unknown zero day attack that has malware payloads
* Persistent → It doesn't stop
* Threat → Sophisticated, difficult-to-detect threats are launched at targets
Examples → Stuxnet, RSA Attack
Cyber Kill Chain - Stages of Attack
1) Reconnaissance → Attacker researches/identifies targets
2) Weaponization → Coupling an exploit with a malicious payload
3) Delivery
→ Transmitting the weapon to the target
4) Exploitation → The code is executed, exploiting a vulnerability at victim's system
5) Installation → Malware is installed to establish a foothold in the network.
6) Command & Control (C2) → The malware establishes a connection for remote control.
7) Actions on Objectives → Attacker achieves their goal.
```

## Page 7
#### Defense Principles
```text
Defense Principles
1) Layering (Defense in Depth) → Use multiple, layered security controls so if one fails,
other remains
2) Limiting (Least Privilege) → Restrict user and system access rights to the minimum
necessary to perform a task
→ Use security products from different vendors to avoid
3) Diversity
a single point of failure
4) Obscurity
→ Hide internal system details to make
reconnaissance harder
5) Simplicity
→ Keep systems and security rules simple to manage
and understand, reducing the attack surface.
* In short, effective defense is Multiple, Minimal, Varied, Hidden, and
Simple.
```

## Page 8
### Chap # 2: Malware & Social Engineering
#### Malware Fundamentals
#### How Malware Spreads
```text
Chap # 2 :- Malware & Social Engineering
Thursday
4/9/2025
Malware Fundamentals
* Malicious software that installs without consent to damage systems.
Key Traits
* Unauthorized :- Installs/runs without user consent
* Persistence :- Maintains long-term access
Impacts
* Data Theft :- Confidentiality breached (info stolen)
* Disruption :- Integrity breached (system crash / file deleted)
* Financial Loss :- Availability breached (cost from ransom etc.)
Layering
* Most effective principle against malware
* Defense in Depth
* Prevent a single point of failure
How Malware Spreads
* Infected USB Drives :- Uses autorun feature or infected files
* Malicious Downloads :- Bundled with pirated software/fake update prompts
* Network Propagation (Worms) :- Self-replicating malware that exploits network vulnerabilities
How malware works
→ enters through vectors (email attachments, USB, downloads)
→ begins when user executes the file / vulnerability is exploited.
```

## Page 9
#### Malware v/s Virus
#### Virus Infection Methods
#### A Working Malware
#### Types of Malware
```text
Malware v/s Virus
* Malware :- An overarching term for all malicious softwares
* Virus :- A type of malware that attaches to file/program & requires
user action to spread
* Not all malware is virus, but all virus is malware
Virus Infection Methods
* Overwriting (changes size) :- File size increases, may not run.
* Overwriting (same size) :- Replaces code, loses functions.
* Random Overwriter :- Overwrites random parts, causes to crash.
* Appender Infection :- Attaches at end, runs with program.
A Working Malware
1) Entry/Infection :- Malicious software enters system via vectors.
2) Concealment :- Hides using rootkits, obfuscation, or split infection to
avoid detection.
3) Payload Execution :- Delivers the harmful action.
* Rootkits → modify OS to mask malicious files/processes.
* Obscuring → encrypt/scramble code to evade scanners.
Types of Malware
1) Virus
→ Malicious code that attaches programs/files
→ Require User Action to spread
→ Can delete, corrupt, or steal data.
```

## Page 10
#### Social Engineering
```text
2) Worm
→ Malware that replicates without user action.
→ Spreads through networks by exploiting vulnerabilities
→ Can consume resources/deliver payloads
3) Trojan
→ Disguised as legitimate software
→ User installs it, believing it safe.
→ Opens backdoor or steals data
4) Ransomware
→ Encrypts user files/locks system access
→ Demands payment to restore access.
→ Very costly to individuals & organizations
5) Spyware/Adware
→ Spyware secretly monitors user activity
→ Adware displays unwanted ads, tracks online behavior.
→ Both degrade performance & compromises privacy
6) Rootkits/Logic Bombs
→ Rootkits hide malware by altering OS functions
→ Logic Bombs are malicious codes triggered by specific events
→ Both are difficult to detect & dangerous.
Social Engineering
1) Phishing
→ Trick users to reveal sensitive info via fake emails/website.
```

## Page 11
```text
→ Spear Phishing targets specific individuals
→ Whaling aims at executives
→ Vishing is voice based scam.
→ Goal is to steal data or deliver malware.
2) Spam
→ Unsolicited bulk messages sent to many users
→ Spreads malware, advertises, promotes scams
3) Typo-Squatting
→ Fake domains with minor typos in famous URLs.
→ Tricks users to visiting malicious sites.
4) Tailgating
→ Physically following someone into a secure area.
→ Aims to gain access to restricted areas.
5) Dumpster Diving
→ Searching trash for discarded sensitive data.
→ eg. Retrieve password in Trash
6) Sholder Surfing
→ Observing someone's screen, keyboard to steal data.
```

## Page 12
### Chap # 3: Cryptography
#### Symmetric Key Cryptography
#### Classical Ciphers
#### ROT-13
```text
Chap # 3:- Cryptography
18/9/2025
Thursday
Cryptography
* Discipline that embodies principles, means & methods for providing Information
Security (confidentiality, integrity, etc.)
* 3 Dimensions:-
1) Type of operations used for transforming plaintext to ciphertext
2) Number of keys used.
3) Way in which plaintext is processed.
Symmetric Key Cryptography
* Conventional Encryption / Single-Key Encryption.
* Key is shared between Sender & Reciever
Plain Text → Encryption Algo
Transmitted Cipher Text
→ Decryption Algo → Plain Text
Secret Key
Secret Key
Classical Ciphers (2 types)
1) Substitution Ciphers
i) ROT-13
* Each letter is substituted by the letter 13 positions ahead
of it. (a→n, b→o)
```

## Page 13
#### Ceaser Cipher
```text
* Encryption → c = (p+k) % 26
* Decryption → p = (c+k) % 26
* Value of k → 13
⇒ NUCES
letter
P value
a
0
AHPRF
b
1
2
c
→N(13)
(13+13) % 26 = 0 (A)
y
24
→U(20)
z
25
(20+13) % 26 = 7 (H)
→C(2)
(2+13) % 26 = 15 (P)
→E(4)
(4+13) % 26 = 17 (R)
→S(18)
(18+13) % 26 = 5 (F)
ii) Ceaser Cipher
* Each letter is substituted by the letter 3 positions ahead of
it. (a→d, b→e)
* Encryption → c = (p+k) % 26
* Decryption → p = (p-k) % 26
* Value of k → 3
⇒ NUCES
QXFHV
```

## Page 14
#### Affine Cipher
```text
→N(13)
(13+3) % 26 = 16 (Q)
→U(20)
(20+3) % 26 = 23 (X)
→C(2)
(2+3) % 26 = 5 (F)
→E(4)
(4+3) % 26 = 7 (H)
→S(18)
(18+3) % 26 = 21 (V)
iii) Affine Cipher
* Encryption → E(x) = (ax + b) % m
* Decryption → D(x) = a^-1 (x-b) % m
* a and b are given
* a and m should be co-prime (GCD should be 1)
* m is usually 26
* How to find a^-1 ?
→ Try all values from 1 to 26
→ Find a value such that:
(a.a^-1) % m = 1
⇒ ITS COOL with E(x) = (5x+8) % 26
WZU SAAL
→I(8)
(5x8+8) % 26 = 22 (W)
→T(19)
(5x19+8) % 26 = 25 (Z)
```

## Page 15
#### Simple Substitution Cipher
```text
→S(18)
(5x18+8) % 26 = 20 (U)
→C(2)
(5x2+8) % 26 = 18 (S)
→O(14)
(5x14+8) % 26 = 0 (A)
→L(11)
(5x11+8) % 26 = 11 (L)
⇒ Decrypt the encrypted string
a=5
* trying 21,
(5x21) % 26 = 1
* Find actual string by applying this formula
D(x) = 21(y-8) % 26
iv) Simple Substitution Cipher
* 2 types
a) Monoalphabetic Substitution Cipher
→ A simple mapping is followed for encryption/decryption.
→ eg. p: a b c d - -
F(k,p): q w e r - -
⇒ Plain Text :- dad
Cipher Text :- rqr
```

## Page 16
#### Vigenere Cipher
```text
b) Vigenere Cipher
→ Similar to Ceaser Cipher BUT value of k
is a list like [k1,k2, ---]
→ Encryption :- c = (p+k) % 26
→ Decryption :- p = (c-k) % 26
⇒ ABC with k = {3,4}
DFF
→A(0)
(0+3) % 26 = 3 (D)
→B(1)
(1+4) % 26 = 5 (F)
→C(2)
(2+3) % 26 = 5 (F)
⇒ Decrypt DFF with k = {3,4}
ABC
→D(3)
(3-3) % 26 = 0 (A)
→F(5)
(5-4) % 26 = 1 (B)
→F(5)
(5-3) % 26 = 2 (C)
```

## Page 17
#### Transpositional Cipher
```text
2) Transpositional Cipher
i) Railfence
* plaintext is written as a sequence of diagonals
* read off as a sequence of rows
⇒ INFORMATION with two level
R1  I  F  R  A  I  N
R2  N  O  M  T  O
cipher → IFRAINNOMTO
R1
R2
⇒ INFORMATION with three level
R1  I  R  I
R2  N  O  M  T  O
R3  F  A  N
cipher → IRINOMTOFAN
R1
R2
R3
* Issues with railfence :-
→ First & Last letter stay same
→ Key is just a number that divides total length
```

## Page 18
#### Columnar Transpositional Cipher
### Cryptanalysis
#### Types of Attacks
```text
ii) Columnar Transpositional Cipher
* Key is a word or phrase
* Key is in alphabetic order
* Blank is represented by 'X'
⇒ INFORMATION with Key = SECRET
⑤ ② ① ④ ③ ⑥
S E C R E T
I N F O R M
A T I O N X
cipher → FINTRNOOIAMX
① ② ③ ④ ⑤ ⑥
Cryptanalysis
* Study of breaking ciphers / reading encrypted messages without key
* Goal is to decrypt a message or recover a key.
* Type of attack depends on type of info available and interaction with cipher
Types of Attacks
→ CipherText only
→ Known PlainText
→ Chosen PlainText
→ Chosen CipherText
→ Chosen Text.
```

## Page 19
#### Unconditionally Secure Algorithm
#### Computationally Secure Algo
#### Brute Force
#### Frequency Analysis
```text
Unconditionally Secure Algorithm
→ CipherText has no enough info to allow cracking it.
→ Can't find plain text, no matter the resources / amount of cipher text
Computationally Secure Algo
→ Time to crack using a computer is too much (i.e. 1000 years)
Brute Force
→ Trying all possible values of key (Exhaustive Key Search)  → eg. • 26 values possible for Ceaser Cipher
• so we try all values of k to find plain text.
Frequency Analysis
→ A known table for frequency percentage of each letter in generic
messages.
→ We write frequency of each letter in cipher.
→ Then we substitute letters on basis of ranking of letters
according to frequency in our table and known table.
→ eg. • "E" is most frequent in known table
• we substitute "E" at place of most frequent letter in our cipher.
```

## Page 20
### Data Encryption Standard
```text
20-9-2023
Data Encryption Standard
⇒ Encrypt "A" using DES
A → 01000001
* Add padding,
plain text → 01000001 00000000 00000000 00000000
00000000 00000000 00000000 00000000
* Now we have 64 bit input block
L0 → First 32 bits (01000001 00 00 00)
R0 → Last 32 bits (00 00 00 00)
* We have a key that can be reduced to 56, then 48 using PC table
* For Round calculations, we use:
Li = Ri-1
Ri = Li-1 ⊕ f(Ri-1, Ki)
* Total Rounds → 16
* 64 bit key
* 4 Tables :-
→ PC1
→ PC2
→ Expansion Table
→ Substitution Table
```

## Page 21
### Advanced Encryption Standard
#### Structure of One Round
#### Sub Bytes
```text
7/10/2025
Tuesday
Advanced Encryption Standard
Key Size No. of Rounds
128
10
192
12
256
14
* State = Combination of
Structure of One Round
4 words
State → Sub Bytes → State → Shift Rows → State → Mix Columns → State
* At start of encryption, "Add Round Key". Then carry out these rounds Add Round Key
Sub Bytes
Final State
* Map old state to new according to map table
0 1 2 3 ___
eg.
EF
0 63 7C 77 7B
1 CA 82 C9 70
E
F
00 12
63 C9
13 33
70 C3
```

## Page 22
#### Shift Rows
#### Mix Columns
```text
Shift Rows
* First Row copied as it is.
* Second Row, each cell shifted one step left
* Third Row, each cell shifted two step left
AND SO ON
63 C9
63 C9
7D C3
C3 7D
Mix Columns
* Benchmark Polynomial → x^7 + x^6 + x^5 + x^4 + x^3 + x^2 + x + 1
* Occurance of a term having same power of x must be odd (x^3 + 2x^3 + 1 → x^3 + 1)
canceled.
eg. 00010001 → (x^4 + 1)
{Predefined Matrix} * {State} = {New State}
02 03 01 01   63 C9 FE 30
F2 63 26 F2
01 02 03 01
=
01 01 02 03
7D D4 C9 C9
03 01 01 02
D4 FA 63 89
P (always same)
O
N
N11 = {02}*{63} ⊕ {03}*{F2} ⊕ {01}*{7D} ⊕ {01}*{D4}
{02}*{63} = x * (x^5 + x^4 + x^3 + x^2 + x + 1)
= x^6 + x^5 + x^4 + x^3 + x^2 + x (01111110)
```

## Page 23
#### Add Round Key
```text
x^9 = x^4 + x^3 + x + 1
{03}*{F2} = (x+1) * (x^7 + x^6 + x^5 + x^3 + x^2 + x)
= x^8 + x^5 + x^4 + x
(00101001)
= x^5 + x^3 + 1
{01}*{7D} = x^6 + x^5 + x^4 + x^3 + x^2 + 1 (01111101)
{01}*{D4} = x^7 + x^6 + x^4 + x^2 (11010100)
* XOR above 4 values, you get,
11111110 → FE
∴ N11 = FE
* This same calculation is done for all cells.
Add Round Key
{State} ⊕ {Round Key} = {New State}
* Each cell XORed with corresponding cell in Round Key.
F2 19 = 0C 7a
eg
FE 63
⊕
C9 7D
77 FA
BE 87
Round Key
State
C9 ⊕ 77 = BE
FE ⊕ F2 = 0C
63 ⊕ 19 = 7a
7D ⊕ FA = 87
```

## Page 24
#### Key Expansion Process
```text
Key Expansion Process
w[i] = { w[i-4] ⊕ SubWord(RotWord(w[i-1])) ⊕ Rcon[i/4]
if i/4 = 0
w[i-4] ⊕ w[i-1]
otherwise
w0 w1 w2 w3
w4 w5 w6 w7
28 28
AB 46
58
A0
2B
1E
7E
AE
F7
20
FA
2B
DC
8C
15
D2
97
63
FE
8C
EB
88
16
A6
75
ED
17
EA
9F
62
∴ W4 = W0 ⊕ SubWord(RotWord(w3)) ⊕ Rcon[1]
* Rcon table is given for every round
W3 = 46 20 63 ED
RotWord(w3) = 20 63 ED 46
SubWord → B7 FB 55 5A
W4 = (28 7E 15 16) ⊕ (B7 FB 55 5A) ⊕ (01 00 00 00)
= A0 FA FE 17
given
```

## Page 25
#### Decryption
```text
W8 = W4 ⊕ SubWord(RotWord(w7)) ⊕ Rcon[2]
= (A0 FA FE 17) ⊕ (64 C4 AA 6A) ⊕ (02 00 00 00)
W7 = 58 8C 88 62
RotWord(w7) = 8C 88 62 58 = t
SubWord(t) = 64 C4 AA 6A
∴ W8 = (C4 3E 54 7D) ⊕ (02 00 00 00)
W8 = (C6 3E 54 7D)
Decryption
* At start of decryption, "Add Round Keys". Then carry out these rounds.
Structure of one Round
State → Add Round Key → State → Inv Mix Columns → State → Inv Shift Rows → State
Inv Sub Bytes
* This process is inverted form of encryption.
State
```

## Page 26
#### Inv Sub Bytes
#### Inv Shift Rows
#### Inv Mix Columns
```text
Inv Sub Bytes
* Table used at decryption is inverse of that used at encryption.
0
1
0 1 2 3 4 5 6 7 8 9
0
63 7C
0
1
CA
82
1
2
3
4
At encryption
3
6
00
7
11
At decryption.
Inv Shift Rows
63 C9 FE 30
63 C9 FE 30
F2 01 C1 B2
B2 F2 01 C1
EF 96 7D B4
D4 79 89 F1
79 89 F1 D4
Inv Mix Columns
* Same process but with different Predefined Matrix.
(Predefined Matrix) * (State) = (New State)
```

## Page 27
```text
0E 0B 0D 09
Predefined Matrix =
09 0E 0B 0D
0D 09 0E 0B
0B 0D 09 0E
```

## Page 28
### Lec 8: Cryptography & Public Key Infrastructure (PKI)
#### Public Key Cryptography
#### Ingredients of Public Key Encryption
```text
16-10-2025
Thursday
Lec 8: Cryptography & Public Key Infrastructure (PKI)
* Secret Key:- Key used in symmetric encryption
* Private Key/Public Key: Keys used in asymmetric encryption.
* Public Key is shared to all users.
* Private Key is known to the owner only
* Public Key Certificate binds identity to public key, signed by Certification (CA)
* PKI manages keys & certificates.
Authority
Public Key Cryptography
* Sender encrypts using reciever's public key (confidentiality)
* Then, sender encrypts using his private key (integrity)
* Reciever decrypts using sender's public key and his private key.
* Both, symmetric & asymmetric encryption are used together in practice.
* Encryption algorithms such as RSA are used.
Ingredients of Public Key Encryption
1) Plaintext
2) Encryption Algorithm
3) Public Keys
4) Private Keys
5) Ciphertext
6) Decryption Algorithm
```

## Page 29
#### Comparison
#### Applications of Public Key Cryptosystems
### Rivest-Shamir-Adleman (RSA) Algorithm
#### Basic Steps
```text
Comparison
Symmetric
Asymmetric
Keys
→ Single shared key
→ Key pair (private/public)
Key Exchange → Out-of-band
→ In-band
Scalability → Low
→ High
Speed → Fast
→ Slow
Use cases → Bulk Encryption
→ Small Data, signatures, PKI
Security Service → Confidentiality, Integrity
→ Confidentiality, Integrity, Authentication, Non-repudiation
Applications of Public Key Cryptosystems
* Encryption/Decryption
* Digital Signatures
* Key Exchange
Rivest-Shamir-Adleman (RSA) Algorithm
* Developed in 1977
Basic Steps
→ Choose two prime numbers p and q such that p ≠ q
→ Compute n = p x q
→ Compute φ(n) = (p-1)(q-1)
→ Choose e such that 1 < e < φ(n) and gcd(e, φ(n)) = 1
→ Compute d = e^-1 mod φ(n) OR d = ((φ(n) * i)+1)/e
→ Public Key = {e, n}
i > 1
→ Private Key = {d, n}
stop computing when
you get whole number
value of d
```

## Page 30
#### Encryption and Decryption
#### Some Mathematical Foundations
#### Example
```text
Encryption and Decryption
→ Encryption :- C = P^e mod n
Some Mathematical Foundations
→ Eucledian Algorithm :- find GCD / HCF
→ Euler's Totient Function (φ(n)):-
* If n is prime,
φ(n) = n-1
* If n = p x q,
φ(n) = (p-1)(q-1)
→ Multiplicative Inverse under mod n:-
* e.d ≡ 1 mod n
Example
→ Step 1:
p = 13 , q = 11
→ Step 2:
n = p x q = 143
→ Step 3:
φ(n) = (p-1)(q-1) = 12 x 10 = 120
→ Step 4:
e = 13
bcz 1 < e < 120 & gcd(e, 120) = 1
```

## Page 31
#### Applying Keys
```text
→ Step 5:-
* Finding d. We know that e = 13
→ d = ((φ(n) * i) + 1) / e
→ i = 1
d = (120+1)/13 = 9.3
→ i = 2
d = (240+1)/13 = 18.53
→ i = 3
d = (360+1)/13 = 27.76
→ i = 4
d = (480+1)/13 = 37
∴ d = 37
→ Step 6:
* Public Key → {13, 143}
* Private Key → {37, 143}
Applying Keys
→ Let's say P = 13
C = P^e mod n = 13^13 mod 143 = 52
→ Let's say C = 52
P = C^d mod n = 52^37 mod 143 = 13
```

## Page 32
### Lec 9: Public Key Cryptosystems
#### Diffie-Hellman Algorithm
#### Basic Steps
#### Finding 'g' values for a given 'p'
```text
Lec 9: Public Key Cryptosystems
Diffie-Hellman Algorithm
* Asymetric crypto (RSA) is strong but slow for bulk data
* Symetric crypto (AES) is fast but needs shared key
* Diffie-Hellman securely creates that shared key over an open channel
Basic Steps
* Values of prime (p) and generator (g) are public
1) R1 = g^x mod p
x is sender's secret value
2) R1 sent to reciever
3) R2 = g^y mod p
y is reciever's "  "
4) R2 sent to sender
selected by every user
5) K = (R2)^x mod p at sender
6) K = (R1)^y mod p at reciever
7) Shared Secret Key (K) = g^xy mod p
Finding 'g' values for a given 'p'
1) Value of p is given (eg. p = 17)
2) Find prime factors of p-1 (eg. {2} selected from {1,2,4,8,16})
3) Compute
g^((p-1)/q_i)
mod p for every possible value of g
4) Range for g is usually given. g is always less than p
5) Stop computing as soon as you get 1 in answer.
6) If, for a value of g, you compute for all values of q_i and don't
get a 1, that value of g is premitive root of p.
```

## Page 33
#### Example
#### Solving for g=12 (x = 3, y = 6)
```text
Example
→ p = 17, Find possible values of g in range 1<g<17
(p-1) = 16
Factors = {1,2,4,8,16}
Prime factors = {2} → single q
g^(16/q_i) mod p → g^8 mod 17
Formula →
→ g = 12
(12)^8 mod 17 = 16 → premitive root
→ g = 13
(13)^8 mod 17 = 1 → not premitive
→ g = 14
(14)^8 mod 17 = 16 → premitive root
→ g = 15
(15)^8 mod 17 = 1 → not premitive
→ g = 16
(16)^8 mod 17 = 1 → not premitive.
∴ g = 12, 14
Solving for g=12 (x = 3, y = 6)
R1 = (12)^3 mod 17 = 11
R2 = (12)^6 mod 17 = 2
K = (2)^3 mod 17 = (11)^6 mod 17 = 8
g^xy mod p = (12)^18 mod 17 =
Shared Secret Key =
```

## Page 34
### Lec 10: Cryptographic System Standards
#### Stages of Cryptographic Systems
#### Negotiation Stage
```text
Thursday
23/10/2025
Lec 10: Cryptographic System Standards
* Cryptographic systems are a packaged set of cryptographic countermeasures for protecting dialogue
* Needed when 2 parties communicate.
Stages of Cryptographic Systems
Confidentiality
Integrity
1) Initial Negotiation of Security Parameters
Authentication
2) Initial Authentication
3) Keying (source exchange of keys/secrets)
4) Ongoing Communication Stage with message-by-message.
Negotiation Stage
* Cipher suite is a specific set of security methods and options for a
particular cryptographic system standard.
* Includes specific set of methods/options for initial authentication, key
exchange, and ongoing message confidentiality, authentication, and integrity.
* Focus:- CIA planning
* Use of encryption algorithms we studied do ensure confidentiality but
not integrity (message not altered in between)
* Solution is Hashing:-
(Reciever)
(Sender)
Plain Text
Hashing
HMAC
Plain Text + Hash
Plain Text + Hash
Encryption
Decryption
send
Cipher
Cipher
```

## Page 35
#### Authentication Stage
```text
* If Plain Text and Hash don't match at Reciever's end, integrity has
been compromised.
* Now the issue is, what if man in middle changes plaintext, and hash accordingly
* This causes loss of authentication.
* Solution:-
→ Encrypt hash using your private key, at sender's side.
→ Can't change it
→ If public key of sender does not give real hash, authenticity
has been compromised
(Sender)
(Reciever)
Plain Text
Hashing
Plain Text + Hash
Private Key - RSA
Plain Text + Hash
Decrypt (sender's public)
Plain Text + Digital Signature
Encrypt using reciever's public key
Decrypt (reciever's private key)
send
Cipher
Authentication Stage
* Focus:- Integrity
* It has 3 key entities:-
1) Supplicant
→ The entity requesting access. Wants to prove identity (eg. client)
2) Credentials
→ Proofs of identity provided by the supplicant
3) Verifier
→ The entity verifying supplicant's identity by testing credentials (eg. server)
```

## Page 36
#### Keying Stage
#### Message-by-Message Authentication Stage
```text
Keying Stage
* Focus:- Confidentiality
* There are two types of ciphers for confidentiality:-
1) Symmetric Key Encryption.
→ Both parties use the same key (secret key)
→ A new symmetric session key is generated for each dialogue/
session for security.
2) Public Key Encryption (assymetric)
→ Key-pair of Public and Private Key
→ Key pair is typically long-lived and not changed frequently.
* Key Exchange Methods:-
1) Public Key Encryption (Hybrid)
→ Asymmetric process used to securely exchange the symmetric session key.
2) Diffie-Hellman Key Agreement
→ A fast public key encryption method.
→ Allows two parties to jointly establish a shared secret key
over an insecure channel.
Message-by-Message Authentication Stage
* This stage aims to protect messages against:-
1) Man-in-the-middle (MITM) attack.
2) Replay Attack
* Electronic Signature provides authentication (proof of sender) and message integrity
(proof message wasn't altered)
```

## Page 37
#### Digital Signatures & Certificates
#### Verifying a Digital Certificate
```text
* Two common types:-
1) Digital Signatures
2) Key-hashed message authentication codes (HMACs)
Digital Signatures & Certificates
* True party is the person the supplicant claims to be.
* Digital Signature is created by using Sender's private key
* It is verified by the reciever by using Sender's public key
* Digital Certificate is a file issued by a trusted Certificate Authority (CA)
* It binds the True Party's name to their public key.
Verifying a Digital Certificate
1) Test the CA's signature
→ The certificate itself is signed with the CA's private key.
→ Verify this signature using the CA's well-known public key.
2) Check the Valid Period
→ Ensure the current date/time is within the certificate's validity period
3) Check for Revocation.
→ Certificates may get revoked for improper behavior or other reasons.
→ Download the Certificate Revocation List (CRL) from the CA
and check if certificate's serial number is listed.
→ Other way is to query the CA directly using Online Certificate
Status Protocol (OCSP).
* Use of Digital Signatures brings Message Integrity.
* Use of Public Key Encryption is strong but expensive.
```

## Page 38
#### Key-Hashed Message Authentication Codes (HMACs)
#### Nonrepudiation
#### Quantum Security
#### Quantum Key Distribution (QKD)
```text
Key-Hashed Message Authentication Codes (HMACs)
* An authentication method that uses cryptographic hashing and a shared
secret key.
* It is much less computationally expensive than digital signatures.
* It does not provide nonrepudiation.
Nonrepudiation
* It means that the sender can not deny having sent a message.
* Digital Signatures provide nonrepudiation because:-
→ Sender uses his secret private key while sending
→ Can't blame anyone else as message has been decrypted using his public key
* HMACs don't provide nonrepudiation as:-
→ Both parties share same secret key.
→ Sender can claim that reciever forged the message
Quantum Security
* Quantum Mechanics describe the behavior of fundamental particles.
Quantum Key Distribution (QKD)
* Transmits a one-time key as long as the message.
* Unbreakable as a one-time key can't be cracked by cryptanalysis.
* If an interceptor reads a part of the key in transit, this will be
immediately apparent to the sender and reciever.
```

## Page 39
#### Quantum Key Cracking
```text
Quantum Key Cracking
* Leverages quantum mechanics to test many possible keys simultaneously.
* If realized, it could break today's strong encryption keys.
* In short, Cryptographic Systems combine all cryptographic protections
(Confidentiality, Authentication, Integrity) into a single, integrated system.
* It protects user dialogues from attackers, and abstracts the complexity,
so the users don't need to understand the underlying cryptographic
details.
```

## Page 40
### Lec 12: SQL Injection
#### Basic SQLI Example
#### Types of SQL Injection Attacks
#### UNION-Based Attacks
```text
Saturday
13/12/2025
Lec 12: SQL Injection
* An attack where malicious SQL code is inserted into queries.
* > 50% web attacks are SQL injection.
Basic SQLI Example
Vulnerable Code
$sql = "SELECT * FROM Users WHERE name='$user' AND pass='$pass'";
Normal Input
name = "frank"
pass = "123456"
Malicious Input
name = "frank' OR '1'='1"
pass = "anything"
* Returns all users.
Types of SQL Injection Attacks
UNION-Based Attacks
* Purpose is to extract data from other tables.
* Note that number of columns must & match.
Code
$sql = "SELECT name, description FROM products WHERE category='$cat'";
Injection
' UNION SELECT username, pass FROM users --
```

## Page 41
### Blind SQL Injection
#### Boolean Based
#### Time Based
#### Error Based
### Second Order SQL Injection
```text
Blind SQL Injection
* No direct error messages/data shown.
1) Boolean Based
* → If true, normal response
→ If false, error response.
eg. 'AND SUBSTRING((SELECT pass FROM users WHERE username = 'admin'),
1,1) = 'a' --
2) Time - Based
→ If delay occurs, condition was true
→ If no delay, condition was false
eg. '; IF (1=1) WAITFOR DELAY '0:0:30'; --
3) Error Based
→ Triggers SQL errors to extract info
eg. 'AND (SELECT CASE WHEN (1=1) THEN 1/0 ELSE 'a' END) = 'a'
Second Order SQL Injection
* Malicious input stored in database
* Later retrieved & executed in different context.
* Vulnerable sites can be found by Google Dorking.
```

## Page 42
### Techniques for Advanced Injection
### SQLI Countermeasures
```text
Techniques for Advanced Injection
→ Comment Variations
* --
* #
* %00
→ Encoding Techniques
* Hex Encoding
* CHAR() Function
* URL Encoding
SQLI Countermeasures
→ Parameterized Queries
→ Input Validation
* White listing (only alphanumeric values)
* Black listing (remove risky characters)
→ Escaping Functions
```

## Page 43
### Lec 13: HTTP(s)
#### HTTP Request Structure
#### HTTP Method
#### Important Headers
```text
13/12/2025
Saturday
Lec 13: HTTP(s)
* HyperText Transfer Protocol → Stateless application-layer protocol
* Uses request-response model b/w Client & Server
* Default Port → 80
HTTP Request Structure
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0
Accept: text/html
Cookie: sessionId = abc123
HTTP Method
→ GET: Retrieve resources (parameters in URL)
→ POST: Submit data (parameters in body)
→ PUT, DELETE, HEAD, OPTIONS
Important Headers
→ User-Agent : Client Software Identifier
→ Referer : Previous page URL
→ Cookie : Stored Session data
→ Accept : Acceptable content types
→ Connection: keep-alive → Reuse TCP connection.
```

## Page 44
#### HTTP Response Structure
#### Status Codes
#### HTTPS (HTTP Secure)
#### SSL/TLS Handshake
```text
HTTP Response Structure
HTTP/1.1 200 OK
Content-Type : text/html
Content-Length: 1234
Set-Cookie : session=xyz; Secure; HTTPOnly
<html> ... </html>
Status Codes
→ 2xx : Success
→ 3xx : Redirection
→ 4xx : Client error
→ 5xx : Server Error
HTTPS (HTTP Secure)
* HTTP + SSL/TLS encryption.
* Default Port → 443
* Provides :-
→ Confidentiality
(Encrypted Communication)
→ Integrity
(Data can't be modified in transit)
→ Authentication (Verify server identity via certificates)
SSL/TLS Handshake
* Client sends 'ClientHello' with supported cipher suites
* Server responds with 'ServerHello' certificate and public key
* Client verifies certificate, generates session key
* Encrypted communication begins.
```

## Page 45
#### Web Security Threats & Defenses
```text
Web Security Threats & Defenses
1) Downgrade Attacks
* Force protocol to use weaker encryption
* Defense :- Disable old TLS versions
2) Mixed Content
* HTTPS page loads HTTP resources
* Browser blocks/warns about insecure content
* Defense :- Use only HTTPS resources
3) SSL Strip Attacks
* MITM attacker strips HTTPS to HTTP
* Defense :- HSTS (HTTP Strict Transport Security)
4) Certificate Issues
* Self-signed certificates
* Expired certificates
* Wrong domain certificates
* Defense :- Never bypass certificate warnings.
```

## Page 46
### Lec 14: Cookies
#### What are Cookies
#### Cookie Attributes
```text
Saturday
13/12/2025
Lec 14: Cookies
* HTTP is stateless. It has no memory of previous requests.
* There is a need to maintain state across multiple requests
* Solutions → Hidden Fields, URL parameters, Cookies
What are Cookies
* Small pieces of info/data stored in browser
* Sent automatically with requests to matching domains.
* Key Attributes:-
→ Name & Value
→ Domain & Path
→ Expiration Date
→ Secure Flag
→ HttpOnly Flag
* How Cookies work:-
Client → Server : GET /login
Server → Client : Set-Cookie: sessionid= abc123; HttpOnly;
Client → Server : GET /profile (Cookie: sessionid= abc123)
Cookie Attributes
document.cookie = "name= value; domain= .example.com";
2) Path
document.cookie = "name= value; path= /dashboard";
```

## Page 47
#### Types of Cookies
```text
3) Secure Flag
eg. Set-Cookie: sessionid= xyz; Secure
4) HTTPOnly Flag
* Prevents Javascript access.
eg. Set-Cookie: sessionid= xyz; HttpOnly
5) Same Site Attribute
* Controls cross-site cookie sending (prevents CSRF)
* 3 values → Strict, Lax, None.
Types of Cookies
1) Session Cookies
→ Temporary. Deleted when browser closes
→ No expiration date.
2) Persistent Cookies
→ Stored until expiration date
→ eg. Set-Cookie: id= abc; Expires: Wed, 21 Oct 2025 07:28:00 GMT
3) First Party Cookies
→ Same domain as website
4) Third Party Cookies
→ From different domain (ads etc.)
→ Modern browsers block third-party cookies by default.
```

## Page 48
#### Cookie Security Issues
#### Browser Fingerprinting
```text
Cookie Security Issues
1) Cookie Theft
→ Causes session hijacking.
→ Can be done by :-
* Network Sniffing
* XSS Attack (steal via JavaScript)
* Physical Access to a device.
2) Session Fixation
→ Attacker sets user's session ID
→ Can be prevented by regenerating session ID at every login.
3) Cross-Site Request Forgery (CSRF)
→ Unauthorized commands by trusted user
→ Can be prevented by SameSite Cookies.
Browser Fingerprinting
* Alternative to cookies for tracking
* Collects browser/device characteristics :-
→ User Agent, Screen Resolution
Slides not clear :(
→ Installed Fonts, Plugins
→ Timezone, Language.
* Test your fingerprint
```

## Page 49
### Lec 15: CSRF (Cross-Site Request Forgery)
#### How CSRF works
#### CSRF Defense Mechanisms
```text
13/12/2025
Saturday
Lec 15: CSRF (Cross-Site Request Forgery)
* An attack that forces user to perform unwanted actions on a web app where
they are authenticated.
* Target → Users with active sessions on vulnerable websites
* Attack Goal → Make victim's browser send malicious requests to target site.
* Impact → State changing actions (transfers, change of password etc.)
How CSRF works
1) User logs in to 'bank.com' and gets session cookie.
2) User visits malicious site 'attacker.com'
3) Malicious site contains hidden request to 'bank.com'
4) Browser automatically sends request with user's cookies
5) Bank processes request as legitimate user action.
* Hidden Request might be in form of:-
→ Image Tag Exploit
→ Form Auto Submit
→ JSON/API CSRF
etc.
CSRF Defense Mechanisms
1) Referer/Origin Header Validation.
→ Referer: Checks previous page URL
→ Origin: Checks source domain (for CORS)
→ Limitations:-
* Headers can be spoofed/omitted
* Privacy Concerns/Browser Inconsistencies.
```

## Page 50
```text
2) Synchronizer Token Pattern (STP)
→ also called secret token
→ Most common/effective defense
→ How it works:-
* Server generates unique, unpredictable token
* Token is embedded in forms as hidden fields
* Token also stored at server-side (session)
* On submission, verify that token matches
3) Double Submit Cookie Pattern
→ Variation of STP without server-side storage.
→ How it works:-
* Set random token as cookie
* Include same token in form
* Verify cookie token == form token.
4) SameSite Cookie Attribute
→ Browser based defense
→ 3 values possible:
1) Strict (Never send in cross-site requests)
2) Lax (Send with top-level navigation GET requests)
3) None (Always send. (requires Secure Flag))
→ eg. Set-Cookie : sessionid = abc123; SameSite: Strict
5) Custom HTTP Headers
→ Set custom headers in HTTP Request/Response to set a token.
→ Verify that token at the event.
```

## Page 51
### Lec 16: XSS (Cross Site Scripting)
#### Same Origin Policy (SOP)
#### Types of XSS Attacks
```text
13/12/2025
Saturday
Lec 16: XSS (Cross Site Scripting)
* A security vulnerability allowing attackers to inject malicious scripts
into webpages viewed by other users.
* Causes Cookie Theft, Session Hijacking, Defacement, Malware Distribution
* XSS is caused by failure to properly validate/sanitize user input.
Same Origin Policy (SOP)
* Origin → protocol:// domain : port
* SOP Restriction → Scripts from one origin can't access resources from
another origin.
* XSS Bypass → Malicious script appears to come from same origin as
target site.
Types of XSS Attacks
1) Stored (Persistent) XSS
→ Malicious Script is stored on Server
→ Delivered to all visitors.
→ Common Locations :- Comments, Forums, Databases
→ Attack Flow:-
Attacker
→ Server
→ Browser Executes
Serves script
Injects script
into database
to user
2) Reflected (Non-Persistent) XSS
→ Script is reflected in immediate response (not stored)
→ Delivery :- Malicious URLs via Email, Phishing etc.
→ Attack Flow:-
Attacker sends malicious URL → User Clicks → Server echos script → Browser
```

## Page 52
#### XSS Defense Mechanisms
```text
3) DOM-based XSS
→ Client side JavaScript processes untrusted data unsafely
→ No server involvement
→ Entire attack occurs in browser.
* XSS Attacks may be contained by:-
→ HTML Tags
→ Event Handlers
→ JavaScript Protocol
→ Encoded Data
XSS Defense Mechanisms
1) Input Validation & Sanitization
→ Whitelist Approach
└→ allow only alphanumeric values
→ HTML Purification.
2) Output Encoding
→ Context Specific Encoding done to avoid data leakage.
3) Content Security Policy (CSP)
→ Modern defense strategy
→ Implemented via HTTP header.
→ Common CSP directives:-
• default-src → Fallback for other resource types
• script-src → Controls script sources
• style-src →
" stylesheet "
• img-src →
" image "
```

## Page 53
#### XSS vs CSRF
```text
• connect-src → Controls fetch, XHR, WebSocket
• frame-src → Controls frame sources
• report-uri → Send violation reports
→ Usage :-
header ("Content-Security-Policy:" .
"default-src 'self';" .
"object-src 'none';");
4) HttpOnly Cookies
→ Set-Cookie: sessionId=abc123; HttpOnly=True; Secure
5) Input Length Limits
6) Regular Expression Filtering
XSS vs CSRF
* XSS exploits the trust a "client browser" has in the data sent from
the "legitimate website."
(attacker tries to control what website sends to client)
* CSRF exploits the trust a "legitimate website" has in the data sent
from the "client browser"
(attacker tries to control what client sends to the website)
```

## Page 54
### Lec 17: Access Control
#### Access Control Protections
```text
Saturday
13/12/2025
Lec 17: Access Control
* Access → Ability to approach, enter, or retrieve resources.
* Physical → Entering a place
* Logical → Retrieving data.
* Access Modes → Read, Write, Append, Execute, Delete, Create, Search.
* Access Control → Policy-driven limitation of access to systems, data, and
dialogues.
Access Control Protections
1) Identification
→ Uniquely identifies a user
→ Maybe unique & standardized
→ Should not reveal extra user info
2) Authentication
→ Verifies identity using:-
• What you know (password)
• What you have (card, token)
• What you are (biometrics)
• What you do (behavioral patterns)
3) Authorization
→ Grants permissions based on identity/role.
→ Principle of Least Permissions :- Give minimal permissions at start.
4) Auditing
→ Logs and reviews access activities
```

## Page 55
#### Authentication Methods
#### Passwords
#### Access Cards and Tokens
#### Biometrics
```text
5) Accountability
→ Holds user responsible for actions
6) Non-Repudiation
→ Prevents denial of actions.
Authentication Methods
* Credentials are based on 4 principles:-
1) What you Know ?
2) " " have ?
3) " " are ?
4) " " do ?
Passwords
→ 2 Types :- Reusable Passwords + One-time Passwords (OTP)
→ Vulnerable to cracking, Social Engineering
→ Policies :- Complexity, Duration, Multi-site Uniqueness
Access Cards and Tokens
→ Access Cards:- Magnetic Stripe Cards / Smart Cards
→ Tokens :- USB Key / Rolling Code Generators
→ Uses Radio Frequency Id (RFID) for proximity access
→ Loss/Theft addressed by Cancellation
Biometrics
→ Uses biological traits (fingerprints, iris, face etc.)
→ Enrollment by Template Creation
→ Verification done against template to identify user.
```

## Page 56
#### Multi-Factor Authentication
#### Authorization Models
#### Access Matrix
```text
→ Error Rate: Accuracy when user is not trying to deceive the system.
→ Deception Rate: Likelihood that an imposter can deceive the system
→ Error Rates:-
• False Acceptance Rates (FAR)
• False Rejection Rates (FRR)
Performance Analytics
• Failure to Enroll
(FTE)
Multi-Factor Authentication
* Uses >= 2 authentication factors
* eg. Card + PIN (2 factor auth)
* Vulnerable to Trojan Horse, MITM Attack.
Authorization Models
* Individual Access Control:- Per-user permission
* Role-based Access Control:- Permission distributed by role
* Mandatory Access Control (MAC):- Strict. Centrally Controlled.
* Discretionary Access Control (DAC):- Flexible. Controlled by Groups/Departments
* Multi-level Security:- Resources/Users ranked by clearance.
Access Matrix
OBJECTS
File 1
File 2
File 3 File 4
SUBJECTS
User A
Own
Own
Read
Read
Read
Write
Read
User B
Own
Write Read
User C
Read
Read
Own
Write
Read
```

## Page 57
#### Access Control Structures
#### Auditing and Logging
```text
Access Control Structures
→ Access Control List (ACL) for File 1
File 1
A
B
C
Own
R
R
R
W
→ Capability List of User A
User A → File 1
File 3
Own
R
R
Auditing and Logging
* Logging → Record events
* Log reading must be regular
* Automatic Alerts set for high-risk events
```

## Page 58
### Lec 18: Network Security
#### Common Network Security Controls
#### Denial-of-Service (DOS) Attack
```text
Saturday
13/12/2025
Lec 18: Network Security
* Set of rules/technologies/processes designed to ensure CIA Triad.
Common Network Security Controls
1) Firewalls
→ Filter the traffic
→ Isolate Network Section to limit breach impact
2) Network Segmentation
3) Access Control
→ Restrict Network Access to Authorized Users
4) Zero Trust Network Architecture
→ Trust None/Verify Everyone
5) Remote Access VPN (SSL VPN)
→ Secure Remote Connections
→ Protect against Phishing/Spam
6) Email Security
7) Data Loss Prevention (DLP)
→ Prevent unauthorized data transfer
8) Intrusion Detection/Prevention Systems (IDPS) → Monitor & Block threats
9) Sandboxing
→ Test suspicious files in a safe environment
10) Cloud Network Security
→ Protect Cloud based resources
Following are the threats that compromise CIA Triad:-
Denial-of-Service (DOS) Attack
* Goal → Overwhelm in a system/network to make it unavailable
* How → Flood target with traffic. Consume Resources. Exploit Vulnerabilities
* Impact → Disruption of services. Loss of Revenue. Reputational Damage.
* Targets :-
• Web Servers
• DNS Servers
• Email Servers
• Network Bandwidth
• Application Services
```

## Page 59
#### Distributed Denial-of-Service (DDOS) Attack
#### Botnets
```text
Distributed Denial-of-Service (DDOS) Attack
* What → A DoS attack launched from multiple compromized systems.
* Often coordinated via a Botnet.
* Harder to mitigate due to distributed resources.
Botnets
* A network of infected computers (bots/zombies) controlled by an
attacker (botmaster).
* Used for :-
• DDoS attacks
• Spamming
• Traffic Sniffing
• Keylogging
• Spreading Malware
• Ad fraud
• Identity Theft.
* Botnet Creation :- Malware Infection
Device becomes a part of Botnet
Awaits Commands.
```
