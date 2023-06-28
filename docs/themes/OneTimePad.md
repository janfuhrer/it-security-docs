tags: #symmetric 

# OneTimePad

links:  [[102 AC1 TOC - Security & Cryptography|AC1 TOC - Security & Cryptography]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

## General definition

- the key is as long as the message (and also the ciphertext has the same length)
- the OneTimePad is only secure if used once (with a given key)

## Using OneTimePad twice

Adversary can learn the $XOR$ of the two messages (where they differ) if a OneTimePad (key) is used twice:
$c \oplus c' = (m \oplus k)\oplus (m' \oplus k) = m \oplus m'$

## Limitations of Perfect Secrecy

Any perfectly secret encryption scheme must have a key space that is at least as large as the message space: $|K|\geq|M|$

---

## Definitions

- XOR (bitwise exclusive-or): $a \oplus b$

| XOR | 0 | 1 |
|-----|----|---|
| 0      | 0 | 1 |
| 1       | 1 | 0 |


---
links:  [[102 AC1 TOC - Security & Cryptography|AC1 TOC - Security & Cryptography]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]