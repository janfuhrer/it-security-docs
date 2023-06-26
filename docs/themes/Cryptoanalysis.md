tags: #symmetric #asymmetric 
links:  [[Topic 2 - Security]], [[themes/000 Index|Index]]

---
# Cryptoanalysis

The art or process of deciphering coded messages without being told the key.

- Brute Force Attack
- Indistinguishability (IND)
- Non-Malleability (NM) - The One Time Pad is vulnerable to this
- Ciphertext only Attack (CoA)
- Known Plaintext Attack (KPA)
- Chosen Ciphertext Attack (CCA)
- Chosen Plaintext Attack (CPA)

If the cipher holds against this it is IND-CPA secure.

**CPA** means that the attacker is able to obtain the encryption of any message of their choosing. In symmetric key cryptography this models tricking the enemy into using certain words. In asymmetric cryptography the attacker can use the public key to encrypt whatever they want, and this is the simplest form of attack you can imagine.

IND-CPA immediately implies some sort of randomised ciphertext: if encryption was deterministic, the attacker would just encrypt the two plaintexts of their choice by themself, then compare those against the challenge received.

Textbook RSA is not secure under CPA (due to a lack of randomisation), but ElGamal is. AES in ECB mode is not (due to lack of an IV), but in CBC/CTR mode it is.

**CCA** means the attacker is able to obtain the decryption of any ciphertext of their choosing, except the challenge. It models the case where tricking an enemy into decrypting a lot of ciphertexts for you will not help you into breaking any others.

One consequence of CCA security is that the ciphertext should be tamperproof (non malleable) . If it is not, then the attacker can slightly alter the challenge ciphertext in a predictable way, then try to get the decryption of this altered challenge.

RSA and ElGamal are not CCA secure due to their homomorphic properties, but RSA-OAEP is. AES in CTR mode is not CCA secure (flipping a bit in the ciphertext means flipping a bit in the plaintext), but AES in and AEAD mode like GCM is.

IND-CCA is a really strong notion of security, and the golden standard these days. There are standard constructions to turn any IND-CPA construction into an IND-CCA construction.

---
links:  [[Topic 2 - Security]], [[themes/000 Index|Index]]