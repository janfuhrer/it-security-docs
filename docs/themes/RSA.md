tags: #AC2 #math #RSA-AOEP #encrypt

# RSA

links: [[204 AC2 TOC - RSA and ElGamal Encryption|AC2 TOC - RSA and ElGamal Encryption]] - [[themes/000 Index|Index]]

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

The key generation in RSA starts by picking two *different* random Primes $p$ and $q$ which shall be equally large (half of the input parameter $k$). The found $p$ and $q$ are then multiplied to form $n$. First the public key $e$ is calculated by choosing a random relative prime in the group defined by the Euler phi function $\phi(n) = (p-1)(q-1)$, which counts the number of all elements in the multiplicative group $\mathbb{Z}_{\phi(n)}^{*}$ (all elements which generate the group $\mathbb{Z}_{\phi(n)}$ and therefore are relative prime). Given the public key $e$, now the private key $d$ is calculated by calculating the multiplicative inverse of $e$ in $\mathbb{Z}_{\phi(n)}^{*}$. Then resulting key pair consists of the value $n$ and the respective key $e$ (public) or $d$ (private) -> (n,e), (n, d) -> public-key, private-key

![[RSA-Key-Generation.png]]

## Textbook RSA

Textbook RSA leverages and heavily relies on modular exponentiation as internal driver. Given a message $m$ it calculates the ciphertext $c$ by simply applying modular exponentiation to the message using the public key $e$ of the receiving party. $c$ is calculated within the group $\mathbb{Z}_n^{*}$. Therefore $n$ (which is part of the public key) is supplied as parameter to the modular exponentiation algorithm. Since the private key $d$ is the multiplicative inverse of $e$ we can easily decrypt the message by applying modular exponentiation to the ciphertext $c$ using the private key $(n, d)$ as parameter of the algorithm.

Does $m$  need to be in $\mathbb{Z}_n^*$? Probably not: [Link](https://crypto.stackexchange.com/questions/1004/does-rsa-work-for-any-message-m)

![[Textbook-RSA.png]]

![[Textbook-RSA-Example.png]]

![[Textbook-RSA-Security.png]]

**Textbook RSA is insecure (!)**:

- It's completely deterministic -> never a good thing for encryption
- Not IND-CPA because encrypting the same input with the same public key always results in the same output.
- Malleable because an attacker who knows $c$ for some plaintext $m$ can create a ciphertext for $2m$ without knowing $m$.
- see video: [en: Youtube](https://www.youtube.com/watch?v=M7kEpw1tn50)

## RSA-OAEP (Feistel network)
Textbook RSA is insecure because its to easy to brute-force and crack the key using only the process specified in Textbook-RSA due to its deterministic nature. For this reason RSA-OAEP was invented as extension of Textbook-RSA. RSA-OAEP basically just adds a randomized padding to the message leveraging a two-round Feistel network which uses two different hash functions internally. The padded plaintext is encrypted and not the plaintext itself. After decryption, the padding is reversed and the plaintext is revealed.

![[RSA-OAEP-Pseudocode.png]]

![[RSA-OAEP-Padding.png]]

![[RSA-OAEP-Padding-Pseudocode.png]]

![[RSA-OAEP-Unpadding-Pseudocode.png]]

- Instead of encrypting $m$ ($modExp(m)$) a randomized $m'$ is calculated which is then encrypted
- see video: [de: Youtube](https://www.youtube.com/watch?v=WISyWBimSFY)

[[Computational Hardness Assumption#The FACTORING and RSA Assumptions|Additional information about hardness assumption]]

---
links: [[204 AC2 TOC - RSA and ElGamal Encryption|AC2 TOC - RSA and ElGamal Encryption]] - [[themes/000 Index|Index]]