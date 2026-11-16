### Lecture 11 – PKI, Hashing, and Digital Signatures (Summary Notes)

---

### 1. PKI (Public Key Infrastructure)

- **Goal**: Manage public keys and bind them to real-world identities.
- **Components**:
  - End-entities (subjects) with key pairs.
  - Certificate Authorities (CAs) that issue and sign certificates.
  - Registration Authorities (RAs) that verify identities.
  - Repositories for certificates and revocation data (CRL/OCSP).
- **Certificates**:
  - Contain subject, public key, validity, issuer, and CA signature.
  - Verified via a chain of trust up to a trusted root CA.

---

### 2. Cryptographic Hash Functions

- Map arbitrary-length input to fixed-length output \( h = H(M) \).
- **Security properties**:
  - Pre-image, second pre-image, and collision resistance.
- **Uses**:
  - Integrity checks (comparing hashes).
  - Password storage (hash + salt).
  - Input to digital signatures (sign the hash, not entire message).

---

### 3. Digital Signatures (Concept)

- **Signing** (e.g., RSA):
  1. Compute hash \( h = H(M) \).
  2. Compute signature \( S = h^d \bmod n \) using private key \( d \).
- **Verification**:
  1. Compute \( h' = H(M) \).
  2. Compute \( h_v = S^e \bmod n \) with public key \( e \).
  3. Accept if \( h_v = h' \).
- **Properties**:
  - Integrity: any change in M breaks verification.
  - Authentication: only private key holder can sign.
  - Non‑repudiation: signer cannot easily deny valid signatures.

---

### 4. MAC / HMAC vs Digital Signatures

- **MAC / HMAC**:
  - Integrity + authentication using shared secret key.
  - Faster than signatures; good for ongoing communication.
  - No non‑repudiation (any party with the key can forge MACs).
- **Digital signatures**:
  - Use asymmetric keys; verifiable by anyone with public key.
  - Provide non‑repudiation.

---

### 5. Use in Protocols (e.g., HTTPS/TLS)

- Server proves identity with CA-signed certificate (PKI).
- Client verifies certificate (signature, validity, revocation).
- Key exchange (RSA or Diffie–Hellman) sets up symmetric session keys.
- Data is then protected with:
  - Symmetric encryption (e.g., AES).
  - Integrity via MAC/HMAC or authenticated encryption modes.


