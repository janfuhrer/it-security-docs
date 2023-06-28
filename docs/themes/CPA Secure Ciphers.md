tags: #AC1 #symmetric #StreamCipher #BlockCipher #Indistinguishability

# CPA Secure Ciphers

links [[105 AC1 TOC - Private Key Encryption|AC1 TOC - Private Key Encryption]] - [[themes/000 Index|Index]]

---
### CPA - Attacker Model
The CPA attacker model is maybe the most important in cryptography. If a cipher can resist a CPA attacker, the cipher is deemed secure.

The CPA attacker model describes an attacker who can choose a plaintext, encrypt it and retrieve the resulting ciphertext (encryption oracle). What this means in practice is that a cipher must resist attackers who are capable of installing and using tools like openssl or similar. It also means that the cipher must be secure, even if your system does leak ciphertext for a given input at some point (for example if you 'accidentally' log your ciphertext to the web console or similar stupid stuff).

Everything about CPA is also described by Katz & Lindell and summarised [[CPA-Security|here]].

### Indistinguishability
The most important requirement which is needed for a CPA secure cipher is the indistinguishability of ciphertexts. It is defined by Lindell & Katz (p. 73) as follows:

If you give an attacker access to an encryption oracle as well as two plaintext and one of the plaintext ciphertexts. Now the attacker shall not be able to decide which plaintext was encrypted with a probability much higher than 50% (the deviation must be negligible). Assuming the attacker has access to the encryption oracle all the time.

### Constructing CPA-Secure Cipher

How to construct CPA-Secure ciphers is summarized in chapter [[CPA-Security|CPA-Security]]

---
links [[105 AC1 TOC - Private Key Encryption|AC1 TOC - Private Key Encryption]] - [[themes/000 Index|Index]]
