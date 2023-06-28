tags: #AC1 

# CBC Attack

links:  [[108 AC1 TOC - From Symmetric Encryption to Secure Channels|AC1 TOC - From Symmetric Encryption to Secure Channels]] - [[themes/000 Index|Index]]

---

## Attacking CBC stateful IV

In a chosen plaintext attack, an attacker can choose a plaintext and observe the resulting ciphertext. In the case of a stateful IV, if the attacker can predict the IV that will be used (for example, because they know the previous ciphertext), they can choose a plaintext that, when XORed with this predicted IV, results in a specific block that they want to encrypt. This allows them to get the ciphertext for any block of their choosing.

In other words:

If you guess the plaintext corresponding to _any_ ciphertext block you have seen before, and can predict a future IV, you can verify your guess by submitting a suitable message to be encrypted with that IV. Obviously, that could be bad if, say, you knew the plaintext to be either "yes" or "no", and only need to find out which one it is.

Extract cookies that were sent over HTTPS: [BEAST](https://crypto.stackexchange.com/a/3885)

---

links:  [[108 AC1 TOC - From Symmetric Encryption to Secure Channels|AC1 TOC - From Symmetric Encryption to Secure Channels]] - [[themes/000 Index|Index]]