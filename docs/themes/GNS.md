tags: #asymmetric #GNS #GNU #DHT

# GNU Name System (GNS)

links: [[211 AC2 TOC DPKI|AC2 TOC DPKI]] - [[themes/000 Index|Index]]

---

## Overview

**Properties**

- **interoperable with DNS**
- **decentralized name system** with secure memorable names
- delegation used to achieve transitivity (using zones of other users)
- also supports globally unique, secure identifiers (".PUBLIC-KEY")
- achieves **query and response privacy**
- **censorship-resistant**
- reliable revocation using flooding with proof-of-work
- provides alternative public key infrastructure
	- Trust paths explicit, trust agility
	- Simplified key exchange compared to [[Trust Model#The Web of Trust|Web of Trust]

![[gns.png]]

## Delegation

- Bob creates a local zone with his public key and some records (e.g. www)
- Alice learns Bob's public key and creates delegation to this zone under *label* bob
- Alice can reach Bob's webserver via "www.bob.gnu"

![[gns_delegation.png]]

## Name Resolution

![[gns_name-resolution.png]]

## Cryptography

![[gns_cryptography-terminology.png]]

![[gns_cryptography.png]]

### Cryptographic identifiers

- Zone are identified by a public key
- "alice.bob.PUBLIC-KEY" is perfectly legal in GNS $\rightarrow$ Globally unique identifiers

## Summary

**Privacy Summary**

![[DNS_summary_privacy.png]]

**Key management summary**

![[DNS_summary_key-management.png]]

**Conclusion**

- DNS - globalist
- DNSSEC - authoritarian
- Namecoin - libertarian (US)
- RAINS - nationalist
- GNS - anarchist

---
links: [[211 AC2 TOC DPKI|AC2 TOC DPKI]] - [[themes/000 Index|Index]]