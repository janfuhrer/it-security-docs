tags: #symmetric 
links:  [[Topic 2 - Security]], [[030 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---
# OneTimePad

- the key is as long as the message
- the OneTimePad is only secure if used once (with a given key)

#### Using OneTimePad twice

Adversary can learn the $XOR$ of the two messages (where they differ):
$c \oplus c' = (m \oplus k)\oplus (m' \oplus k) = m \oplus m'$

#### Limitations of Perfect Secrecy

Any perfectly secret encryption scheme must have a key space that is at least as large as the message space: $|K|\geq|M|$

### Shannon's Theorem

Shannon provided a characterization of perfectly secret encryption schemes.

> We have an encryption scheme with $|M| = |K| = |C|$, the scheme is perfectly secret iff:
> 	1. Every key $k \in K$ is chosen with equal probability $1/|K|$ by $Gen$
> 	2. For every $m \in M$ and every $c \in C$, there is a unique key $k \in K$ such that $Enc_k(m)$ outputs $c$

---

### Definitions

- XOR (bitwise exclusive-or): $a \oplus b$
 - **Message space**: set of all possible messages: $M$

---
links:  [[Topic 2 - Security]], [[030 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]