# Terms

links: [[themes/000 Index|Index]]

---

**Cryptographic Hash Functions**

* [[Cryptographic Hash Functions#SHA-1|SHA-1]] (Merkle–Damgård construction)
* [[Cryptographic Hash Functions#SHA-2|SHA-2]] (Merkle–Damgård construction)
* [[Cryptographic Hash Functions#SHA-3|SHA-3]] (Sponge construction / Keccak)
* BLAKE (Bernstein)
* Ascon-Hash (Sponge construction)

**KDF (Key Derivation Function)** 

* HKDF (Using HMAC/Hash)
* Argon2 (Password Based --> PBKDF)
* PBKDF2
* scrypt

**MAC (Message Authentication Code)**

* [[Cryptographic MACs#HMAC (Hash-based Message Authentication Code)|HMAC]] (Hash Based)
* [[Cryptographic MACs#KMAC (Keccak Message Authentication Code|KMAC]] (Based on Keccak. Also usable as a regular hash function without key)
* [[Cryptographic MACs#Poly1305|Poly1305]] (Bernstein)

**AEAD (Authenticated Encryption and Associated Data)**

* [[Authenticated Encryption#GCM (Galois/ counter mode)|AES-GCM]]
* ChaCha20-Poly1305 (Bernstein)
* Ascon-128 (Sponge construction)

**XOF (Extended Output Function)**

* SHAKE / cSHAKE (Based on Keccak)
* Ascon-Xof (Sponge construction)

**Random**

* PRG (Pseudo Random Generator)
* [[Pseudorandom Number Generator|PRNG]] (Pseudo Random Number Generator)
	* Subset of PRG. Used interchangeably.
* [[Pseudorandom Number Generator#Other properties|CSPRNG]] (Cryptographically secure pseudorandom number generator)
	* A PRNG that is safe for cryptographic use. (Assuming the seed is picked correctly)
* [[CPA-Security#Pseudorandom Functions and Permutations|PRF]] (Pseudo Random Function) 
	* [KDF > PRF > MAC](https://crypto.stackexchange.com/a/60652)
	* [HASH vs XOF vs MAC vs PRF vs KDF](https://www.cryptosys.net/pki/manpki/pki_prfxof.html)
* [[Random Number Generator (RNG)|RNG]] (Random Number Generator)
	* Some mechanism that produces random numbers
* [[Random Number Generator (RNG)#^456990|TRNG]] (True Random Number Generator)
	* An RNG that is based off of some unpredictable physical process.

---
links: [[themes/000 Index|Index]]