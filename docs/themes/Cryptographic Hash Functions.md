tags: #symmetric #hash

# Cryptographic Hash Functions

links: [[105 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

## MD5

- applying the [[Hash Functions#Davies-Meyer|Davies-Meyer]] & [[Hash Functions#Merkle-Damgård Transform|Merkle-Damgård Transform]] construction
- not secure anymore, a collision can be found under one minute
- 128-bit output length
- is prone to [[Hash-and-Mac#Length-Extension Attack|length-extension attacks]]

## SHA

*Secure Hash Algorithms* (SHA) refers to a set of cryptographic hash functions standardized by NIST.

### SHA-1

- applying the [[Hash Functions#Davies-Meyer|Davies-Meyer]] & [[Hash Functions#Merkle-Damgård Transform|Merkle-Damgård Transform]] construction
- 160-bit output length
- collisions was found, not recommended anymore
- see attack [SHAttered](https://shattered.io/)
- is prone to [[Hash-and-Mac#Length-Extension Attack|length-extension attacks]]

### SHA-2

- applying the [[Hash Functions#Davies-Meyer|Davies-Meyer]] & [[Hash Functions#Merkle-Damgård Transform|Merkle-Damgård Transform]] construction
- hash family with following hash functions: SHA-224, SHA-256, SHA-384, SHA-512, SHA-512/224, SHA-512/256
- currently appear to be save and thus recommended when collision-resistant hashing is needed (output length 224 is not recommended anymore)
- SHA-256 and SHA-512 are prone to [[Hash-and-Mac#Length-Extension Attack|length-extension attacks]]

### SHA-3

- SHA-3 Standard defines:
	- four fixed-length hash functions: SHA3-224, SHA3-256, SHA3-384, SHA3-512
	- two extendable Output Functions (XOFs): SHAKE128 and SHAKE256 (see [[SHAKE & cSHAKE]])
- applying the [[Keccak]] (Sponge) construction
- also recommended


### Security Strengths in Bits

![[security_of_sha_functions.png]]

## BLAKE

> BLAKE is a cryptographic hash function based on Bernsteins [[Authenticated Encryption#ChaCha20-Poly1305|ChaCha]] stream cipher.

There are like in the SHA family several versions of the hash function:

- **BLAKE**: submitted 2008, lost in final round of SHA-3 competition to [[Keccak]]
- **BLAKE2**: hash function based on BLAKE (2012), *BLAKE2b* is faster than MD5, SHA-1, SHA-2 & SHA-3
- **BLAKE3**: hash function based on BLAKE2 (2020), single algorithm with many desirable features (parallelism, XOF, [[Key Derivation Function (KDF)|KDF]], [[CPA-Security#Pseudorandom Functions and Permutations|PRF]] and [[MAC]]), faster than BLAKE2

- Users of BLAKE2: [[Password Based Key Derivation Function (PBKDF)#PBKDF using Argon2|Argon2]], Wireguard, ...

Source [en: Wikpedia](https://en.wikipedia.org/wiki/BLAKE_(hash_function))

---
links: [[105 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]