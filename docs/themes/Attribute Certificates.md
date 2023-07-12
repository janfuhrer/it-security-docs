tags: #AC2 #asymmetric 

# Attribute Certificates

links: [[207 AC2 TOC - X.509|AC2 TOC - X.509]] - [[themes/000 Index|Index]]

---

## Identity Certificates vs. Attribute Certificates

* If you want to change something in a certificate: **Revoke and reissue**
* Attributes in a certificate should be as static as possible
* If you have a dynamic environment it makes sense to use attribute certificates
* **Attribute certificate helps to separate authentication (identity) and authorization (permission).**

## Definition

- a certified set of attributes like temporary network access privileges, electronic letters of credit access, signing and purchasing authority, etc.
- much the same syntax as a X.509v3 certificate (**without a public key**)    
- bound to a serial number of an identity certificate 
- typically have a much **shorter lifetime** than identity certificates 
- grants **temporary authorization** to individuals

Individuals can hold several attribute certificates:

- each referencing the same identity certificate  
- each issued by a different attribute authority (AA)  
- and use them selectively according to the resource or service being accessed

---
links: [[207 AC2 TOC - X.509|AC2 TOC - X.509]] - [[themes/000 Index|Index]]