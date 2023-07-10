# Terms

links: [[themes/000 Index|Index]]

---

**NIST Glossary**

- The NIST maintains a comprehensive cybersecurity glossary: [NIST Glossary](https://csrc.nist.gov/glossary)
- Check actual recommendations for key length on [Keylenght.com](https://www.keylength.com/)

## AC1

**Cryptographic Hash Functions**

* [[Cryptographic Hash Functions#SHA-1|SHA-1]] (Merkle–Damgård construction)
* [[Cryptographic Hash Functions#SHA-2|SHA-2]] (Merkle–Damgård construction)
* [[Cryptographic Hash Functions#SHA-3|SHA-3]] (Sponge construction / Keccak)
* [[Cryptographic Hash Functions#BLAKE|BLAKE]] (ChaCha)

**KDF (Key Derivation Function)** 

* [[Key Derivation Function (KDF)|KDF]]
* [[Key Derivation Function (KDF)#KDF using HMAC (HKDF)|HKDF]] (Using HMAC)
* [[Password Based Key Derivation Function (PBKDF)#PBKDF using Argon2|Argon2]] (Password Based $\rightarrow$ [[Password Based Key Derivation Function (PBKDF)|PBKDF]])
* [[Password Based Key Derivation Function (PBKDF)#PBKDF1 & PBKDF2|PBKDF2]]
* [[Password Based Key Derivation Function (PBKDF)#scrypt|scrypt]]

**MAC (Message Authentication Code)**

- [[Cryptographic MACs#CBC-MAC|CBC-MAC]] (Block cipher based)
* [[Cryptographic MACs#HMAC (Hash-based Message Authentication Code)|HMAC]] (Hash-and-Mac based)
* [[Cryptographic MACs#Poly1305|Poly1305]] & [[Cryptographic MACs#GMAC (Galois Message Authentication Code)|GMAC]] (Based on a universal hash family)
* [[Cryptographic MACs#KMAC (Keccak Message Authentication Code|KMAC]] (Based on Keccak. Also usable as a regular hash function without key)

**AEAD (Authenticated Encryption and Associated Data)**

* [[Authenticated Encryption#GCM (Galois/ counter mode)|AES-GCM]] (Block cipher)
* [[Authenticated Encryption#ChaCha20-Poly1305|ChaCha20-Poly1305]] (Bernstein)
* [[Ascon|Ascon]] (Sponge construction)

**XOF (Extended Output Function)**

* [[themes/SHAKE & cSHAKE|SHAKE & cSHAKE]] (Based on Keccak)

**Random**

* [[Pseudorandom Number Generator (PRNG)#Construct PRG (Pseudo Random Generator) from PRF (Pseudo Random Function)|PRG]] (Pseudo Random Generator)
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

**IND-CPA**

- Randomized Encryption
	- [[Block Cipher#Cipher Block Chaining (CBC) mode|AES-CBC]] (not [[Block Cipher#Chained CBC mode|Chained CBC mode]]!)
	- [[Block Cipher#Output Feedback (OFB) mode|AES-OFB]]
	- [[Block Cipher#Counter (CTR) mode|AES-CTR]]

**IND-CCA**

- [[Authenticated Encryption]] / [[Authenticated Encryption with Associated Data|AEAD]] $\rightarrow$ Non-Mallable
	- [[Authenticated Encryption#GCM (Galois/ counter mode)|AES-GCM]]
	- [[Authenticated Encryption#ChaCha20-Poly1305|ChaCha20-Poly1305]]
	- [[Ascon|Ascon]]

**Naming Systems**

- [[Naming Systems#Cryptography in DNS|Cryptography in DNS]] (DNSSEC / DNSCurve / DoT / DoH / RAINS)
- [[Naming Systems#Ethereum Name System|Ethereum Name Systems]]

**Secure Channel**

- Authenticity & Repudiation!
	- [[Secure Channels#Off-the-record (OTR) protocol|OTR]] (DSA & DH)
	- [[Secure Channels#Triple Diffie-Hellman (3DH)|3DH]] (only DH)

**Key Establishing**

- [[Key Establishment#Neumann-Stubblebine|Neumann-Stubblebine]] (Broken)
- [[Key Establishment#Denning-Sacco|Denning-Sacco]]
- [[Key Establishment#Wide-Mouth Frog protocol|Wide-Mouth Frog protocol]]
- [[Key Establishment#Needham-Schroeder protocol|Needham-Schroeder protocol]]
- [[Key Establishment#Kerberos|Kerberos]]
- [[Key Establishment#Otway-Rees protocol|Otway-Rees protocol]]
- [[Key Establishment#Station to station key agreement protocol (STS)|STS]]

**Key Revocation**

- [[Key Revocation#Certificate Revocation Lists (X.509)|CRL]] (x.509)
- [[Key Revocation#Online Certificate Status Protocol (OCSP)|OCSP]] / OCSP Stapling
- Controlled flooding
	- [[Bloom Filters & Set Unification#Bloom filters|Bloom Filter]] (BF / CBF / IBF)
	- [[Bloom Filters & Set Unification#Set Union Protocol|Set Union Protocol]]

**Key Management**

- [[Key Management#PSE|PSE]]
	- Software ([[PKCS]]#12)
	- Hardware (YubiKey)
	- [[Key Management#Hardware Security Modules (HSM)|HSM]]
- [[Shamir Secret Sharing]] (Polynominals)
- [[Key escrow and recovery#Anastasis|Anastasis]] (Key escrow and recovery)
- [[Threshold Signatures]] (FROST / FROSIX)

## AC2

**Networking**

- [[TLS]] (Transport Layer Security)
- [[X.509 CA Alternatives#Alternative 5 HTTP Strict Transport Security (HSTS)|HSTS]] (HTTP Strict Transport Security)

**Math**

* [[Group, Ring and Field]]

| Notation | Description |
|----------|-------------|
|$\mathbb{Z}_n$|Set of integers modulo n, called the ring of integers modulo $n$. Consists of the integers $\{0, 1, 2, ..., n-1\}$|
||Additive group $(\mathbb{Z}_n, +_n, −_n, 0)$|
|$\mathbb{Z}_n^*$ |Multiplicative group $(Z^∗_n, \times_n,^{−1} ,1)$|
|$G_q ⊂ Z^∗_p$ |Subgroup $G_q$ (If $p$ and $q$ are used prime numbers are implied)|
|$G$ / $\mathcal{G}$ |Group notation $\mathcal{G} =(G,◦,inv,e)$|
|$F$ / $\mathcal{F}$ |Field notation $\mathcal{F} = (F,+,−,0,×,^{−1} ,1)$|
|$E_{a,b}(F)$|Elliptic curve over a field with curve parameters $a$ and $b$|

---
links: [[themes/000 Index|Index]]
