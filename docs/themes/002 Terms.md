# Terms

links: [[themes/000 Index|Index]]

---

**NIST Glossary**

- The NIST maintains a comprehensive cybersecurity glossary: [NIST Glossary](https://csrc.nist.gov/glossary)
- Check actual recommendations for key length on [Keylenght.com](https://www.keylength.com/)

**Cryptographic Hash Functions**

* [[Cryptographic Hash Functions#SHA-1|SHA-1]] (Merkle–Damgård construction)
* [[Cryptographic Hash Functions#SHA-2|SHA-2]] (Merkle–Damgård construction)
* [[Cryptographic Hash Functions#SHA-3|SHA-3]] (Sponge construction / Keccak)
* BLAKE (Bernstein)

**KDF (Key Derivation Function)** 

* [[Key Derivation Function (KDF)|KDF]]
* HKDF (Using HMAC/Hash)
* [[Password Based Key Derivation Function (PBKDF)#PBKDF using Argon2|Argon2]] (Password Based $\rightarrow$ [[Password Based Key Derivation Function (PBKDF)|PBKDF]])
* PBKDF2
* scrypt

**MAC (Message Authentication Code)**

- [[Cryptographic MACs#CBC-MAC|CBC-MAC]] (Block cipher based)
* [[Cryptographic MACs#HMAC (Hash-based Message Authentication Code)|HMAC]] (Hash Based)
* [[Cryptographic MACs#Poly1305|Poly1305]] & [[Cryptographic MACs#GMAC (Galois Message Authentication Code)|GMAC]] (Based on a universal hash family)
* [[Cryptographic MACs#KMAC (Keccak Message Authentication Code|KMAC]] (Based on Keccak. Also usable as a regular hash function without key)

**AEAD (Authenticated Encryption and Associated Data)**

* [[Authenticated Encryption#GCM (Galois/ counter mode)|AES-GCM]] (Block cipher)
* [[Authenticated Encryption#ChaCha20-Poly1305|ChaCha20-Poly1305]] (Bernstein)
* [[Ascon|Ascon]] (Sponge construction)

**XOF (Extended Output Function)**

* [[themes/SHAKE & cSHAKE|SHAKE & cSHAKE]] (Based on Keccak)

**Networking**
[[TLS]] (Transport Layer Security)
[[it-security-docs/docs/themes/TLS#^dbdd19|HSTS]] (HTTP Strict Transport Security)

**Random**

* PRG (Pseudo Random Generator)
* [[Pseudorandom Number Generator (PRNG)|PRNG]] (Pseudo Random Number Generator)
	* Subset of PRG. Used interchangeably.
* [[Pseudorandom Number Generator (PRNG)#Other properties|CSPRNG]] (Cryptographically secure pseudorandom number generator)
	* A PRNG that is safe for cryptographic use. (Assuming the seed is picked correctly)
* [[CPA-Security#Pseudorandom Functions and Permutations|PRF]] (Pseudo Random Function) 
	* [KDF > PRF > MAC](https://crypto.stackexchange.com/a/60652)
	* [HASH vs XOF vs MAC vs PRF vs KDF](https://www.cryptosys.net/pki/manpki/pki_prfxof.html)
* [[Random Number Generator (RNG)|RNG]] (Random Number Generator)
	* Some mechanism that produces random numbers
* [[Random Number Generator (RNG)#TRNG|TRNG]] (True Random Number Generator)
	* An RNG that is based off of some unpredictable physical process.

---
links: [[themes/000 Index|Index]]