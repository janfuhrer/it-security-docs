tags: #symmetric

# CCA-Security

links:  [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

Assume we have an **active** adversary wich observing a ciphertext $c$. An attacker who can tamper with the communication can modify $c$ to generate another ciphertext $c'$ and send it to the receiver. The receiver will then decrypt $c'$ to get $m'$ (if $m' \neq m$ and $m' \neq \perp$, this is a violation of integrity). What is of interest to us here, however, is the potential impact on secrecy. In particular, if the attacker learns partial information about $m'$, might that reveal information about the original message $m$?

This type of attack, in which an adversary causes a receiver to decrypt ciphertexts that the adversary generates, is called a *chosen-ciphertext attack*. *Chosen-ciphertext attacks are possible, in principle, any time an attacker has the ability to inject traffic on the channel between the sender and receiver*.

**Example**: imagine a client sending encrypted messages to a server. If an adversary can impersonate the client and send ciphertexts to the server that appear to originate from the client, the server will decrypt those ciphertexts and the adversary may learn something about the result

### Padding-Oracle Attacks

The adversary can send arbitrary ciphertexts to the padding oracle (e.g. a server) and learn (based on whether a "bad padding" error is returned) whether the underlying encoded data is padded correctly or not. It enables an adversary to completely recover the original message corresponding to any ciphertext of its choice.

Padding oracle attacks can be quite powerful because they exploit vulnerabilities in the padding validation process, allowing attackers to decrypt encrypted data without knowledge of the encryption key.

### Non-Malleability

CCA-security implies a very important property called *non-malleability*.

> A non-malleable encryption scheme has the property that if the adversary modifies a given ciphertext, the result decrypts to a plaintext that bears no relation to the original one.


---
links:  [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]