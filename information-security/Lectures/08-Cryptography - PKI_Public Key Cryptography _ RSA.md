### Lecture 08 – Public Key Cryptography, PKI, and RSA (Summary Notes)

---

### 1. Symmetric vs Asymmetric

- **Symmetric**: one shared secret key; fast; hard key distribution; used for bulk data.
- **Asymmetric (public key)**:
  - Key pair: public (shared) + private (secret).
  - Public key for encryption / signature verification.
  - Private key for decryption / signing.
  - Slower; mainly used for keys, small data, and signatures.

---

### 2. PKI (Public Key Infrastructure)

- **Goals**: Manage keys and bind public keys to identities.
- **Components**:
  - **Certificate Authority (CA)**: trusted entity that issues signed certificates.
  - **Digital Certificate**: contains subject identity, public key, validity, issuer, CA signature.
- **Uses**:
  - **Confidentiality**: Encrypt with receiver’s **public** key.
  - **Integrity/Authentication**: Verify signatures created with sender’s **private** key.
- **Symmetric vs Asymmetric comparison**:
  - Symmetric: fast, poor scalability.
  - Asymmetric: scalable, but slower → used in hybrid designs (public key for key exchange, symmetric for data).

---

### 3. RSA Algorithm

- **Key generation**:
  1. Choose primes \( p, q \), \( p \ne q \).
  2. \( n = pq \).
  3. \( \phi(n) = (p-1)(q-1) \).
  4. Choose \( e \) with \( 1 < e < \phi(n) \) and \( \gcd(e,\phi(n)) = 1 \).
  5. Compute \( d = e^{-1} \bmod \phi(n) \).
  - Public key: \( (e, n) \); Private key: \( (d, n) \).
- **Operations**:
  - Encryption: \( C = P^e \bmod n \).
  - Decryption: \( P = C^d \bmod n \).
- **Example** (small): \( p=13, q=11, n=143, \phi(n)=120, e=13, d=37 \).

---

### 4. Diffie–Hellman Key Exchange (High-Level)

- **Goal**: Two parties create a shared secret over an insecure channel.
- **Public values**: prime \( p \), generator \( g \).
- **Steps**:
  - Alice picks secret \( x \), sends \( R_1 = g^x \bmod p \).
  - Bob picks secret \( y \), sends \( R_2 = g^y \bmod p \).
  - Both compute shared key \( K = g^{xy} \bmod p \) (Alice via \( R_2^x \), Bob via \( R_1^y \)).
- **Primitive root check**: verify \( g^{(p-1)/f} \not\equiv 1 \pmod p \) for each prime factor \( f \) of \( p-1 \).

---

### 5. Role in Cryptographic Systems

- PKI + RSA + Diffie–Hellman used for:
  - **Negotiation** of algorithms (cipher suites).
  - **Authentication** using certificates and signatures.
  - **Keying**: exchanging symmetric session keys securely.
  - **Ongoing communication**: then uses symmetric ciphers and MACs/hashes.


