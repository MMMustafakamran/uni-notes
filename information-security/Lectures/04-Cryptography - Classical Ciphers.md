### Lecture 04 – Cryptography: Classical Ciphers (Summary Notes)

---

### 1. Symmetric Key & Classical Ciphers

- **Symmetric key cryptography**: Same secret key for encryption and decryption: \( C = E_K(P),\ P = D_K(C) \).
- **Alphabet mapping**: A–Z → 0–25, all arithmetic mod 26.
- **Classical ciphers**: Early symmetric ciphers operating on letters (not bits); useful for learning but insecure today.

---

### 2. Substitution Ciphers

General idea: Replace each plaintext letter with another letter.

#### 2.1 ROT-13
- **Definition**: Special Caesar cipher with fixed shift of 13.
- **Formula**: \( C = (p + 13) \bmod 26 \); applying ROT-13 twice returns the original text.
- **Security**: Trivial; only used for obfuscation.

#### 2.2 Caesar Cipher
- **Definition**: Shift each letter by constant integer \( k \) (typically \( k = 3 \)).
- **Formulas**:
  - Encryption: \( C = (p + k) \bmod 26 \).
  - Decryption: \( P = (c - k) \bmod 26 \).
- **Key space**: Only 25 possible non-trivial shifts → easily broken by brute-force and frequency analysis.

#### 2.3 Affine Cipher
- **Definition**: Generalizes Caesar using linear function on letter indices.
- **Formulas** (with \( m = 26 \)):
  - Encryption: \( E(x) = (a x + b) \bmod m \).
  - Decryption: \( D(x) = a^{-1} (x - b) \bmod m \), where \( a^{-1} \) satisfies \( a a^{-1} \equiv 1 \pmod{m} \).
- **Key condition**: \( \gcd(a, 26) = 1 \) so that \( a^{-1} \) exists.
- **Security**: Still monoalphabetic; broken by frequency analysis and a few known plaintexts.

#### 2.4 Vigenère Cipher
- **Idea**: Use a **repeating keyword** → sequence of shifts instead of one fixed shift.
- **Key**: Keyword letters mapped to numbers \( k_i \), repeated over the plaintext.
- **Formulas**:
  - Encryption: \( C_i = (p_i + k_i) \bmod 26 \).
  - Decryption: \( P_i = (c_i - k_i) \bmod 26 \).
- **Historical view**: Once called “unbreakable,” but broken using Kasiski tests and index of coincidence to find key length, then frequency analysis on each position.

---

### 3. Transposition Ciphers

General idea: **Reorder** the letters without changing them.

#### 3.1 Rail Fence Cipher
- **Concept**: Write plaintext in a zigzag over multiple “rails” and read off row by row.
- **Example (2 rails)**: Zigzag down/up between two rows, then concatenate rows → ciphertext.
- **Decryption**: Reconstruct zigzag pattern knowing number of rails and message length.

#### 3.2 Columnar Transposition
- **Steps**:
  1. Choose keyword; label columns by the letters of the key.
  2. Write plaintext row-wise under the key.
  3. Determine column order by sorting key letters alphabetically.
  4. Read columns in that order to form ciphertext.
- **Decryption**: Reverse process—fill columns in sorted order and read rows.

---

### 4. Cryptanalysis & Security Concepts

- **Cryptanalysis**: Study of breaking ciphers or recovering keys.
  - Attack models: ciphertext-only, known-plaintext, chosen-plaintext, chosen-ciphertext.
- **Frequency analysis**:
  - English letters have known frequencies (e.g., E most common).
  - Simple substitution ciphers (Caesar, Affine) preserve frequency patterns → easy to break.
- **Security definitions**:
  - **Unconditionally secure**: Ciphertext gives insufficient info to determine plaintext even with infinite computation (e.g., one-time pad).
  - **Computationally secure**: Breaking requires infeasible resources with current technology.
  - Classical ciphers are **not** computationally secure today.

---

### 5. Why Classical Ciphers Are Insecure & Their Role Today

- **Weaknesses**:
  - Tiny key spaces (e.g., 25 keys for Caesar).
  - Preserve language structure and letter frequencies.
  - Well-known analytic attacks (frequency analysis, Kasiski, index of coincidence).
- **Role in learning**:
  - Introduce key concepts: modulo arithmetic, invertible transformations, key spaces, and cryptanalysis basics.
  - Provide intuition for modern symmetric ciphers (confusion and diffusion) but must **not** be used for real security.


