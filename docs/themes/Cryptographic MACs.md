tags: #symmetric #mac

# Cryptographic MACs

links: [[themes/106 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

## MAC based on Blockcipher

### CBC-MAC

#### CBC-MAC for fixed-length messages

in compare with [[Block Cipher#Cipher Block Chaining (CBC) mode|CBC mode of operation]]:
- no IV
- only output of last tag (no intermediate output)

> is only secure for "fixed-length" messages (see [[themes/Hash-and-Mac#Length-Extension Attack|Lenght-Extension Attack]])

![[cbc_mac.png]]

#### CBC-MAC for arbitrary-length messages

- one solution is to include the length of the message in the first block
- has been proven secure as long as no two messages that are prefixes of each other are ever used
- **Drawback**: requires a number of cryptographic operations (specifically, block-cipher evaluations) *linear* in the length of the message being authenticated $\rightarrow$ **not efficient**

![[cbc_mac_2.png]]


### GMAC (Galois Message Authentication Code)

- GMAC is an specialization of the [[Authenticated Encryption#GCM (Galois/ counter mode)|GCM (Galois/Counter mode)]] for authentication only
- very efficient by using hardware-level instructions (more efficient and secure than CBC-MAC)

### Poly1305

- Universal hash family designed by Bernstein
- more efficient and secure than CBC-MAC

### GMAC vs. Poly1305

> The main difference between Poly1305-AES and AES-GMAC is the type of arithmetic used by the underlying universal hash family, Poly1305 or GHASH, respectively.

Poly1305 is optimized for fast safe software implementations, whereas GHASH is a security risk unless you can guarantee you're using hardware support.

Source: [Link](https://crypto.stackexchange.com/questions/43112/poly1305-aes-vs-aes-gcm#:~:text=The%20main%20difference%20between%20Poly1305,software%20without%20timing%20side%20channels.)

## MAC based on Hash-and-MAC

### HMAC (Hash-based Message Authentication Code)

- based on the [[Hash-and-Mac]] construct
- Avoids the [[Hash-and-Mac#Length-Extension Attack|Length-Extension Attack]]
- uses the [[Hash Functions#Merkle-Damgård Transform|Merkle-Damgård]] transform to compress arbitrary-length messages
- there is an "inner" and an "outer" hash evaluation with some fixed constants (ipad/opad)
- **Definition**: "*HMAC-Hash*"" (e.g. HMAC-SHA-256, HAMC-SHA3-512)
- **Security**: HMAC is secure as long as you choose a secure hash algorithm (e.g. HMAC-SHA3-256)

![[hmac.png]]

## MAC based on Blockcipher vs. based on Hash-and-MAC

> With Hash-and-MAC (like HMAC) we typically use conjecturally collision-resistant functions like SHA-256, which are orders of magnitude more expensive to compute for conjectured security that we don't even care about in this application (collision resistance).

Source: [Link](https://crypto.stackexchange.com/a/67639)

## MAC based on Sponge Functions

### KMAC (Keccak Message Authentication Code

- KMAC is a PRF and [[Hash Functions#Keyed hash functions|keyed hash function]] based on [[Keccak]]
- two variants KMAC128 and KMAC256, built from cSHAKE128 and cSHAKE256 respectively
- KMAC can also be used as a XOF, which mimics the behavior of cSHAKE

---
links: [[themes/106 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]
