tags: #symmetric #kdf #key-derivation #high-high-entropy

# Key Derivation Function

links:  [[105 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[themes/000 Index|Index]]

---

## High to High Entropy

KDF (key derivation functions) derive a key from a KDK (key derivation key). This means that a KDF creates a key based on another key. A KDF assumes that the KDK which is supplied as input already possesses high entropy and therefore the KDF must not mess with this and just delegates to underlying [[CPA-Security#Pseudorandom Functions and Permutations|PRF]] (pseudo random functions). For this purpose, KDF leverage [[CPA-Security#Pseudorandom Functions and Permutations|PRF]]. The NIST recommends to use [[Cryptographic MACs#HMAC (Hash-based Message Authentication Code)|HMAC]] or [[Cryptographic MACs#KMAC (Keccak Message Authentication Code)|KMAC]] as underlying [[CPA-Security#Pseudorandom Functions and Permutations|PRF]]. KDF which take high entropy as input can also be termed as key expansion. Key expansion is a subpart of a functioning KDF. You could also define a KDF which take  low entropy and generate a high entropy output from this. For low-high entropy scenarios read about [[Password Based Key Derivation Function (PBKDF)|Password Based Key Derivation Function (PBKDF)|PBKDF]].

NIST Recommendations on KDF: [NIST SP 800-108r1](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-108r1.pdf) 

## KDF using KMAC ([[Keccak|Keccak]])

[[Cryptographic MACs#KMAC (Keccak Message Authentication Code)|KMAC]] (Keccak based Message Authentication Code) is based on the [[Keccak]] sponge construction and therefore can output an arbitrary length of output bits.

The NIST defines a [[Cryptographic MACs#KMAC (Keccak Message Authentication Code)|KMAC]] based KDF as follows:

```
Input: KDK, Context, L, and Label

Process:
	1. If L > 2^1040 − 1, output an error indicator and stop (i.e., skip step 2).
	2. DERIVED KEY = KMAC#(KDK, Context, L, Label).
	
Output: DERIVED KEY (or an error indicator)
```

Where the error condition $L > 2^{1040-1}$ is a limitation by [[Cryptographic MACs#KMAC (Keccak Message Authentication Code)|KMAC]] (Section 6.2 of the [NIST document](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-108r1.pdf#%5B%7B%22num%22%3A139%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22XYZ%22%7D%2C70%2C366%2C0%5D)).

### Parameters

- **KDK**: The key derivation key of which a key shall be derived
- **Context**: Context information for the derived key
- **L**: The desired length of the derived key
- **Label**: "Label can be an encoding of
the characters “KDF” or “KDF4X” in 8-bit ASCII" (quote of the [NIST document](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-108r1.pdf#%5B%7B%22num%22%3A139%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22XYZ%22%7D%2C70%2C366%2C0%5D))

### Limitations

The recommended implementation of the KDF by the NIST assume, that the final length of the derived key is always known (the assumption makes sense, since the key length directly influence the security level). But in theory it would also be possible to create variable length derived keys by using XOF KMAC which would allow this.

---
links:  [[105 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[themes/000 Index|Index]]