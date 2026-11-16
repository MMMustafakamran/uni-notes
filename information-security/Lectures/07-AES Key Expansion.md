### Lecture 07 – AES Key Expansion (Summary Notes)

---

### 1. Purpose and Parameters

- **Goal**: Expand a short cipher key into many **round keys** for AES rounds.
- **Definitions**:
  - **Word**: 32 bits (4 bytes).
  - **\(N_b\)**: Number of words in block (always 4 for AES-128).
  - **\(N_k\)**: Number of words in cipher key.
  - **\(N_r\)**: Number of rounds.
- For AES-128: \( N_k = 4, N_r = 10 \) → total words \( N_b (N_r+1) = 44 \).

---

### 2. Key Expansion Output

- Produces array \( W[0..N_b(N_r+1)-1] \) of 32-bit words.
- Round keys:
  - Round 0 key: \( W[0..3] \).
  - Round 1 key: \( W[4..7] \).
  - ...
  - Final round key: last 4 words.

---

### 3. Core Recurrence (AES-128)

- Initialize:
  - \( W[0..3] \) are directly from the 16-byte original key.
- For each word \( i \ge N_k \):
  - If \( i \bmod N_k \ne 0 \):
    - \( W[i] = W[i-1] \oplus W[i-N_k] \).
  - If \( i \bmod N_k = 0 \):
    - \( W[i] = \text{SubWord}(\text{RotWord}(W[i-1])) \oplus Rcon[i/N_k] \oplus W[i-N_k] \).

---

### 4. Building Blocks

- **RotWord**:
  - Rotates a 4-byte word left by one byte: \([b_0,b_1,b_2,b_3] \to [b_1,b_2,b_3,b_0]\).
- **SubWord**:
  - Applies AES S-box to each of the 4 bytes in a word (same S-box as SubBytes).
- **Rcon**:
  - Array of round constants; 32-bit words of the form \((r,0,0,0)\).
  - \( r \) doubles in GF(2⁸) each round (1,2,4,8,...).
  - Breaks symmetry and ensures unique round keys.

---

### 5. Generalization to AES-192 and AES-256

- **AES-192**: \( N_k = 6, N_r = 12 \).
  - Similar recurrence with \( i \bmod 6 = 0 \) using RotWord, SubWord, Rcon.
- **AES-256**: \( N_k = 8, N_r = 14 \).
  - If \( i \bmod 8 = 0 \): use RotWord, SubWord, Rcon.
  - If \( i \bmod 8 = 4 \): apply SubWord (no RotWord/Rcon).
  - Otherwise: simple XOR recurrence.

---

### 6. Relation to AES Rounds and Security

- **Encryption**:
  - Round 0 uses \( W[0..3] \) (initial AddRoundKey).
  - Each later round uses its own 4-word round key.
- **Decryption**:
  - Uses same round keys in reverse order.
- **Security role**:
  - SubWord and Rcon introduce non-linearity and diversity.
  - Small changes in original key affect many later words and round keys, improving resistance to key-related attacks.


