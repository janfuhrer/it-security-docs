tags: #asymmetric 

# DSA Signature Scheme

links: [[205 AC2 TOC - Digital Signatures|AC2 TOC - Digital Signatures]] - [[themes/000 Index|Index]]

---

* DSA = Digital Signature Algorithm  
* ECDSA = Elliptic Curve Digital Signature Algorithm

Exists because of the Schnorr patent.

## DL-Based Signature Schemes

Multiple signature schemes are based on the [[Computational Hardness Assumption#Discrete Logarithm Assumptions (DL)|DL assumption]]

* DSA signature scheme (most widely used in practice)  
* [[Schnorr Signatures|Schnorr signature scheme]]  
* [[ElGamal]]/Pointcheval–Stern signature scheme (rarely used)

Advantage of DL-based signature schemes:

* Shorter keys ([[Elliptic Curves|EC]])
* Shorter signatures
* More efficient (less energy)
* Important for smartcard-based implementations

## Math

Ugly beautiful, involves two hashes, relative primes and multiplicative inverse.

Key generation is simple:

Let $(G_q,\times,−1 ,1)$ be a group of order $q$ and $g \in G_q$ a generator

* $sk \rightarrow randInt(q)$ where $sk \in \mathbb{Z}_q$
* $pk := g^{sk}$ where $pk \in G_p$

## Properties

* The DSA and ECDSA signature schemes are [[Digital Signatures#EUF-CMA|EUF-CMA]] secure under the [[Computational Hardness Assumption#Discrete Logarithm Assumptions (DL)|DL assumption ]](provided that the hashes have the properties of a [[Random-Oracle Model|random oracle]])
* Security is still unproven as one of the hash functions is not standardized.
* DSA works also in a subgroups $G_q ⊂ Z^∗_p$ of much smaller order $q$, which then leads to much smaller signatures
* For example, if $p$ is a 3072-bits prime and $q$ is a 256-bits prime, then the signature size is $2 \cdot 256 = 512$ bits (signature consists of $s = (s_1, s_2)$ where $s_1$ and $s_2$ are 256-bits)
	* ̈The combination of 3072/256 bits for $p$ and $q$ corresponds to security strength $s = 128$
	* Note that 256 bits for $q$ fits well with SHA-256

---
links: [[205 AC2 TOC - Digital Signatures|AC2 TOC - Digital Signatures]] - [[themes/000 Index|Index]]