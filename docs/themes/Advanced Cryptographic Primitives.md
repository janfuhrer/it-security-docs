tags: #asymmetric #ParingBasedCryptography

# Advanced Cryptographic Primitives

links: [[211 AC2 TOC - DPKI|AC2 TOC DPKI]] - [[themes/000 Index|Index]]

---

## Homomorphic Encryption

$$
E(x_1 \oplus x_2) = E(x_1) \otimes E(x_2)
$$

- Unpadded RSA (multiplicative)

$$
E(x_1) \cdot E(x_2) = x_1^ex_2^e = E(x_1 \cdot x_2)
$$

- ElGamal

$$
\begin{align}
E(x_1) \cdot E(x_2) & = (g^{r_1}, x_1 \cdot h^{r_1})(g^{r_2},x_2 \cdot h^{r_2}) \\
& = (g^{r_1 + r_2}),(x_1 \cdot x_2)h^{r_1+r_2} \\
& = E(x_1 \cdot x_2)
\end{align}
$$

### Fully homomorphic encryption

- Additive

$$
E(A) \oplus E(B) = E(A+B)
$$
- **and** multiplicative

$$
E(A) \otimes E(B) = E(A \cdot B)
$$

- Known cryptosystems: Brakerski-Gentry-Vaikuntanathan (BGV), NTRU, Gentry-Sahai-Waters (GSW)

## Pairing-based cryptography

*Hint for Exam: this is a simple Signature Scheme*

- Pairing-based cryptography is based on pairing functions that map pairs of points on an elliptic curve into a finite field
- if constructed properly, they can produce finite fields that are large enough to make the discrete logarithm problem hard to compute, but small enough to make computations efficient
- Pairing-based cryptography can be used to construct identity-based encryption (IBE), which allows a sender to encrypt a message without needing a receiver’s public key to have been certified and distributed in advance. IBE uses some form of a person (or entity’s) identification to generate a public key

Source: [en: doubleoctopus.com](https://doubleoctopus.com/security-wiki/encryption-and-cryptography/pairing-based-cryptography/#:~:text=Pairing%2Dbased%20cryptography%20has%20been,to%20generate%20a%20public%20key.)

![[pairing-based-cryptography.png]]

### Hardness assumption

- Computational Diffie Hellman (remains hard on $G$ even given $e$):

$$
g,g^x,g^y \implies g^{xy}
$$

### Boneh–Lynn–Shacham (BLS) signatures

- cryptographic signature scheme with allows a user to verify that a signer is **authentic**
- scheme uses a *bilinear pairing* for verification, signatures are elements of an elliptic curve group (provides some defense against index calculus attacks)
- (Index calculus attacks exploit the algebraic structure of finite fields or elliptic curves to solve the discrete logarithm problem efficiently. The key idea behind index calculus attacks is to build a system of equations involving the unknown exponent "x" and then solve these equations using linear algebra or other mathematical techniques.)

* $x$: private key
* $g^x$: public key
* $\sigma$: signature
* $h$: hash
* g: generator

![[bls_1.png]]

![[bls_2.png]]

---
links: [[211 AC2 TOC - DPKI|AC2 TOC DPKI]] - [[themes/000 Index|Index]]