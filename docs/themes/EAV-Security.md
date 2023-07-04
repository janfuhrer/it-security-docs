tags: #symmetric #EAV

# EAV-Security

links: [[104 AC1 TOC - Private Key Encryption|AC1 TOC - Private Key Encryption]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

## General definition

EAV-security implies that ciphertexts leak no information about individual bits of the plaintext.

> A private-key encryption scheme has *indistinguishable encryptions in the presence of an eavesdropper*, or is is **EAV-Secure**, iff it is **semantically secure** in the presence of an eavesdropper.

**Leaking the plaintext length**

The default notion of secure encryption does not require the encryption scheme to hide the plaintext length. Sometimes, leaking the plaintext length is problematic:
- *Simple numeric/text data*: Encryption of "yes/no" responses would leak the answer exactly
- *Database searches*: the number of records returned can reveal information about what the user was searching for.
- *Compressed data*: if the plaintext is compressed before being encrypted, then information about the plaintext might be revealed (e.g. that the original plaintext has a lot of redundancy)

Mitigate or prevent such leakage by padding all messages before encrypting them.

## Semantic Security

- takes into account that arbitrary "external" information about the message may be available to the adversary
- allows messages of varying lengths
- assumes the message length is revealed

A semantically secure cryptosystem (RSA, ElGamal) is one where only negligible information about the plaintext can be feasibly extracted from the ciphertext.

Perfect secrecy (see [[themes/Shannons Theorem|Shannons Theorem]]) means that the ciphertext reveals no information at all about the plaintext, whereas semantic security implies that any information revealed cannot be feasibly extracted.

## Constructing an EAV-Secure Encryption Scheme

### Pseudorandom Generators

> deterministic algorithm $G$ for transforming a short, uniform string (called **seed**) into a longer, "uniform-looking" (or "pseudorandom") output string.

Just as indistinguishability is a computational relaxation of perfect secrecy, pseudorandomness is a computational relaxation of true randomness.

**Formal definition**

$G$ is a pseudorandom generator if no efficient distinguisher can detect whether it is given a string output by $G$ or a string chosen uniformly at random.

**Seed**

- must be chosen uniformly and be kept secret from any adversary if we want $G(s)$ to look random
- the seed $s$ must at least be large enough so that a brute-force attack running in time $2^n$ is infeasible

### Proofs by Reduction

Our strategy will be to assume that some mathematical problem is hard, or that some low-level cryptographic primitive is secure, and then to prove that the given construction based on that problem/primitive is secure as long as our initial assumption is correct.

![[proof_by-reduction.png]]

### EAV-Security from a Pseudorandom Generator

Rather than sharing this long, pseudorandom pad, the sender and receiver can instead share a uniform seed that is used to generate the pad when needed.

- only for fixed length pad & messages
- only EAV-Secure

![[eav_with_prng.png]]

---
links: [[104 AC1 TOC - Private Key Encryption|AC1 TOC - Private Key Encryption]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]