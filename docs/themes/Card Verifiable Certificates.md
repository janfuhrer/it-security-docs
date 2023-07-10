tags: #AC2

# Card Verifiable Certificates

links: [[207 AC2 TOC - X.509|AC2 TOC - X.509]] - [[themes/000 Index|Index]]

---

Due to the reduced storage and memory resources of a smartcard, X.509 certificates are often too large and operation may be too complex.

## Details

- CVC are not compatible with X.509 certificates.  
- CVC are used for authentication only.  
- CVC are encoded in Type-Length-Value (TLV) format.

The minimal set of attributes is: 

- Issuer 
- Subject  
- Public key
- Access rights
- Validity period

To save space and time only the signature value will be stored and transmitted rather than the signature value together with the plaintext content.
This is realised according to the ISO 9796 signature scheme with message recovery:

- ISO 9796 uses RSA (amongst others) as signature algorithm, which has message recovery properties.
- The message itself is only readable/recoverable by verifying the signature.
- In other words: the message is stored/transmitted “encrypted” with the private key and can be decrypted using the public key.

---
links: [[207 AC2 TOC - X.509|AC2 TOC - X.509]] - [[themes/000 Index|Index]]