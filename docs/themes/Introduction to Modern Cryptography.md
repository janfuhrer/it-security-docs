tags: #symmetric #kerckhoff #historicalCiphers

# Introduction to Modern Cryptography

links:  [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

**Heuristic approach to Science**

Cryptography has gone from a **heuristic set of techniques** for ensuring secret communication for a few **to a science** for all.

**Principles of Modern Cryptography**

- cryptography was historically more of an art than a science, based on their perceived complexity or cleverness
- in modern cryptography, the ultimate goal being to give a rigorous proof that a given construction is secure -> based on *formal definitions* and _hardness assumptions_ about the algorithmic hardness of certain mathematical problem


### Setting of Private-Key Encryption

- Security of **encryption scheme** relies on a secret, **a key** (also named **shared-/ secret-key**) $\rightarrow$ **private-key encryption**
- **Symmetric-key setting**: use the same key for encryption & decryption

> The goal of encryption is to keep the plaintext hidden from an eavesdropper who can monitor the communication channel and observe the ciphertext.


### Keys and Kerckhoffs' principle

> The cipher method must not be required to be secret, and it must be able to fall into the hands of the enemy without inconvenience.

**Security rely solely on secrecy of the key**

### Historical Ciphers

- **Caesar's cipher**: shifting the letters of the alphabet 3 places forward
- **Shift cipher**: a keyed variant of Caesar's cipher, the key $k$ is a number between 0 and 25, encryption is done by shift letters by $k$ places

$\rightarrow$ use *brute-force (or exhaustive-search)* attack

- **mono-alphabetic substitution cipher**: substitute the whole alphabet using a map, the key-space is now $26!$

$\rightarrow$ use *frequency distribution attack*

- **Vigenère (poly-alphabetic shift) cipher**: the key is a string of letters to "smooth out" the frequency distribution

$\rightarrow$ can be broken with enough obtained ciphertexts (and/or if the key is short or the length of the key is known)

### Security goals

- **Ciphertext-only attack (COA)**: adversary just observes a ciphertext (or multiple) to determine information about the plaintext
- **Known-plaintext attack (KPA)**: the adversary is able to learn one or more plaintext/ciphertext pairs generated using some key -> determine information about some *other* ciphertext (using the same key)
- **Chosen-plaintext attack (CPA)**: the adversary can obtain plaintext/ciphertext pairs for plaintexts *of its choice*
- **Chosen-ciphertext attack (CCA)**: the adversary can decrypt ciphertexts of its choice

---

### Definitions

- **Encryption scheme correctness**: $Dec_k(Enc_k(m)) = m$
- **Key space**: set of all possible keys: $K$
	- The key-space must be sufficient large to make an brute-force attack infeasible

---
links: [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]