# AES

## Definition
The Advanced Encryption Standard (AES) is a symmetric block cipher chosen by the U.S. National Institute of Standards and Technology (NIST) in 2001. Based on the Rijndael cipher designed by Joan Daemen and Vincent Rijmen, AES encrypts data in 128-bit blocks using 128, 192, or 256-bit keys. It is the world's most widely used symmetric encryption algorithm.

## Why It Matters
AES is the encryption standard for virtually all modern security systems. It protects data in TLS/HTTPS (web traffic), Wi-Fi (WPA2/WPA3), disk encryption (BitLocker, FileVault, LUKS), file encryption (WinZip, 7-Zip), VPNs (WireGuard, OpenVPN), and government classified information (AES-256 is approved for TOP SECRET data). Understanding AES is essential for evaluating encryption strength, correctly implementing modes of operation, and conducting cryptanalysis.

## Where It Appears in the Path
AES is covered in the cryptography module. It is prerequisite for understanding TLS/HTTPS, wireless security (WPA2/AES-CCMP, WPA3/AES-GCM), full-disk encryption, and secure protocol design.

## Prerequisites
- Cryptography fundamentals (symmetric encryption)
- Understanding of binary/hexadecimal representation

## AES Specifications
- **Block Size**: 128 bits (16 bytes)
- **Key Sizes**: 128, 192, or 256 bits
- **Rounds**: 10 (AES-128), 12 (AES-192), 14 (AES-256)
- **Structure**: Substitution-permutation network (not Feistel)

## AES Internals
Each round (except the last) performs four transformations:
1. **SubBytes (Substitution)**: Each byte is replaced using a fixed S-box (substitution box). S-box is a 16×16 lookup table based on multiplicative inverse in GF(2^8) and affine transformation.
2. **ShiftRows (Permutation)**: Bytes in each row of the state are shifted cyclically. Row 0 unchanged, row 1 shifted left by 1, row 2 by 2, row 3 by 3.
3. **MixColumns (Diffusion)**: Each column is multiplied by a fixed polynomial modulo x^4 + 1. Provides diffusion across columns. Omitted in the final round.
4. **AddRoundKey**: The round key (derived from the cipher key via key expansion) is XORed with the state.

## Security
- **AES-128**: 128-bit security. Brute-force search of 2^128 keys is infeasible with any foreseeable technology.
- **AES-192**: 192-bit security.
- **AES-256**: 256-bit security. Required for TOP SECRET government data.

No practical attacks exist against the full AES algorithm. Related-key attacks exist against AES-256 (not practical in real usage). Side-channel attacks (timing, cache, power) target implementations, not the algorithm itself.

## Block Cipher Modes
AES alone encrypts only 16-byte blocks. Modes handle messages of arbitrary length:

### ECB (Electronic Codebook)
Each 16-byte block encrypted independently. **Insecure** — identical plaintext blocks produce identical ciphertext blocks, leaking patterns. Never use ECB.

### CBC (Cipher Block Chaining)
Each plaintext block is XORed with the previous ciphertext block before encryption. Requires an initialization vector (IV) — random, unique per encryption. Vulnerable to padding oracle attacks.

### CTR (Counter)
Turns AES into a stream cipher by encrypting sequential counter values and XORing with plaintext. Parallelizable. Requires unique nonce per key. No padding needed.

### GCM (Galois/Counter Mode)
CTR mode + GMAC authentication tag. Provides authenticated encryption (confidentiality + integrity). The most commonly used mode in TLS 1.2/1.3, WPA3, SSH. Requires unique IV/nonce per key — nonce reuse is catastrophic.

### CCM (Counter with CBC-MAC)
Combines CTR for encryption and CBC-MAC for authentication. Used in WPA2 (AES-CCMP). Simpler than GCM but slower.

### XTS (XEX-based Tweaked CodeBook mode)
Used for disk encryption (BitLocker, LUKS). Allows random access (encrypt/decrypt individual blocks) without leaking patterns. Uses two keys (one for encryption, one for tweak).

## Key Size Considerations
| Key Size | Rounds | Security Level | Use Case |
|----------|--------|----------------|----------|
| AES-128 | 10 | 128 bits | Standard security (TLS, VPN, Wi-Fi) |
| AES-192 | 12 | 192 bits | Higher security |
| AES-256 | 14 | 256 bits | Maximum security (classified data) |

AES-256 provides more security margin against quantum attacks (Grover's search reduces effective security to half the key size: AES-256 → 128-bit post-quantum security).

## Side-Channel Attacks
AES implementations can leak information through:
- **Timing**: Observable differences in execution time based on key or data. Mitigated by constant-time implementation.
- **Cache**: Cache-timing attacks like Prime+Probe on S-box lookups. Mitigated by hardware AES instructions (AES-NI) or bitsliced implementations.
- **Power**: Differential Power Analysis (DPA) measures power consumption during encryption. Mitigated by masking.

Hardware AES instructions (AES-NI, ARMv8 Crypto Extensions) are constant-time and resistant to cache and timing side channels.

## Common Interview Questions
1. **What is AES and why is it secure?** AES is a symmetric block cipher based on a substitution-permutation network. Secure due to its large key space (10^38 for AES-128) and resistance to known cryptanalytic attacks.
2. **What is the difference between AES-128 and AES-256?** Key size: 128 vs 256 bits. Rounds: 10 vs 14. Security: 128-bit vs 256-bit security. AES-256 is quantum-resistant (Grover's search reduces to 128-bit security).
3. **Why is ECB mode insecure?** Identical plaintext blocks produce identical ciphertext blocks, leaking data patterns (e.g., the "ECB penguin" test image).
4. **What is the difference between CBC and GCM?** CBC provides only confidentiality. GCM provides both confidentiality and integrity (authenticated encryption). GCM is parallelizable; CBC is not.
5. **What happens if you reuse a nonce/IV in GCM mode?** The security completely breaks — an attacker can recover the authentication key (for forgery) and XOR the keystream to decrypt data.
6. **How does AES-GCM differ from AES-CCM?** Both are authenticated encryption. GCM uses CTR + GHASH (faster with hardware support). CCM uses CTR + CBC-MAC (simpler, slower, no parallelization).

## Further Reading
- [NIST FIPS 197 — Advanced Encryption Standard](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf)
- [NIST SP 800-38A — Block Cipher Modes](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-38a.pdf)
- [NIST SP 800-38D — GCM Mode](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-38d.pdf)
- _Understanding Cryptography_ by Paar and Pelzl
- [AES Visual (animations)](https://agardner.net/aes/)
- [AES-GCM Nonce Reuse Catastrophe](https://www.usenix.org/conference/usenixsecurity21/presentation/garner)
