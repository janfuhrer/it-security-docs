tags: #AC2 #math 

# ElGamal

links:  [[204 AC2 TOC - RSA and ElGamal Encryption|AC2 TOC - RSA and ElGamal Encryption]] - [[themes/000 Index|Index]]

---

## ElGamal Encryption Scheme

![[ElGamal-Encryption-Scheme.png]]

- Security is based on the hardness of the DL (Discrete Logarithm) problem


## ElGamal Key Generation

![[ElGamal-Key-Generation.png]]


## ElGamal Encryption and Decryption

![[ElGamal-Encryption-Decryption.png]]

- $pk = g^{sk}$
- $a = g^r$
- $b = m*pk^r = m*g^{sk*r}$
- $m = b*a^{-sk} = b*g^{-(sk*r)} = b*{\dfrac{1}{g^{sk*r}}} = m * {\dfrac{g^{sk*r}}{g^{sk*r}}} = m$

![[ElGamal-Numerical-Example.png]]


## ElGamal Properties

![[ElGamal-Properties.png]]

[[Generating Random Group Elements and Generators#Generating Random Elements of $G_q subset Z_p *$|Information about Gq subgroup]]

**Information about why DDH doesn't hold in $Z_p^*$**

*GPT*
The Decisional Diffie-Hellman (DDH) assumption is a computational problem in cryptography. Specifically, it's an assumption made about the difficulty of a specific computational task in a cyclic group. The problem is to distinguish between the distributions `(g^a, g^b, g^ab)` and `(g^a, g^b, g^c)` for random `a`, `b`, and `c`.

In the multiplicative group `Z_p^*` (where `p` is prime), the DDH assumption does not hold. This is because if you have access to a group element, you can easily compute its square root (modulo `p`). This means you can distinguish between a random group element and a square. Thus, given `(g^a, g^b, g^ab)` and `(g^a, g^b, g^c)`, it's possible to check whether the third element is the product of the first two (modulo `p`) or not.

On the other hand, if we consider a subgroup `G_q` of `Z_p^*`, where `p = 2q + 1` for `p` and `q` prime (which makes `p` a safe prime), and `G_q` is the subgroup of quadratic residues modulo `p`, the DDH assumption is believed to hold. This is because in this subgroup, it's computationally difficult to distinguish between a random element and a square, hence making it difficult to decide whether the third element is the product of the first two or not.

To summarize, the DDH problem is easier to solve in the full group `Z_p^*` (thus the DDH assumption does not hold), but is believed to be hard in the specific subgroup `G_q` (thus the DDH assumption is considered to hold). This difference arises due to the mathematical properties of these groups and the specific structure of the DDH problem.

---

links:  [[204 AC2 TOC - RSA and ElGamal Encryption|AC2 TOC - RSA and ElGamal Encryption]] - [[themes/000 Index|Index]]