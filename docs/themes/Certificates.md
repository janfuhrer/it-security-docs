tags: #AC2 #asymmetric 

# Certificates

links: [[207 AC2 TOC - X.509|AC2 TOC - X.509]] - [[themes/000 Index|Index]]

---

## Definition

> Digital certificates are data structures which bind a public key value to a subject (Identity). The binding is asserted by an issuer.

Asymmetric Crypto uses privat/public key pairs where the public key pairs are distributed. So an attacker could just distribute forged public keys. Because of that we need to combine a public key with an identifying information and make this combination tamper resistant. 

The certificate contains primarily:

* Identity and attributes of the **subject** to be protected.  
* Identity and attributes of the **issuer** of the certificate.  
* **Public key** of the subject, used for crypto operations.  
* **Signature** from an issuer, covering all certificate content. (Tamper resistance)

---
links: [[207 AC2 TOC - X.509|AC2 TOC - X.509]] - [[themes/000 Index|Index]]