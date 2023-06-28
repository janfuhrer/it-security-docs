tags: #symmetric #perfect-secrecy #shannon

# Shannon's Theorem

links:  [[102 AC1 TOC - Security & Cryptography|AC1 TOC - Security & Cryptography]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

Shannon provided a characterization of perfectly secret encryption schemes.

> We have an encryption scheme with $|M| = |K| = |C|$, the scheme is perfectly secret iff:
> 
> 	1. Every key $k \in K$ is chosen with equal probability $1/|K|$ by $Gen$
> 	2. For every $m \in M$ and every $c \in C$, there is a unique key $k \in K$ such that $Enc_k(m)$ outputs $c$

Given that $M, K$ and $C$ represent spaces (Message-, key- and ciphertextspace) and not concrete expressions/terms (as also stated in [[Shannon Cipher|Shannon Cipher]]).

---
links:  [[102 AC1 TOC - Security & Cryptography|AC1 TOC - Security & Cryptography]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]