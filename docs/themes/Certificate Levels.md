tags: #AC2

# Certificate Levels

links: [[207 AC2 TOC - X.509|AC2 TOC - X.509]] - [[themes/000 Index|Index]]

---

## User Certificates

- **Class 4 / D** - No identity check (at most per e-mail address only) purpose: digital signature, authentication, encipherment
- **Class 3 / C** - low level identity check purpose: digital signature, authentication, encipherment
- **Class 2 / B** - high level identity check of natural person and enterprises, called: advanced (regulated) certificates purpose: digital signature, authentication, (encipherment)
- **Class 1 / A** - highest level identity check, for natural person only mandatory for qualified certificates purpose: non-repudiation only (e.g. in Switzerland ZertES and TAV of BAKOM)

## Server Certificates

* **Domain Validation (DV):** Automated issuing, WHOIS check & simple confirmation (e.g. by e-mail, local agent, etc.) $\rightarrow$ https://letsencrypt.org
* **Organization Validation (OV):** Average examination of claimant. Provides higher level of trustworthiness, thanks to better validation of organisation.
* **Extended Validation (EV):** Strong identity and authenticity verification based on CAB-Forum guidelines, operated by WebTrust for auditing CA’s to be accredited for EV-Certificate issuance $\rightarrow$ certificates have an additional subject information and a policy identifier ([[Certificate Standards#Object Identifiers (OIDs)|OID]] 2.23.140.1.1)

## The Certificate Authority Browser (CAB) Forum

The CAB forum is a voluntary group of CA’s and Browser suppliers with the goal to establish and enforce standards for certificate issuance and processing.

---
links: [[207 AC2 TOC - X.509|AC2 TOC - X.509]] - [[themes/000 Index|Index]]