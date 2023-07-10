tags: #asymmetric 

# GNU Taler Key Management

links: [[212 AC2 TOC - GNU Taler|AC2 TOC GNU Taler]] - [[themes/000 Index|Index]]

---

Taler has many types of keys:  
* Coin keys  
* Denomination keys  
* Online message signing keys 
* Offline key signing keys
* Merchant keys  
* Auditor key  
* Security module keys 
* Transfer keys 
* Wallet keys  
* TLS keys
* DNSSEC keys

## Offline Keys

Both exchange and auditor use offline keys.

* Those keys must be backed up and remain highly confidential!
* We recommend that computers that have ever had access to those keys to NEVER again go online.

## Online Keys

The exchange needs RSA and EdDSA keys to be available for online signing.
The public keys are certified using Taler’s public key infrastructure (which uses offline-only keys).

![[Taler Key Management.png]]

Compartmentalise where possible. Different processes are used that have limited access to the keys. Minimal permissions given everywhere.

---
links: [[212 AC2 TOC - GNU Taler|AC2 TOC GNU Taler]] - [[themes/000 Index|Index]]