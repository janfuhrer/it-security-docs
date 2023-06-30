tags: #symmetric #kdf #key-derivation #pbkdf #password #password-based-key-derivation #low-high-entropy

# Password Based Key Derivation Function (PBKDF)

links: [[105 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[themes/000 Index|Index]]

---

## Low to High Entropy 

A PBKDF (password based key derivation functions) derive a key from an input. This means that a PBKDF creates a key based on some information supplied as input. Other than in pure [[Key Derivation Function (KDF)|KDF]], PBKDF do not need high entropy as input but can also create high entropy output from low entropy. This is especially useful, if you have to for example store passwords or similar.

### PBKDF using Argon2

[Argon2](https://github.com/P-H-C/phc-winner-argon2/blob/master/argon2-specs.pdf) is the winner of the 2015 completed [password hashing competition](https://www.password-hashing.net/). Argon2 is the de facto standard when it comes to hashing passwords. Argon2 is equivalent to a PBKDF and therefore can be used everywhere a low-high entropy scenario comes into play. Argon2 leverages Blake2b as [[Pseudorandom Number Generator (PRNG)|PRNG]].

#### Parameters

Argon2 can be parameterized by adjusting time-, memory-, and parallel-complexity. This allows fine tuning Argon2 for certain use-cases and make it harder to crack passwords by configuring the three parameter with higher values.

## PBKDF1 & PBKDF2

Password-Based Key Derivation Function 1 & 2 are [[Key Derivation Function (KDF)|key derivation functions]]. PBKDF2 is part of [[themes/PKCS|PKCS]] (PKCS #5) series and supersedes PBKDF1, which could only produce derived keys up to 160 bits long.

The PBKDF2 key derivation function has five input parameters:

1. the [[CPA-Security#Pseudorandom Functions and Permutations|PRF]] (e.g. a keyed [[Cryptographic MACs#HMAC (Hash-based Message Authentication Code)|HMAC]])
2. $Password$: master password from which a derived key is generated
3. $Salt$: to reduce ability to use precomputed hashes (rainbow tables)
4. $c$: number of iterations
5. $dkLen$: desired bit-length of the derived key
6. $DK$: the generated derived key

$DK = PBKDF2(PRF, Password, Salt, c, dkLen)$

## scrypt

> scrypt (Pronounced "ess crypt") is a PBKDF created by Colin Percival. The scrypt function is designed to hinder such attempts by raising the resource demands of the algorithm. Specifically, the algorithm is designed to use a large amount of memory compared to other password-based KDFs, making the size and the cost of a hardware implementation much more expensive, and therefore limiting the amount of parallelism an attacker can use, for a given amount of financial resources.

Source: [en: Wikipedia](https://en.wikipedia.org/wiki/Scrypt)

---
links: [[105 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[themes/000 Index|Index]]