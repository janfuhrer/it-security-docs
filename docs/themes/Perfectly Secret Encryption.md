tags: #symmetric

# Perfectly Secret Encryption

links: [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

## Perfect secrecy

For a scheme to be perfectly secret, observing this ciphertext should have no effect on the adversary's knowledge regarding the actual message that was sent.

> The ciphertext reveals nothing about the underlying plaintext

## Perfect indistinguishability

> An encryption scheme is *perfectly indistinguishable* if no adversary can succeed with probability better than $1/2$ (in the indistinguishability experiment)

---

## Definitions

- An Encryption scheme is formally defined with $\Pi = (Gen, Enc, Dec)$
- Encryption algorithm is **probabilistic** (encryption might output a different ciphertext when run multiple times): $c \leftarrow Enc_k(m)$
- Decryption algorithm is **deterministic**: $m := Dec_k(c)$

---
links: [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]