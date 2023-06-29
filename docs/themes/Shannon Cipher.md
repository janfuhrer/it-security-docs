tags: #symmetric 

# Shannon Cipher

links: [[102 AC1 TOC - Security & Cryptography|AC1 TOC - Security & Cryptography]] - [[themes/000 Index|Index]]

---

* **K**ey space
* **M**essage space
* **C**ipher space
* **E**ncryption function
* **D**ecryption function
* **U**niform
* **Pr**obability

Shanon Cipher: $ε = {(K, M, C)(E: K × M → C, D: K × C → M)}$

Encrypt & Decrypt in detail:

![[Shannon_cipher.png]]

**Decorrelation** 

- Ciphertext is drawn with a uniform probability over the ciphertext space for every key / message input.
- The probability that two different messages using two different keys result in the same ciphertext is equally likely to any other outcome.

**Confusion**

- Intended to make the relationship between the key and ciphertext as complex as possible.
- The same message with a different key should result in a strictly different ciphertext.
- (Confusion can be achieved by applying substitutions)

**Diffusion**

- Refers to rearranging or spreading out the bits in the message so that any redundancy in the message is spread out over the ciphertext. 
- A different message with the same key should result in a strictly different ciphertext.
- (Diffusion can be achieved by applying permutations)

**Recorrelation**

- Refers to the decryption of the message.

---
links: [[102 AC1 TOC - Security & Cryptography|AC1 TOC - Security & Cryptography]] - [[themes/000 Index|Index]]