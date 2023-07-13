tags: #symmetric #private-key

# Key Management

links: [[109 AC1 TOC - Secret sharing|AC1 TOC - Secret sharing]] - [[themes/000 Index|Index]]

---

## PSE

The Personal Security Environment (PSE) is used in information security to describe the part of a storage medium in which the secret keys are stored.

There are 2 different types of PSE: "software based" or "hardware based".

## Software Based

[[PKCS|PKCS#12]] is the most widely used format for software PSEs. It is described as follows:

- File container format used to store and transport private keys
- Content (data) is protected with a private key, e.g. a password.
- The security of [[PKCS|PKCS#12]] is based solely on the strength of the password.

## Hardware Based

There are several hardware crypto tokens/cards on the market (e.g. Yubikey, Smartcards). They all have the following characteristics:

- Ability to be a secure container for secret data.
- A platform for the execution of cryptographic algorithms
- "Black box" from the outside, some operations can only be used through a very restrictive hardware and software interface. Enforcement of specific security policies.
- Access to sensitive data (i.e. private keys) is made physically "impossible" from the outside.

### Yubikey

- Provides Smart Card functionality based on the Personal Identity Verification (PIV) interface specified in NIST SP 800-73
- Performs sign/ decrypt operations using the private key stored on the token via a common interface such as [[PKCS|PKCS]]#11
- Supports [[RSA]] 2048 or ECC 256/384 key sizes
- "Universal Smartcard Minidriver" provides smart functionality and certificate/ PIN management capabilities.
- Some "special" Yubikeys have obtained FIPS 140-2 security level certification.

### Hardware Security Modules (HSM)

HSMs are specialized security hardware devices with the following characteristics
Common functionality:

- Key pair generation
- Random number generator
- Digital signing
- Secure storage and use of key material
- Key archiving
- Acceleration for cryptographic schemes

They are designed to protect keys from:

- Mechanical attacks
- Temperature attacks
- Voltage manipulation
- Chemical attacks

---
links: [[109 AC1 TOC - Secret sharing|AC1 TOC - Secret sharing]] - [[themes/000 Index|Index]]