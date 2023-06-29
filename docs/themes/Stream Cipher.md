tags: #symmetric

# Stream Cipher

links: [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

The output bits of a stream cipher are produced gradually and on demand, so that an application can request exactly as many pseudorandom bits as its needs.

## Stream cipher with pseudorandom generator

A secure stream cipher *without* an IV is just a pseudorandom generator with a more flexible interface.
- $s$: seed/key
- $l$: length

$G^l(s) := GetBits_1(Init(s), 1^l)$

## Stream cipher with pseudorandom function

Using different values for the $IV$ should produce output streams that appear independently uniform. Practical stream ciphers typically do not support arbitrary values of $n$ (which determines the length of the seed and the IV), but instead work only for some fixed values of $n$.

$F_s^l(IV) := GetBits_1(Init(s, IV), 1^l)$

**Example Output of a stream cipher**

$F_s(IV \parallel \langle 0 \rangle),F_s(IV \parallel \langle 1 \rangle), ...$

## Modes of Operation

### Synchronized mode

Stateful encryption where the sender and receiver are required to maintain state between the encryption/decryption of different messages. Does not need to use an IV.

### Unsynchronized mode

When a stream cipher does take an IV, it can be used to construct a **stateless encryption scheme**. The main advantage here is that the encryption scheme directly handles arbitrary-length messages.


---
links: [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]