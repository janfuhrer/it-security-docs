tags: #symmetric #cca #attack #attacker-model 

# CCA-Security

links: [[104 AC1 TOC - Private Key Encryption|AC1 TOC - Private Key Encryption]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

Assume we have an **active** adversary which observes a ciphertext $c$. An attacker who can tamper with the communication can modify $c$ to generate another ciphertext $c'$ and send it to the receiver. The receiver will then decrypt $c'$ to get $m'$ (if $m' \neq m$ and $m' \neq \perp$, this is a violation of integrity). What is of interest to us here, however, is the potential impact on secrecy. In particular, if the attacker learns partial information about $m'$, might that reveal information about the original message $m$?

This type of attack, in which an adversary causes a receiver to decrypt ciphertexts that the adversary generates, is called a *chosen-ciphertext attack*. *Chosen-ciphertext attacks are possible, in principle, any time an attacker has the ability to inject traffic on the channel between the sender and receiver*.

**Example**: imagine a client sending encrypted messages to a server. If an adversary can impersonate the client and send ciphertexts to the server that appear to originate from the client, the server will decrypt those ciphertexts and the adversary may learn something about the result.

## Padding-Oracle Attacks

The adversary can send arbitrary ciphertexts to the padding oracle (e.g. a server) and learn (based on whether a "bad padding" error is returned) whether the underlying encoded data is padded correctly or not. It enables an adversary to completely recover the original message corresponding to any ciphertext of its choice.

Padding oracle attacks can be quite powerful because they exploit vulnerabilities in the padding validation process, allowing attackers to decrypt encrypted data without knowledge of the encryption key.

## Non-Malleability

CCA-security implies a very important property called *non-malleability*.

> A non-malleable encryption scheme has the property that if the adversary modifies a given ciphertext, the result decrypts to a plaintext that bears no relation to the original one.

## Authenticity

IND-CCA itself does not provide authenticity. CCA only requires that an attacker cannot determine which of two different plaintexts a given ciphertext corresponds to. Authenticity cannot be provided because under IND-CCA an attacker is still able to create a new valid ciphertext.

**Example from slides**

[[Block Cipher#Counter (CTR) mode|CTR]] schemes are IND-CCA insecure:

> “Say $⟨r,C⟩$ is a ciphertext of some $l$-bit message $M$, and we flip bit i of $C$, resulting in a new ciphertext $⟨r,C′⟩$. Let $M′$ be the message obtained by decrypting the new ciphertext. Then $M′$ equals $M$ with the i-th bit flipped. Thus, by making a decryption oracle query of $⟨r,C′⟩$ one can learn $M′$ and thus $M$.”
> 
> — Symmetric Encryption by Mihir Bellare and Phillip Rogaway

---
links: [[104 AC1 TOC - Private Key Encryption|AC1 TOC - Private Key Encryption]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]