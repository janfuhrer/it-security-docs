# Terms

links: [[themes/000 Index|Index]]

---

**Cryptographic Hash Functions**

* SHA-1 (Merkle–Damgård construction)
* SHA-2 (Merkle–Damgård construction)
* SHA-3 (Sponge construction / Keccak)
* BLAKE (Bernstein)
* Ascon-Hash (Sponge construction)

**KDF (Key Derivation Function)** 

* HKDF (Using HMAC/Hash)
* Argon2 (Password Based --> PBKDF)
* PBKDF2
* scrypt

**MAC (Message Authentication Code)**

* HMAC (Hash Based)
* KMAC (Based on Keccak. Also usable as a regular hash function without key)
* Poly1305 (Bernstein)

**AEAD (Authenticated Encryption and Associated Data)**

* AES-GCM
* ChaCha20-Poly1305 (Bernstein)
* Ascon-128 (Sponge construction)

**XOF (Extended Output Function)**

* SHAKE / cSHAKE (Based on Keccak)
* Ascon-Xof (Sponge construction)

**Random**

* PRG (Pseudo Random Generator)
* PRNG (Pseudo Random Number Generator)
	* Subset of PRG. Used interchangeably.
* CSPRNG (Cryptographically secure pseudorandom number generator)
	* A PRNG that is safe for cryptographic use. (Assuming the seed is picked correctly)
* PRF (Pseudo Random Function) 
	* [KDF > PRF > MAC](https://crypto.stackexchange.com/a/60652)
* RNG (Random Number Generator)
	* Some mechanism that produces random numbers
* TRNG (True Random Number Generator)
	* An RNG that is based off of some unpredictable physical process.

---
links: [[themes/000 Index|Index]]