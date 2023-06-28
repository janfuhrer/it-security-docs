tags: #symmetric #hash

# Cryptographic Hash Functions

links: [[themes/106 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

## MD5

- applying the [[Hash Functions#Davies-Meyer|Davies-Meyer]] & [[Hash Functions#Merkle-Damgård Transform|Merkle-Damgård Transform]] construction
- not secure anymore, a collision can be found under one minute
- 128-bit output length

## SHA

- *Secure Hash Algorithms* (SHA) refers to a set of cryptographic hash functions standardized by NIST

### SHA-1
- applying the [[Hash Functions#Davies-Meyer|Davies-Meyer]] & [[Hash Functions#Merkle-Damgård Transform|Merkle-Damgård Transform]] construction
- 160-bit output length
- collisions was found, not recommended anymore

### SHA-2

- applying the [[Hash Functions#Davies-Meyer|Davies-Meyer]] & [[Hash Functions#Merkle-Damgård Transform|Merkle-Damgård Transform]] construction
- hash family with two related hash functions: SHA-256 and SHA-512
- 256- or 512-bit output length
- currently appear to be save and thus recommended when collision-resistant hashing is needed

### SHA-3

- applying the [[Keccak]] (Sponge) construction
- released in 2015, supports 224-, 256-, 384- & 512-bit output lengths
- also recommended

---
links: [[themes/106 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]