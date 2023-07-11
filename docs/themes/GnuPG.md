tags: #asymmetric 

# GnuPG

links: [[211 AC2 TOC - DPKI|AC2 TOC DPKI]] - [[themes/000 Index|Index]]

---

## PGP (Pretty Good Privacy)

- can be used to encrypt and digitally sign files and e-mails
- Data is at rest or transmitted unidirectionally $\rightarrow$ no secure channel!
- PGP certificates are **public key certificates** with one or more identity labels tied to it

## GnuPG (GPG, GNU Privacy Guard)

- free version of PGP, with library (libgcrypt)
- provides common cryptographic primitives & implementation of OpenPGP
- used for: secure e-mail, encrypt files, sign files

## PGP Certificate

- *PGP Version*
- *Holder's public key*: [[RSA]] or DSA
- *Holder information*: identity information (name, user ID, ...)
- *Holder digital signature*: "self-signature", signature using the private key
- *Validity period*: start and expiration date
- *Preferred symmetric encryption algorithm*: e.g. CAST, IDEA, Triple-DES, AES, ...

**PGP Certification**: one certificate may be signed by **multiple entities** (persons)

## Key validity

### PGP Private Keyring

- stores private/public key pairs:
	- timestamp
	- key ID (indexed)
	- public key
	- encrypted private key (with passphrase)
	- user ID (indexed)

### PGP Public Keyring

- stores public key pairs, certificate and trust status:
	- timestamp
	- key ID (indexed)
	- public key
	- user ID (indexed)
	- owner trust:
		- unknown user
		- usually not trusted to sign
		- usually trusted to sign
		- always trusted to sign
		- ultimately trusted (own key in private keyring)
	- signature(s)
	- signature trust(s): copy of owner trust of the signer
	- validity of public key

### Key validity calculation

- if at least one signature trust is ultimate, then the validity of the key is 1 (complete)
- otherwise, a weighted sum of the signature trust values is computed (*always trusted* signature have more weight as *usually trusted*)

---
links: [[211 AC2 TOC - DPKI|AC2 TOC DPKI]] - [[themes/000 Index|Index]]