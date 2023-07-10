tags: #AC2 #math 

# RSA

links:  [[204 AC2 TOC - RSA and ElGamal Encryption|AC2 TOC - RSA and ElGamal Encryption]] - [[themes/000 Index|Index]]

---
## RSA Basic Idea

![[RSA.png]]

- Security is based on the hardness of the FACTORING problem

*GPT*
- In the RSA cryptosystem, `e` and `d` are chosen such that they are coprime to `phi(n)`. They are exponents used for encryption and decryption, respectively, and are not required to be coprime to `n`. Their being coprime to `phi(n)` ensures they are multiplicative inverses of each other modulo `phi(n)`, which is a requirement for RSA to function correctly (`e * d ≡ 1 (mod phi(n))`).

![[RSA-Proof.png]]

- The message `m` in RSA encryption and decryption is an element of $Z_n$, the set of all integers modulo `n`. It is not required to be an element of $Z_n^*$ (the set of integers coprime to `n`), because the RSA processes involve exponentiation modulo `n` (not multiplication), and these operations don't require `m` to have a multiplicative inverse modulo `n`.

- However, in practice, it can be beneficial for security reasons to ensure that `m` is coprime to `n`, particularly when `m` contains sensitive information.


## RSA Key Generation

![[RSA-Key-Generation.png]]


## Textbook RSA

![[Textbook-RSA.png]]
![[Textbook-RSA-Example.png]]https://www.youtube.com/watch?v=M7kEpw1tn50
![[Textbook-RSA-Security.png]]
- Not IND-CPA because encrypting the same input with the same public key always results in the same output.
- Malleable because an attacker who knows $c$ for some plaintext $m$ can create a ciphertext for $2m$ without knowing $m$.


## RSA-OAEP (Feistel network)
Textbook RSA is insecure because its to easy to brute-force and crack the key using only the process specified in Textbook-RSA. For this reason RSA-OAEP was invented as extension of Textbook-RSA. RSA-OAEP basically just adds a randomized padding to the message leveraging a two-round Feistel network which uses two different hash functions internally. The padded plaintext is encrypted and not the plaintext itself. After decryption, the padding is reversed and the plaintext is revealed.

![[RSA-OAEP-Pseudocode.png]]
![[RSA-OAEP-Padding.png]]
![[RSA-OAEP-Padding-Pseudocode.png]]
![[RSA-OAEP-Unpadding-Pseudocode.png]]
- Instead of encrypting $m$ ($modExp(m)$) a randomized m* is calculated which is then encrypted
- https://www.youtube.com/watch?v=WISyWBimSFY

[[Computational Hardness Assumption#The FACTORING and RSA Assumptions|Additional information about hardness assumption]]

---

links:  [[204 AC2 TOC - RSA and ElGamal Encryption|AC2 TOC - RSA and ElGamal Encryption]] - [[themes/000 Index|Index]]