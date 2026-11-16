### Lecture 05 – Data Encryption Standard (DES) (Summary Notes)

---

### 1. DES at a Glance

- **Type**: Symmetric block cipher, Feistel network.
- **Block size**: 64 bits.
- **Key**: 64‑bit input key with 8 parity bits → **56‑bit effective key**.
- **Rounds**: 16 Feistel rounds.
- **Status**: Historically important but **insecure today** due to short key length; replaced by AES.

---

### 2. Feistel Structure and Round Equations

- After initial permutation (IP), the block is split:
  - \( L_0 \), \( R_0 \) each 32 bits.
- For each round \( i = 1..16 \):
  - \( L_i = R_{i-1} \)
  - \( R_i = L_{i-1} \oplus f(R_{i-1}, K_i) \)
- After 16 rounds:
  - Swap halves → \( R_{16} \| L_{16} \).
  - Apply final permutation (FP) = \( IP^{-1} \) → ciphertext.
- **Decryption**: same equations, keys in **reverse order** \( K_{16}..K_1 \).

---

### 3. Round Function \( f(R_{i-1}, K_i) \)

Steps:
1. **Expansion E**:
   - Expand 32‑bit \( R_{i-1} \) to 48 bits using a fixed table (some bits repeated).
2. **Key mixing**:
   - XOR with 48‑bit round key: \( X = E(R_{i-1}) \oplus K_i \).
3. **S‑boxes (substitution)**:
   - Split X into eight 6‑bit pieces.
   - Each 6‑bit input goes through one S‑box (S1..S8) → 4‑bit output.
   - Concatenate 8 outputs → 32 bits.
4. **Permutation P**:
   - Permute the 32 bits via table P to diffuse S‑box outputs.

Result: 32‑bit output used in \( R_i = L_{i-1} \oplus f(\cdot) \).

---

### 4. Key Schedule (Round Keys)

- Start from 64‑bit key:
  - Apply **PC‑1** → select 56 bits and permute → \( C_0 \), \( D_0 \) (each 28 bits).
- For each round \( i = 1..16 \):
  - Left‑rotate \( C_{i-1} \), \( D_{i-1} \) by 1 or 2 bits (fixed schedule) → \( C_i, D_i \).
  - Apply **PC‑2** to \( C_i \| D_i \) → select 48 bits = **round key \( K_i \)**.
- Produces 16 round keys \( K_1..K_{16} \).

---

### 5. Modes of Use (Mentioned)

- DES is a block primitive; common modes:
  - **ECB**: each block encrypted independently (pattern leaks).
  - **CBC**: XOR with previous ciphertext block, uses IV.
  - **CFB / OFB / CTR**: turn DES into a stream‑like cipher.

---

### 6. Security and Successor Algorithms

- **Weaknesses**:
  - 56‑bit key → feasible **brute‑force** with modern hardware.
  - Susceptible to advanced cryptanalysis (differential / linear) on reduced rounds.
- **Triple DES (3DES)**:
  - EDE structure with 2 or 3 keys to extend effective key length.
  - More secure than DES but slower than AES; also being phased out.
- **Replacement by AES**:
  - Need for larger keys (128/192/256 bits), better performance, and stronger security guarantees.


