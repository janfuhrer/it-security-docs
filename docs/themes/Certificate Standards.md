tags: #AC2 #asymmetric 

# Certificate Standards

links: [[207 AC2 TOC - X.509|AC2 TOC - X.509]] - [[themes/000 Index|Index]]

---

- [[X.509 Certificates]] (for public keys)
- [[Attribute Certificates|Attribute Certificates]] (bind set of descriptive data items to a subject name)
- PGP Certificates (Pretty Good Privacy. [[Trust Model#The Web of Trust|Web of Trust]])
- [[Card Verifiable Certificates|CV Certificates ]](Card Verifiable Certificates)

X.509 certificates are not compatible to OpenPGP or CVC.

## X.509

The [[X.509 Certificates]] Authentication Framework designed by CCITT/[[003 Organisations#^1776b5|ITU]] for the purpose of securing the X.500 Directory included a certificate specification where the format and data type remain important until today.

Used in:

* The official [[003 Organisations|IETF]] PKI standard: **PKIX** (Public Key Infrastructure for X.509)
* The (older) industrial standard: [[PKCS]] (Public Key Cryptography Standards)

X.509 is an [[003 Organisations#^1776b5|ITU]] standard — but also:

- TLS servers (and sometimes clients) are identified by public key (e.g. [mTLS](https://www.cloudflare.com/learning/access-management/what-is-mutual-tls/))
- Public keys are certified by certificate authorities  
- X.509 certificates are the format used for certificates (defines not how to distribute over network)
- Any certificate authority can certify keys for any domain (in contrast to DNSSEC, only parent zone can certify a child zone)

Also used by [[MIME#S/MIME|S/MIME]]

## PKCS

* see [[PKCS]]
* Published by RSA
* Goal was to promote public-key techniques
* Not open standards $\rightarrow$ Industrial standards
	* Most were moved into PKIX

## X.500

X.500 entries are based on a Distinguished Name (DN), which is part of a global unique namespace. (Hint: LDAP)

Hierarchy: 

1. Roots
2. Countries
3. Organisations
4. Organisational units
5. People

> Root $\rightarrow$ USA $\rightarrow$ Google $\rightarrow$ Staff $\rightarrow$ John Doe

```
CN = Thawte Personal Freemail Issuing CA,
O = Thawte Consulting (Pty) Ltd, C = ZA
```

## ASN.1 and DER

**Abstract Syntax Notation One (ASN.1):**

* Defined by the ITU-T
* Specifies **type and structure** of data:
	* Type of value (integer, boolean, character string, etc.)
	* Structure (containment, order, options)
* Does not specify encoding (representation)

**Distinguished Encoding Rules (DER):**

Provides the advantage to have a unique way of **encoding** each ASN.1 value.

**Privacy-Enhanced Mail (PEM) Encoding**

Base64 of DER bytestream with "begin certificate" and "end certificate" markers.

```
-----BEGIN CERTIFICATE-----

-----END CERTIFICATE-----
```

## Object Identifiers (OIDs)

* An Object Identifier (OID) is an identifier used to name an object in a hierarchically-assigned namespace $\rightarrow$ an OID number should never change!
* In the security domain, OIDs serve to name almost every object type in X.509 certificates, such as components of Distinguished Names, Algorithms, etc.

*Example*: [oid-info.com - oid 1.2.840.113549.1.1.5](http://www.oid-info.com/cgi-bin/display?oid=1.2.840.113549.1.1.5&submit=Display&action=display)

## Certificate Authorities (CA)

- see [[Public Key Infrastructure#Certification Authority (CA)|PKI CA]]
- Entities that *claim* to be trustworthy to verify identities and issuing public key certificates
- CAs can be organized into a directed graph
- X.509: Tree depth can be limited for a subtree (see X.509 [[X.509 Certificates#basicConstraints|basicConstraints]] Extension)
- X.509: Certificates of CAs signing intermediate-level CAs have the special "CA" bit set (see X.509 [[X.509 Certificates#keyUsage|keyUsage]] Extension)

## Self-signed certificates

- Signer is self  
- Allowed by TLS  
- Used to sign CA tree roots

---
links: [[207 AC2 TOC - X.509|AC2 TOC - X.509]] - [[themes/000 Index|Index]]