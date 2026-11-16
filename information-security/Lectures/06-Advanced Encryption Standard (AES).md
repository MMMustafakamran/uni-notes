### Lecture 06 – Advanced Encryption Standard (AES) (Summary Notes)

---

### 1. AES Basics

- **Type**: Symmetric block cipher, Substitution–Permutation Network (SPN).
- **Block size**: 128 bits.
- **Key sizes / rounds**:
  - 128‑bit key → 10 rounds.
  - 192‑bit key → 12 rounds.
  - 256‑bit key → 14 rounds.
- **State**: 128‑bit block viewed as 4×4 matrix of bytes.

---

### 2. Overall Encryption Structure

- **Key Expansion**: Original key expanded into multiple **round keys** (round 0..N).
- **Initial step**:
  - **AddRoundKey** with round 0 key.
- **Rounds 1 to N−1** (middle rounds):
  1. **SubBytes** – Nonlinear S‑box applied bytewise.
  2. **ShiftRows** – Cyclic left shift of each row (0,1,2,3 bytes).
  3. **MixColumns** – Linear mixing of columns in GF(2⁸).
  4. **AddRoundKey** – XOR with current round key.
- **Final round** (round N):
  - SubBytes → ShiftRows → AddRoundKey (no MixColumns).

---

### 3. Round Operations in More Detail

- **AddRoundKey**:
  - XOR state with round key; ties encryption directly to the key.
- **SubBytes**:
  - Uses fixed 16×16 S‑box.
  - Provides **confusion** (non-linearity against cryptanalysis).
- **ShiftRows**:
  - Shifts rows by 0,1,2,3 bytes.
  - Spreads bytes across columns for **diffusion**.
- **MixColumns**:
  - Multiplies each column by a fixed matrix over GF(2⁸), using polynomial \(x^8 + x^4 + x^3 + x + 1\).
  - Mixes bits inside each column, further increasing diffusion.

---

### 4. Decryption (High Level)

- Uses **inverse** operations:
  - InvSubBytes, InvShiftRows, InvMixColumns, AddRoundKey.
- Round keys are applied in **reverse order**.
- Because operations are invertible, decryption reverses the encryption steps.

---

### 5. AES vs DES and Security

- Compared to DES:
  - Larger block (128 vs 64 bits).
  - Much larger keys (128/192/256 vs 56 bits).
  - SPN structure instead of Feistel.
- **Security**:
  - No practical attacks on full AES for standard key sizes.
  - 128‑bit+ keys are safe from brute-force with current technology.
- **Performance**:
  - Efficient in software and hardware, widely implemented and accelerated.


