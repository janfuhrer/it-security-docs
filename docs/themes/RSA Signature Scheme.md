tags: #asymmetric 

# RSA Signature Scheme

links: [[205 AC2 TOC - Digital Signatures|AC2 TOC Digital Signatures]] - [[themes/000 Index|Index]]

---

See [[RSA]] to understand the basics.

Let $pk=(n,e)$ and $sk=(n,d)$ be ordinary RSA keys and $M=S=\mathbb{Z}_n^*$

![[RSA Signature.png]]

## Security

Textbook RSA should never be implemented like that  as it's not EUF-CMA secure:

* Textbook RSA is deterministic (same message always gives the same result)
* Textbook RSA is multiplicative (The attacker can choose $m_1$ and $m_2$, get signatures on them, and then construct a valid signature on the message $m_1m_2$, even though they never got a signature on that message.)

**Sign the hash not the message**

Hash-and-Sign: sign $h = hash(m)$ instead of $m \in \{0, 1\}^∗$, use a collision-resistant hash function.

**RSA-SHA**

$hash: \{0, 1\}^∗ \rightarrow \{0, 1\}^{256}$ for SHA-256

* Standardised in PKCS#1 v1.5 (includes padding)
* No proof for EUF-CMA security

**RSA-FDH** (RSA-PSS)

Standardised in PKCS#1 v2.1 as **RSA-PSS** (probabilistic signature scheme)

EUF-CMA secure under RSA assumption (provided that $hash(·)$ has the properties of a random oracle)

See more details here: [[Blind Signatures (RSA)#Full Domain Hash (FDH)|FDH]]

---
links: [[205 AC2 TOC - Digital Signatures|AC2 TOC Digital Signatures]] - [[themes/000 Index|Index]]