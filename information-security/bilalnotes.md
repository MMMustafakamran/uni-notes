
### **Chapter 1: Introduction to Information Security**

**Overview and Objectives**
Information Security involves protecting data in digital formats, securing it during storage, transmission, and processing, and blocking unauthorized access. Weak security leads to data breaches and compromised confidentiality.

The core objectives are defined by the **CIA Triad**:

* **Confidentiality:** Preventing unauthorized disclosure of information.
* **Integrity:** Maintaining accuracy, consistency, and trustworthiness of data. Events compromising integrity include accidental deletion or entering invalid data. Countermeasures include hashing, access control, and Cyclic Redundancy Checks (CRC).
* **Availability:** Ensuring reliable and timely access to information and resources. Countermeasures involve load balancing and software backups.

**Security Protections & Terminologies**
To secure information, systems utilize specific protections:

* **Identification:** Determining who the user is.
* **Authentication:** Proving the user's identity.
* **Authorization:** Determining what the user is allowed to do.
* **Auditing/Accounting:** Recording usage and tracking actions.

Key security terminologies include:

* **Asset:** An item of value.
* **Threat:** Actions or events with potential harm.
* **Threat Agent:** The element carrying out the threat.
* **Vulnerability:** A flaw allowing a threat agent to bypass security.
* **Risk:** The situation involving exposure to danger.

**Risk Mitigation Strategies**
There is a trade-off between security and convenience. Risk mitigation strategies include:

1. **Risk Avoidance:** Identifying risk but not engaging in the activity.
2. **Acceptance:** Accepting the risk will occur (ignoring it).
3. **Risk Mitigation:** Addressing the risk to make it less serious.
4. **Deterrence:** Warning attackers of consequences.
5. **Transference:** Transferring risk to a third party.

**Advanced Persistent Threats (APT) & Cyber Kill Chain**
APTs are long-term, stealthy, and sophisticated attacks, often state-sponsored, targeting high-value organizations for espionage or data theft.

The **Cyber Kill Chain** outlines the stages of an attack:

1. **Reconnaissance:** Identifying targets.
2. **Weaponization:** Coupling an exploit with a payload.
3. **Delivery:** Transmitting the weapon to the target.
4. **Exploitation:** Executing code to exploit a vulnerability.
5. **Installation:** Installing malware to establish a foothold.
6. **Command & Control (C2):** Establishing remote control.
7. **Actions on Objectives:** Achieving the attacker's goal.

**Defense Principles**
Effective defense follows these principles:

* **Layering (Defense in Depth):** Using multiple security controls.
* **Limiting (Least Privilege):** Restricting access to the minimum necessary.
* **Diversity:** Using products from different vendors to avoid single points of failure.
* **Obscurity:** Hiding internal system details.
* **Simplicity:** Keeping systems simple to manage and reduce attack surfaces.

---

### **Chapter 2: Malware & Social Engineering**

**Malware Fundamentals**
Malware is malicious software that installs without consent to damage systems. Its key traits are stealth, unauthorized installation, and persistence. Malware spreads via infected USB drives, malicious downloads, and network propagation (worms).

**Types of Malware**

1. **Virus:** Attaches to files/programs and requires user action to spread.
2. **Worm:** Replicates without user action and spreads through networks.
3. **Trojan:** Disguised as legitimate software but opens backdoors.
4. **Ransomware:** Encrypts user files and demands payment for access.
5. **Spyware/Adware:** Monitors activity or displays unwanted ads.
6. **Rootkits/Logic Bombs:** Rootkits modify OS functions to hide; logic bombs trigger on specific events.

**Social Engineering**
This involves tricking users into revealing sensitive information. Techniques include:

* **Phishing:** Fake emails/websites to steal data.
* **Spear Phishing:** Targeting specific individuals.
* **Whaling:** Targeting executives.
* **Vishing:** Voice-based scams.
* **Typo-Squatting:** Fake domains with minor typos (e.g., `goggle.com`).
* **Tailgating:** Following someone physically into a secure area.
* **Dumpster Diving:** Searching trash for discarded data.
* **Shoulder Surfing:** Observing someone's screen or keyboard.

---

### **Chapter 3: Cryptography**

**Symmetric Key Cryptography**
Also known as conventional or single-key encryption, where the key is shared between the sender and receiver.

**Classical Ciphers**

1. **ROT-13:** A substitution cipher where each letter moves 13 positions.
   * Encryption: \( C = (p + 13) \% 26 \).

2. **Caesar Cipher:** Substitutes letters by moving them 3 positions ahead.
   * Encryption: \( C = (p + k) \% 26 \) (where \( k = 3 \)).
   * Decryption: \( P = (c - k) \% 26 \).

3. **Affine Cipher:**
   * Encryption: \( E(x) = (ax + b) \% m \).
   * Decryption: \( D(x) = a^{-1}(x - b) \% m \).
   * **Note:** \( a \) and \( m \) (usually 26) must be co-prime. To find \( a^{-1} \), find a value such that \( (a \cdot a^{-1}) \% m = 1 \).

4. **Vigenère Cipher:** Similar to Caesar cipher but uses a list of keys (e.g., \( k = \{k_1, k_2\} \)).
   * Encryption: \( C = (p + k) \% 26 \).
   * Decryption: \( P = (c - k) \% 26 \).

**Transposition Ciphers**

1. **Rail Fence:** Plaintext is written as a sequence of diagonals and read off as rows.
2. **Columnar Transposition:** Uses a keyword. The key is arranged in alphabetical order to determine the column reading order.

**Cryptanalysis & Security Definitions**

* **Cryptanalysis:** Breaking ciphers or recovering keys without the original key. Attacks include Ciphertext Only, Known Plaintext, Chosen Plaintext, and Chosen Ciphertext.
* **Unconditionally Secure:** Ciphertext provides insufficient info to crack, regardless of resources.
* **Computationally Secure:** Time to crack is too long (e.g., 1000 years) using current computers.
* **Frequency Analysis:** Using known letter frequency tables (e.g., 'E' is most common) to crack substitution ciphers.

**Data Encryption Standard (DES)**

* DES encrypts 64-bit blocks of plain text.
* The key is reduced to 56 bits, then 48 bits using Permutation Choice (PC) tables.
* It consists of 16 rounds.

**Round Calculation:**

* \( L_i = R_{i-1} \)
* \( R_i = L_{i-1} \oplus f(R_{i-1}, K_i) \)

**Process Overview:**

* To encrypt a block (e.g., "A"), the data is padded to create a 64-bit input block.
* Structure: The 64-bit block is split into a Left half (\( L_0 \)) and a Right half (\( R_0 \)), each consisting of 32 bits.
* Round Calculation: The algorithm uses 16 rounds with:
  * \( L_i = R_{i-1} \)
  * \( R_i = L_{i-1} \oplus f(R_{i-1}, K_i) \)
* Keys: A 64-bit key is used, which is reduced to 56 bits and then to 48 bits using Permuted Choice (PC1 and PC2) tables.
* Tables Used: Expansion, Substitution, PC1, and PC2.

**Advanced Encryption Standard (AES)**

**Key Sizes and Rounds**

* 128-bit Key: 10 Rounds  
* 192-bit Key: 12 Rounds  
* 256-bit Key: 14 Rounds

**Encryption Round Structure**

* A "State" is a combination of 4 words.
* The rounds (except the start and end) typically follow this sequence:
  1. **Add Round Key:** XOR state with the key.
  2. **Sub Bytes:** Map the old state to a new state using a substitution table (S-box).
  3. **Shift Rows:**
     * First row: Copied as is.
     * Second row: Shifted one step left.
     * Third row: Shifted two steps left.
  4. **Mix Columns:**
     * Uses a benchmark polynomial \( x^8 + x^4 + x^3 + x + 1 \).
     * The state is multiplied by a predefined matrix to generate a new state.
  5. **Add Round Key (Final Step of Round):** Each cell of the state is XORed with the corresponding cell in the Round Key.

**Key Expansion Process**

* Keys are expanded using operations like RotWord (rotating the word), SubWord (substituting bytes), and Rcon (Round Constant).
* Formula: \( W[i] = W[i-1] \oplus W[i-4] \) (with specific conditions for every 4th word).

**AES Decryption**

* The process is the inverted form of encryption:
  * Add Round Keys → Inverse Shift Rows → Inverse Sub Bytes → Add Round Key → Inverse Mix Columns.
* Uses the inverse of the encryption tables (e.g., Inverse S-box).
* Inverse Mix Columns uses a different predefined matrix (containing 0E, 0B, 0D, 09).

**Public Key Infrastructure (PKI)**

**Key Concepts**

* **Secret Key:** Used in symmetric encryption.
* **Private/Public Keys:** Used in asymmetric encryption. The public key is shared with everyone, while the private key is known only to the owner.
* **Certificate Authority (CA):** Signs Public Key Certificates to bind an identity to a public key.
* **PKI:** Manages keys and certificates.

**Public Key Cryptography Usage**

* **Confidentiality:** Sender encrypts using the Receiver's Public Key.
* **Integrity/Authentication:** Sender encrypts using their own Private Key.

**Ingredients:**

* Plaintext, Encryption Algorithm, Public Keys, Private Keys, Ciphertext, Decryption Algorithm.

**Comparison: Symmetric vs. Asymmetric**

* **Keys:** Symmetric uses a single shared key; Asymmetric uses a key pair.
* **Scalability:** Symmetric is low; Asymmetric is high.
* **Speed:** Symmetric is fast; Asymmetric is slow.
* **Usage:** Symmetric for bulk encryption; Asymmetric for small data and signatures.

**RSA Algorithm**

**Steps to Generate Keys**

1. Choose two prime numbers \( p \) and \( q \) (\( p \neq q \)).
2. Compute \( n = p \times q \).
3. Compute Euler's Totient \( \phi(n) = (p-1)(q-1) \).
4. Choose \( e \) such that \( 1 < e < \phi(n) \) and \( gcd(e, \phi(n)) = 1 \).
5. Compute \( d \) such that \( d = e^{-1} \mod \phi(n) \) (or \( d = ((\phi(n) \times i) + 1) / e \)).
6. Public Key: \( \{e, n\} \).
7. Private Key: \( \{d, n\} \).

**Encryption/Decryption Formulas**

* Encryption: \( C = P^e \mod n \).
* Decryption: \( P = C^d \mod n \).

**RSA Example** (\( p = 13, q = 11 \))

* \( n = 143 \).
* \( \phi(n) = 12 \times 10 = 120 \).
* Choose \( e = 13 \) (coprime to 120).
* Calculate \( d \): Using the formula, for \( i = 4 \), \( d = (480+1)/13 = 37 \).
* Keys: Public \( \{13, 143\} \), Private \( \{37, 143\} \).

**Diffie-Hellman Key Exchange**

**Overview**

Securely creates a shared secret key over an insecure channel.

* Public values: Prime \( p \) and Generator \( g \).

**Steps**

1. Sender calculates \( R_1 = g^x \mod p \) (where \( x \) is secret).
2. Receiver calculates \( R_2 = g^y \mod p \) (where \( y \) is secret).
3. They exchange \( R_1 \) and \( R_2 \).
4. Sender computes Key \( K = (R_2)^x \mod p \).
5. Receiver computes Key \( K = (R_1)^y \mod p \).
6. Shared Secret: \( K = g^{xy} \mod p \).

**Primitive Root Check**

To find if \( g \) is a primitive root of \( p \), compute \( g^{(p-1)/f} \mod p \) for all prime factors \( f \) of \( p-1 \). If the result is never 1, it is a primitive root.

**Cryptographic System Standards**

**Stages of Cryptographic Systems**

1. **Negotiation:** Agreeing on a "Cipher Suite" (security methods/options).
2. **Initial Authentication:** Verifying identities (Supplicant vs. Verifier).
3. **Keying:** Exchanging keys for confidentiality (Symmetric or Public Key methods).
4. **Ongoing Communication:** Message-by-message confidentiality, authentication, and integrity.

**Integrity and Hashing**

* Encryption alone does not ensure integrity.
* **Solution:** Hashing. If the plaintext and hash don't match at the receiver's end, integrity is compromised.
* **Digital Signature:** To prevent Man-in-the-Middle (MITM) attacks on the hash, the sender encrypts the hash with their Private Key.

**Authentication Stage**

* **Supplicant:** The entity requesting access.
* **Verifier:** The entity testing credentials (e.g., server).
* **Credentials:** Proofs of identity.

**Keying Stage Exchange Methods**

* **Public Key Encryption (Hybrid):** Uses asymmetric encryption to exchange a symmetric session key.
* **Diffie-Hellman:** Allows joint establishment of a shared secret.

**Message Authentication**

Protects against MITM and Replay attacks.

* **Digital Signatures:** Provide non-repudiation (sender cannot deny sending) because they use the sender's private key.
* **HMAC (Key-Hashed Message Authentication Code):** Uses hashing and a shared secret key. It is faster than digital signatures but does not provide non-repudiation.

**Digital Certificates**

* Issued by a CA to bind a name to a public key.

**Verification:**

1. Test CA's signature.
2. Check validity period.
3. Check revocation (CRL or OCSP).

**Quantum Security**

* **Quantum Key Distribution (QKD):** Transmits a one-time key. If intercepted, it is immediately apparent.
* **Quantum Key Cracking:** Could leverage quantum mechanics to test many keys simultaneously, threatening current encryption.

---

### **Lec 12: SQL Injection**

**Definition:** An attack where malicious SQL code is inserted into queries, accounting for over 50% of web attacks.

**Attack Mechanism:** Malicious input (e.g., `' OR '1'='1`) alters the query logic to bypass authentication or retrieve unauthorized data.

**Types of Attacks:**

* **UNION-Based:** Extracts data from other tables by combining results; requires column counts to match.
* **Blind SQL Injection:** No error messages are shown; attackers use Boolean (True/False) or Time-based (delays) inference.
* **Second Order:** Malicious input is stored in the database and executed later in a different context.

**Countermeasures:** Use parameterized queries, input validation (whitelisting/blacklisting), and escaping functions.

---

### **Lec 13: HTTP(S)**

**HTTP Basics:** A stateless application-layer protocol using a request-response model on Port 80.

* **Methods:** GET (retrieve), POST (submit), PUT, DELETE, etc.
* **Status Codes:** 2xx (Success), 3xx (Redirection), 4xx (Client Error), 5xx (Server Error).

**HTTPS (Secure):** HTTP over SSL/TLS (Port 443) providing confidentiality, integrity, and authentication.

**Handshake:** Client and server exchange hello messages, certificates, and keys to establish an encrypted session.

**Threats & Defenses:**

* **Downgrade Attacks:** Forcing weaker encryption protocols; prevent by disabling old TLS versions.
* **SSL Strip:** MITM strips HTTPS to HTTP; prevent using HSTS (HTTP Strict Transport Security).

---

### **Lec 14: Cookies**

**Purpose:** Maintain state in the stateless HTTP protocol.

**Attributes:**

* **Secure:** Cookie sent only over HTTPS.
* **HttpOnly:** Prevents JavaScript access (mitigates XSS).
* **SameSite:** Controls cross-site sending to prevent CSRF (Values: Strict, Lax, None).

**Types:**

* Session (temporary)
* Persistent (stored until expiration)
* First-party (same domain)
* Third-party (tracking/ads)

**Security Issues:**

* Cookie theft (session hijacking)
* Session Fixation (attacker sets session ID)
* CSRF

**Browser Fingerprinting:** An alternative to cookies that tracks users via device characteristics like screen resolution, fonts, and user agent.

---

### **Lec 15: Cross-Site Request Forgery (CSRF)**

**Definition:** An attack forcing an authenticated user to perform unwanted state-changing actions (e.g., money transfer) on a trusted site.

**Mechanism:** A malicious site sends a hidden request (via image tags, forms) to the target site using the victim's active cookies.

**Defenses:**

* **Synchronizer Token Pattern (STP):** Server generates a unique hidden token for forms; requests fail if the token is missing or incorrect.
* **Double Submit Cookie:** Token sent as both a cookie and a form parameter; the server verifies they match.
* **SameSite Attribute:** Restricts when cookies are sent with cross-site requests.

---

### **Lec 16: Cross-Site Scripting (XSS)**

**Definition:** Injecting malicious scripts into webpages viewed by others, often due to poor input sanitization.

**Same Origin Policy (SOP):** Restricts scripts from one origin accessing resources from another; XSS bypasses this by making the script appear to come from the trusted site.

**Types:**

* **Stored (Persistent):** Script stored on the server (e.g., database, comments) and served to victims.
* **Reflected:** Script reflected immediately in the response (e.g., via malicious URL parameters).
* **DOM-based:** Client-side script processes untrusted data unsafely without server involvement.

**Defenses:**

* **Input Validation & Output Encoding:** Sanitize inputs and encode context-specific output.
* **Content Security Policy (CSP):** HTTP header controlling allowed sources for scripts, images, and styles.

**XSS vs. CSRF:** XSS exploits the user's trust in a website; CSRF exploits the website's trust in a user's browser.

---

### **Lec 17: Access Control**

**Core Concepts:**

* **Identification:** Uniquely identifying a user.
* **Authentication:** Verifying identity via "What you know" (passwords), "What you have" (tokens), "What you are" (biometrics), or "What you do".
* **Authorization:** Granting permissions based on identity/role (Least Privilege principle).

**Biometrics:** Uses biological traits; accuracy is measured by False Acceptance Rate (FAR) and False Rejection Rate (FRR).

**Models:**

* **Discretionary Access Control (DAC):** Flexible, controlled by owners/groups.
* **Mandatory Access Control (MAC):** Strict, centrally controlled.
* **Role-Based Access Control (RBAC):** Permissions distributed by role.

**Structures:** Access Control Lists (ACLs) and Capability Lists manage permissions (Read, Write, Own).

---

### **Lec 18: Network Security**

**Controls:** Firewalls, Network Segmentation, Zero Trust Architecture, VPNs, IDS/IPS, and Sandboxing.

**Availability Threats:**

* **DoS (Denial of Service):** Overwhelms systems to make them unavailable.
* **DDoS (Distributed DoS):** Launched from multiple compromised systems, often via Botnets.

**Botnets:** A network of infected devices ("zombies") controlled by a botmaster for attacks like DDoS, spam, and traffic sniffing.


