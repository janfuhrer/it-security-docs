tags: #symmetric
links:  [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---
# Block Cipher

> A block cipher is simply another name for a (strong) pseudorandom permutation.

That is, a block cipher $F : \{0, 1\}^n \times \{0, 1\}^l \rightarrow \{0, 1\}^l$ is a keyed function, $n$ is the key length of F and $l$ is the block length.
The main distinction between block ciphers and pseudorandom permutations is that the former typically only support a specific set of key/block lengths and do not support arbitrary-length keys.

### Electronic Code Block (ECB) mode

- direct application of the block cipher
- ECB mode is deterministic and therefore cannot be CPA secure
- not even EAV secure $\rightarrow$ should never be used!

![[ecb_mode.png]]

### Cipher Block Chaining (CBC) mode

- randomized through IV
- Unsynchronized mode (stateless)
- CPA secure
- not parallel encryption/decryption

![[cbc_mode.png]]

### Chained CBC mode

- last block of the previous ciphertext is used as the IV $\rightarrow$ reduces bandwith
- **synchronized mode** (stateful)
- not CPA secure

![[cbc-chained_mode.png]]

### Output Feedback (OFB) mode

- Unsynchronized mode (stateless)
- Pseudorandom stream is independent
- No need of $F_k^{-1}$
- not necessary for the plaintext length to be a multiple of the block length $n$
- CPA secure

![[ofb_mode.png]]

### Counter (CTR) mode

- Unsynchronized mode (stateless)
- Parallel encryption & decryption
- the blocks of the pseudorandom stream can be computed independently of each other
- CPA secure

![[ctr_mode.png]]

### Practical Considerations

**Block length and concrete security**

If the block length $n$ is too short, then the resulting concrete-security bound will be too weak for practical applications. Since the IV is a uniform string of length $3n/4$, an IV will repeat after some time. The the smaller $n$, the faster the IV is repeated. But if $n$ is too large, the concrete-security will also decrease.

**IV misuse**

A repeated IV can be catastrophic: it implies that the entire pseudorandom stream is repeated, which means that by XORing the two ciphertexts using the same IV reveals the XOR of the underlying plaintexts.

### Nonce-Based Encryption

The encryption and decryption algorithms additionally accept a *nonce* as input.
A **nonce** refers to a value that is supposed to be **used once, and never repeated**.

**Difference between IV**

- instead of using an IV, wich is chosen uniformly, use a nonce
- **repeat cannot occur** (assumption that the application using the encryption scheme ensures that nonces never repeat)
- nonce-based encryption scheme can be CPA-secure even though it is deterministic

**Advantages**

- in settings where generating high-quality randomness is expensive or impossible, it may be much easier to use a counter as a nonce rather than to generate a nonce uniformly.


---
links:  [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]