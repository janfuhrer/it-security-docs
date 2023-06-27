tags: #AC1 

# Key Revocation

links:  [[112 AC1 TOC - Key Revocation|AC1 TOC - Key Revocation]] - [[themes/000 Index|Index]]

---

## What is key revocation?
The process of invalidation a cryptographic key pair. It's used when a key is compromised or no longer required.

**Certificate Revocation Lists (X.509)**
CRL is a list of certs which have been revoked by the issuing CA before their scheduled expiration date.

**Online Certificate Status Protocol (OCSP)**
Protocol used to obtain the revocation status of a cert. Instead of having to parsing a list of revoked certs itself, a client sends a query to an OCSP responder and receives information about a single cert.

**OCSP Stapling (TLS)**
The server itself periodically retrieves OCSP response for its own cert and "staples" it to the TLS handshake which means the client doesn't have to contact the OCSP himself.

**Publish Revocation in blockchain**
Revocations could be published on the blockchain. Similar to CRL but decentralised, don't have to trust CA.

**Controlled flooding**
Revocations (signed with private key) can be flooded through a network. It's controlled in that each message is only re broadcasted a certain number of times to prevent endless loops. Efficient set reconciliation ([[Bloom Filters & Set Unification]]) is used to compare the sets of revoked certs when nodes first connect to make sure they both have the same state. Proof of work is used to limit DoS-potential. POW can be calculated ahead of time and stored offline to have them read in case they are needed. 

---
links:  [[112 AC1 TOC - Key Revocation|AC1 TOC - Key Revocation]] - [[themes/000 Index|Index]]