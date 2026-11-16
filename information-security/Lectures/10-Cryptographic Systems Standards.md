### Lecture 10 – Cryptographic Systems Standards (Summary Notes)

---

### 1. Four Stages of a Cryptographic System

- **Negotiation**:
  - Agree on a **cipher suite** (key exchange, symmetric cipher, hash/MAC, modes).
  - Client proposes options; server selects secure, compatible set.
- **Initial Authentication**:
  - Roles: **Supplicant** (client) and **Verifier** (server).
  - Use credentials (e.g., passwords, certificates) to verify identity.
  - Server commonly proves identity with a CA-signed **digital certificate**.
- **Keying**:
  - Establish symmetric session keys using:
    - **Public key encryption** (e.g., RSA-encrypted session key), or
    - **Diffie–Hellman** key exchange (shared secret from exchanged values).
- **Ongoing Communication**:
  - Use symmetric encryption (e.g., AES) + integrity mechanisms (HMAC or AEAD modes like GCM) per message.

---

### 2. Integrity, Hashing, and Authentication

- **Hashes**:
  - Map arbitrary messages to fixed-length digests (e.g., SHA‑256).
  - Provide integrity checks but alone are vulnerable to MITM altering both message and hash.
- **Digital Signatures**:
  - Signer hashes the message and encrypts the hash with their **private key**.
  - Verifier decrypts signature with **public key** and compares with fresh hash.
  - Gives integrity, authentication, and non‑repudiation.
- **MAC / HMAC**:
  - MAC = integrity check based on a shared secret key.
  - **HMAC** uses a hash + secret key; faster than signatures; provides integrity and mutual authentication but not non‑repudiation.

---

### 3. Digital Certificates and PKI

- **Certificate**:
  - Binds subject identity to a public key; signed by a **Certificate Authority (CA)**.
  - Contains subject, public key, validity, issuer, and CA signature.
- **Verification**:
  1. Verify CA’s signature.
  2. Check validity period.
  3. Check revocation (CRL/OCSP).
- Used heavily in protocols like HTTPS/TLS for server (and sometimes client) authentication.

---

### 4. Quantum Considerations (Preview)

- **Quantum Key Distribution (QKD)**:
  - Uses quantum channels to share keys; eavesdropping is detectable.
- **Quantum Threats**:
  - Future quantum computers may break current public key systems (RSA, DH, ECC), driving research into post‑quantum cryptographic standards.


