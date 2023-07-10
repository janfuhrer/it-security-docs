tags: #asymmetric 

# Elliptic Curves in Crypto

links: [[206 AC2 TOC - Elliptic Curves|AC2 TOC - Elliptic Curves]] - [[themes/000 Index|Index]]

---

Writing elliptic curves as **additive** groups is a convention.

$xP = \underbrace{P + P + · · · + P}_{\text{x times}}$ instead of $P^x$

A **generator** $G$ of an elliptic curve of order $q$ can generate all points from $G$ to $qG$
If $q$ is prime all points are generators except for $\mathcal{O}$

## DL problem in elliptic curves (ECDL)

Finding a value $x \in \mathbb{Z}_p$ such that $xG = P$

The fastest general ECDL algorithm is **Pollard’s rho** algorithm with an expected running time of $\mathcal{O}(\sqrt{q})$. This means that a 256 bit prime $p$ gives us 128 bits of security.

## Elliptic Curve Cryptography (ECC)

- Elliptic curve Diffie-Hellman key exchange (ECDH)  
- Elliptic curve ElGamal encryption scheme (EC-ElGamal)
- Elliptic curve DSA signature scheme (ECDSA)

We need algorithms to encode and decode messages into curve points. Those exist and are efficient.

## Elliptic Curves in Practice

The generation of “good” elliptic curves is a cumbersome process. Some parameters $a,b \in \mathbb{Z}_p$ are insecure.

Use standardised curves but be careful of magic numbers and whom you trust.

* Curve25519 (Bernstein)
* secp256k1 (Bitcoin)
* P-256, P384 (NIST)
* Brainpool curves

## Advanced topics

### Embedding Degree

* Let $q$ be the prime order of some sub-group of $⟨G⟩ ⊆ E(\mathbb{Z}_p)$, i.e., $q$ is dividing $|E (\mathbb{Z}_p)|$
* The embedding degree of $E(\mathbb{Z}_p)$ relative to $q$ is the smallest integer $k$ such that $q$ divides $p^k − 1$
* For elliptic curves with small embedding degrees $k = 2, 3, 4, 6$ the **Weil pairing** and **Tate pairing** can be computed efficiently

If you have an elliptic curve defined over a finite field, you can consider the group of points on that curve, and that group will have a certain size (the order). You can also look at the finite field itself, and consider larger fields obtained by taking powers of the original field's size. The embedding degree tells you how far you have to go in this process before you get a field in which the order of the group divides the size of the field minus 1.

**Example**

Suppose we have an elliptic curve defined over the finite field $F_7$, and let's say this curve's group has order $n = 9$.

We want to find the smallest positive integer $k$ such that $n$ divides $7^k - 1$.

$k=1: 7^1 - 1 = 6$

$k=2: 7^2 - 1 = 48$

$k=3: 7^3 - 1 = 342$ (divisible by 9)

So, the embedding degree of this elliptic curve with respect to the order $9$ is $k=3$.

### (Asymmetric) Pairing

The Weil and Tate pairings are examples of a mapping from two groups $\mathcal{G}_1 = (G_1,+,−,0)$ and $\mathcal{G}_2 = (G_2,+,−,0)$ into a target group
$G_T = (G_T,×,^{−1} ,1)$: 

$$e: G_1 \times G_2 \rightarrow G_T$$

Such a mapping is called **bilinear map**, if the following two properties hold:

* Bilinearity: $e(xP,yQ)=e(P,Q)^{xy}$, for all $(P,Q)∈G_1 \times G_2$
* Non-degeneracy: for all $P ∈ G_1$ there is a $Q ∈ G_2$ such that $e(P, Q) \neq 1$, and vice versa

A bilinear map is called **pairing**, if e is computable in an efficient manner and hard to invert

### Symmetric Pairing

In a **symmetric pairing**, the two source groups are identical: 

$$e : G \times G → G_T$$

- If a symmetric pairing exists for a given group $G$, then DDH can be solved efficiently.
- Therefore, such a group G can not be used in a cryptographic scheme relying on DDH
- Note that it is unknown how to solve CDH or DL using a pairing

### Pairing-Based Cryptography

- Cryptographic schemes can be defined based on the bilinearity of the pairing
- All known pairings (Weil, Tate, . . . ) are based on elliptic curves with small embedding degrees
- Can be used for: 
	- Multi-party key exchange, blind signatures, threshold signatures etc.

### Three-Party DH Key Exchange

Extending the classical DH key exchange to three (or more) parties requires $>1$ communication rounds.

Using pairing-based cryptography, a single communication round is sufficient:

1. Alice sends $A = aP$ to Bob and Chris 
2. Bob sends $B = bP$ to Alice and Chris 
3. Chris send $C = cP$ to Alice and Bob 
4. All can compute $k = e(P, P)^{abc}$, since

$e(B,C)^a =e(A,C)^b =e(A,B)^c =e(P,P)^{abc}$

### BLS Signature Scheme

See more details [[Advanced Cryptographic Primitives#Boneh–Lynn–Shacham (BLS) signatures|here]].

* BLS signatures are deterministic (other than RSA, DSA, etc.)
* Scheme proven to be [[Digital Signatures#^7418da|EUF-CMA]] secure under the CDH assumption in the random oracle model
* Multiple signatures $S_1, . . . , S_n$ can be aggregated into a single short signature $S = S_1 + · · · + S_n$, which can be verified step by step using: $e(hash(m_n), PK_n)$
	* (note that aggregated signatures are insecure due to the **rogue public-key attack**, but there are several defense strategies)

---
links: [[206 AC2 TOC - Elliptic Curves|AC2 TOC - Elliptic Curves]] - [[themes/000 Index|Index]]