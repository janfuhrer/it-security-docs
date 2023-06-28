tags: #symmetric #mac

# Cryptographic MACs

links: [[themes/106 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

### CBC-MAC

in compare with [[Block Cipher#Cipher Block Chaining (CBC) mode|CBC mode of operation]]:
- no IV
- only output of last tag (no intermediate output)

![[cbc_mac.png]]

**CBC-MAC for arbitrary-length messages**

![[cbc_mac_2.png]]


## GMAC (Galois Message Authentication Code)

-  GMAC is an specialization of the GCM (Galois/Counter mode) and used for authentication.


## HMAC (Hash-based Message Authentication Code)

- based on the [[Hash-and-Mac]] construct
- Avoids the [[Hash-and-Mac#Length-Extension Attack|Length-Extension Attack]]
- uses the [[Hash Functions#Merkle-Damgård Transform|Merkle-Damgård]] transform to compress arbitrary-length messages
- there is an "inner" and an "outer" hash evaluation with some fixed constants (ipad/opad) 

![[hmac.png]]


## KMAC (Keccak Message Authentication Code

- KMAC is a PRF and [[Hash Functions#Keyed hash functions|keyed hash function]] based on [[Keccak]]
- two variants KMAC128 and KMAC256, built from cSHAKE128 and cSHAKE256 respectively
- KMAC can also be used as a XOF, which mimics the behavior of cSHAKE

## Poly1305

- 

---
links: [[themes/106 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]]]
