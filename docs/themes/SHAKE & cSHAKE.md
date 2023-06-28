tags: #symmetric #shake

# SHAKE & cSHAKE

links: [[105 AC1 TOC - Private Key Encryption|AC1 TOC - Private Key Encryption]] - [[themes/000 Index|Index]]

---

## SHAKE

- SHAKE (**S**ecure **H**ash **A**lgorithm and **KE**CAK) is an Extendable-Output Function (or XOF)
- It is like SHA-3 but with an **infinite** output
- can be used as a [[Key Derivation Function (KDF)|KDF]], a [[Pseudorandom Number Generator|PRNG]], a [[Stream Cipher]], ...
- based on the [[Keccak]] permutation function

## cSHAKE

- cSHAKE is a customisable version of SHAKE
- has one new input: a **customization string**
- the purpose is to **avoid collisions** between different usages of the SHAKE function

**Examples**

- In [[Cryptographic MACs#KMAC (Keccak Message Authentication Code)|KMAC]], the cSHAKE function is called with the customization string "KMAC"
- two examples given by the NIST publication:
	- cSHAKE128(public_key, 256, "", "key fingerprint")
	- cSHAKE128(email_contents, 256, "", "email signature")

Source: [Link](https://cryptologie.net/article/388/shake-cshake-and-some-more-bit-ordering/)

---
links: [[105 AC1 TOC - Private Key Encryption|AC1 TOC - Private Key Encryption]] - [[themes/000 Index|Index]]