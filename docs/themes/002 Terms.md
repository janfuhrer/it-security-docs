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

**Math**

* [[Modular Arithmetic#Greatest Common Divisor|GCD]] (Greatest common divisor)
* [[Modular Arithmetic#Euler's Totient Function $ phi$|Euler's Totient Function]] ($\phi$)
* [[Modular Arithmetic#Fermat's (Little) Theorem|Fermat's Little Theorem]] ($a^{p-1}\equiv 1 \quad (mod\; p)$)
* [[Modular Arithmetic#Euler's Theorem|Euler's Theorem]] ($a^{\phi(n)}\equiv 1 \;(mod \; n)$)
* [[Modular Arithmetic#Primitive Root Modulo $n$|Primitive Root]]
* [[Modular Arithmetic#Multiplicative Inverse Modulo n|Multiplicative Inverse]]
* [[Modular Arithmetic#Co-prime|Co-prime]]
* [[Prime Numbers#Safe prime|Safe prime]] ($p = 2q+1$)
* [[Group Theory#Subgroups|Lagrange's Theorem]] (For sub groups)
* [[Generating (Random) Primes#Miller-Rabin|Miller-Rabin]] (Primality test)
* [[Algorithm of Euclid]] (Standard and extended)
* [[Modular Exponentiation#Square-and-Multiply Algorithm|Square and Multiply]]
* [[Computational Hardness Assumption|Hardness Assumptions for Cryptography]]
* [[FACTORING & DL Algorithms#Baby-Step-Giant-Step Algorithm|BSGS]] (Baby-Step-Giant-Step + Pollard's rho)
* [[Group, Ring and Field]] (differences)
* [[Elliptic Curves in Crypto#Embedding Degree|Embedding Degree]]
* [[Elliptic Curves in Crypto#(Asymmetric) Pairing|Pairing]]
* [[Advanced Cryptographic Primitives#Pairing-based cryptography|Pairing-based cryptography]]
* [[Advanced Cryptographic Primitives#Homomorphic Encryption|Homomorphic Encryption]] (Make calculations on the ciphertext)

| Notation | Description |
|----------|-------------|
|$\mathbb{Z}_n$|Set of integers modulo n, called the ring of integers modulo $n$. Consists of the integers $\{0, 1, 2, ..., n-1\}$|
||Additive group $(\mathbb{Z}_n, +_n, −_n, 0)$|
|$\mathbb{Z}_n^*$ |Multiplicative group $(Z^∗_n, \times_n,^{−1} ,1)$|
|$G_q ⊂ Z^∗_p$ |Subgroup $G_q$ (If $p$ and $q$ are used prime numbers are implied)|
|$G$ / $\mathcal{G}$ |Group notation $\mathcal{G} =(G,◦,inv,e)$|
|$F$ / $\mathcal{F}$ |Field notation $\mathcal{F} = (F,+,−,0,×,^{−1} ,1)$|
|$E_{a,b}(F)$|Elliptic curve over a field with curve parameters $a$ and $b$|


**Public-key cryptosystems**

* [[Diffie-Hellman|DH]] (Key exchange)
* [[ElGamal]] (encryption)
* [[RSA]] (encryption)
* [[RSA Signature Scheme|RSA]] (signature)
* [[Blind Signatures (RSA)|Blind Signatures]] (with RSA)
* [[Schnorr Signatures|Schnorr]] (signature)
* [[DSA Signature Scheme|DSA]] (signature)
* [[Elliptic Curves in Crypto#BLS Signature Scheme|BLS]] (signature)

**Certificates**

- [[X.509 Certificates|X.509]] (Format of public key certificates)
- [[Public Key Infrastructure#Certification Authority (CA)|CA]] (Certification Authority)
- [[Trust Issues in X.509#Online Certificate Status Protocol (OCSP)|OCSP]] (Online Certificate Status Protocol)
- [[X.509 CA Alternatives#Alternative 1 [DNSSEC / DANE](https //tools.ietf.org/html/rfc6698)|DANE]] (DNS-Based Authentication of Named Entities)
- [[X.509 CA Alternatives#Alternative 1 [DNSSEC / DANE](https //tools.ietf.org/html/rfc6698)|DNSSEC]]
- [[X.509 CA Alternatives#Alternative 2 [HTTP PublicKEy Pinning (HPKP)](https //www.owasp.org/index.php/Certificate_and_Public_Key_Pinning)|HPKP]] (HTTP Public Key Pinning)
- [[X.509 CA Alternatives#Alternative 5 HTTP Strict Transport Security (HSTS)|HSTS]] (HTTP Strict Transport Security)

**Secure Channels / Messaging**

- [[TLS]] (Transport Layer Security)
- [[SMTP]] (Simple Mail Transfer Protocol)
- [[MIME#MIME|MIME]] (Multipurpose Internet Mail Extensions)
- [[MIME#S/MIME|S/MIME]] (Secure/Multipurpose Internet Mail Extensions)
- [[Asynchronous Bidirectional Secure Channels#Forward secrecy|Forward secrecy]] (past stays secret)
- [[Asynchronous Bidirectional Secure Channels#Future secrecy|Future secrecy]] (future will stay secret)
- [[Asynchronous Bidirectional Secure Channels#Silent Circle Instant Message Protocol (SCIMP)|SCIMP]] (Silent Circle Instant Message Protocol)
- [[Asynchronous Bidirectional Secure Channels#Axolotl / Signal Protocol|Signal Protocol]]

**Anonymity**

- [[Anonymity]] (Different aspects of anonymity) 
- [[Anonymity - Trilemmas|Trilemmas]] (achieve 2 out of 3 goals)
- [[Anonymity - Attacks#What is a Sybil attack and how can it be mitigated|Sybil attack]] (many fake identities)
- [[Anonymity - Attacks#What is an eclipse attack and how can it be mitigated?|Eclipse attack]](separate nodes from each other)
- [[Anonymity - Attacks#What is a poisoning attack and how can it be mitigated?|Poisoning attack]] (nodes provide false information)
- [[Anonymity - Attacks#What is a timing attack and how can it be mitigated?|Timing attack]] (latency, delay, timestamps)
- [[Distributed Computing#Explain Boyd's Theorem I and II|Boyd's Theorems]] (about secure communication)
- [[Distributed Computing#Explain Zfone Authentication (ZRTP)|Zfone Authentication]] (extend DH stuff and call each other)
- [[Distributed Computing#Explain self stabilisation|Self stabilisation]] (system that recovers it self)
- [[Distributed Computing#What is Secure Multiparty Computation?|SMC]] (Secure Multiparty Computation. Jointly compute something but private)
- [[Anonymity - TOR|TOR]]

**Decentralisation**

* [[GnuPG|GPG]] (GNU Privacy Guard)
* [[Trust Model]] (TOFU, Web of Trust, Hierarchical Trust)
* [[Fog of Trust]] (Secure Web of Trust)
* [[DHT]] (Distributed Hash Tables and different approaches)
* [[GNS]] (GNU Name System)
* [[GNUnet]]

**Taler**

* [[Cut-and-choose zero-knowledge proof|Cut-and-choose]] (Zero knowledge proof)
* [[GNU Taler Overview|GNU Taler]] (Overview)
* [[Credit Card Surveillance|Credit Card Surveillance]]
* [[GNU Taler Details#Double Spending Problem|Double Spending Problem]]
* [[Payto]] (Similar to mailto)


---
links: [[themes/000 Index|Index]]
