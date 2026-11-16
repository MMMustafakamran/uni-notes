### Lecture 09 – Public Key Cryptosystems (Summary Notes)

---

### 1. Main Uses of Public Key Cryptography

- **Confidentiality**: Encrypt with recipient’s **public key**, decrypt with private key.
- **Authentication & Integrity (Signatures)**:
  - Sign with **private key** (usually over a hash of the message).
  - Verify with **public key**.
  - Provides integrity, origin authentication, and non-repudiation.
- **Key Exchange**: Establish symmetric session keys securely (e.g., via RSA or Diffie–Hellman).

---

### 2. Hybrid Cryptosystems

- Combine asymmetric and symmetric methods:
  - Asymmetric used only in handshake to authenticate and exchange a session key.
  - Symmetric cipher (e.g., AES) used for bulk data encryption.
- Benefits:
  - **Performance**: avoids expensive public key operations on large data.
  - **Security**: strong key distribution and authentication + efficient confidentiality.

---

### 3. Diffie–Hellman Key Exchange (Reused Here)

- Public parameters: prime \( p \), generator \( g \).
- Alice: secret \( x \), sends \( g^x \bmod p \).
- Bob: secret \( y \), sends \( g^y \bmod p \).
- Shared key:
  - Alice: \( K = (g^y)^x = g^{xy} \bmod p \).
  - Bob: \( K = (g^x)^y = g^{xy} \bmod p \).
- Both share K without transmitting it directly.

---

### 4. Digital Signature Concept (RSA Example)

- **Signing**:
  - Compute \( h = \text{Hash}(M) \).
  - Signature \( S = h^d \bmod n \) using private key \( d \).
- **Verification**:
  - Recompute \( h' = \text{Hash}(M) \).
  - Compute \( h_v = S^e \bmod n \) using public key \( e \).
  - If \( h_v = h' \), signature is valid.
- Provides integrity, authenticity, and non‑repudiation.

---

### 5. Public Key Schemes Overview

- **RSA**: encryption + signatures; based on factoring hardness.
- **Diffie–Hellman**: key agreement; based on discrete logs.
- **ECC-based schemes** (conceptual mention):
  - ECDH, ECDSA for key exchange and signatures with smaller keys.

---

### 6. Final Comparison

- **Use symmetric algorithms (AES)** for:
  - High-speed, large-volume encryption after a key is shared.
- **Use public key cryptosystems (RSA, DH, ECC)** for:
  - Secure key distribution.
  - Entity authentication and digital signatures.


