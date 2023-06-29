tags: #symmetric #kdf #key-derivation #pbkdf #password #password-based-key-derivation #low-high-entropy

# Password Based Key Derivation Function (PBKDF)

links:  [[105 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[themes/000 Index|Index]]

---

## Low to High Entropy 
A PBKDF (password based key derivation functions) derive a key from an input. This means that a PBKDF creates a key based on some information supplied as input. Other than in pure [[Key Derivation Function (KDF)|KDF]], PBKDF do not need high entropy as input but can also create high entropy output from low entropy. This is especially useful, if you have to for example store passwords or similar.

### PBKDF using Argon2

[Argon2](https://github.com/P-H-C/phc-winner-argon2/blob/master/argon2-specs.pdf) is the winner of the 2015 completed [password hashing competition](https://www.password-hashing.net/) . [Argon2](https://github.com/P-H-C/phc-winner-argon2/blob/master/argon2-specs.pdf) is the de facto standard when it comes to hashing passwords. [Argon2](https://github.com/P-H-C/phc-winner-argon2/blob/master/argon2-specs.pdf) is equivalent to a [[Password Based Key Derivation Function (PBKDF)|PBKDF]] and therefore can be used everywhere a low-high entropy scenario comes into play. [Argon2](https://github.com/P-H-C/phc-winner-argon2/blob/master/argon2-specs.pdf) leverages Blake2b as [[Pseudorandom Number Generator]|PRNG].

#### Parameters

[Argon2](https://github.com/P-H-C/phc-winner-argon2/blob/master/argon2-specs.pdf) can be parameterized by adjusting time-, memory-, and parallel-complexity. This allows fine tuning [Argon2](https://github.com/P-H-C/phc-winner-argon2/blob/master/argon2-specs.pdf) for certain use-cases and make it harder to crack passwords by configuring the three parameter with higher values.

---
links:  [[105 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[themes/000 Index|Index]]