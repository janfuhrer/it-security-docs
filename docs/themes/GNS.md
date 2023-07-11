tags: #asymmetric #GNS #GNU #DHT

# GNU Name System (GNS)

links: [[211 AC2 TOC - DPKI|AC2 TOC DPKI]] - [[themes/000 Index|Index]]

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
	- Trust paths explicit, [[trust agility]]
	- Simplified key exchange compared to [[Trust Model#The Web of Trust|Web of Trust]]

![[gns.png]]

## General

The GNU Name System GNS is specified in a [RFC](https://datatracker.ietf.org/doc/id/draft-schanzen-gns-01.html)

We can see that other than in DNS there is no centralized server which manages records. Each GNS client is part of a P2P network which maintains a [[DHT]] containing address information. In addition to the [[DHT]] also an individual zone database is kept, which stores information for address resolution. Each zone consists of a public/private ECDSA key pair. The public key also uniquely identifies the zone it defines.

## Publishing Records

To publish records, a RRBLOCK is written to the [[DHT]] by using the `PUT(key, value)` primitive such a [[DHT]] has. The `key` is derived from the zone key `zk` as follows: 
```
PRK_h := HKDF-Extract ("key-derivation", zk)
h := HKDF-Expand (PRK_h, label | "gns", 512 / 8)
d_h := h * d mod L
zk_h := h mod L * zk
q := SHA512 (zk_h) 
```

The `value` is a `RRBLOCK` which contains information about the entry. Each `RRBLOCK` starts with the signature of the block. Only the `PUBLIC-KEY` does not belong to the signature. The `PUBLIC-KEY` follows the signature. This `PUBLIC-KEY` can be used to verify the data block. After the `PUBLIC-KEY`, `SIZE`, `PURPOSE` and `EXPIRATION` follow. They define the size of the `BDATA` block, the purpose is always set to `15` (network byte order -> Big Endian -> MSB) and the expiration defines when the `RRBLOCK` should be removed from the [[DHT]]. Then follows the `BDATA` block which contains the actual information about the resource record. The `BDATA` block is encrypted using a **key `K` and an `IV` which are derived as follows**:

```
PRK_k := HKDF-Extract ("gns-aes-ctx-key", zk)
PRK_iv := HKDF-Extract ("gns-aes-ctx-iv", zk)
K := HKDF-Expand (PRK_k, label, 512 / 8);
IV := HKDF-Expand (PRK_iv, label, 256 / 8)
```

where `zk` is the zone key. ([RFC-5869 which specifies HKDF](https://www.rfc-editor.org/rfc/rfc5869.html))

## Name Resolution

The resolution of names must start with a given starting zone indicated by a `zk` public key. The resolution then recursively iterates over the to be resolved domain from right to left token by token. For each token the [[DHT]] store-key `q` is derived as [[GNS#Publishing Records|described above]]. With the derived `q` we can load entries from the [[DHT]] and recursively resolve the target. We can decrypt the encrypted `BDATA` by deriving keys as [[GNS#Publishing Records|explained above]]. The name resolution can handle `GNS2DNS` records which allow interoperability with DNS.

## How do we gain Trust agility with GNS?

Since we manage our local zone database and our lookups will start there, we can choose which paths we take to resolve an address. Maybe I will trust Cynthia more than Bob to resolve a certain domain. So I can start my lookup in the [[DHT]] with Cynthia's zone to resolve an address. But if for some reason I think Bob is more trustworthy now, I can simply update my local zone database and do my lookups over Bob's zone instead of Cynthia's. 

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
- [[X.509 CA Alternatives#Alternative 1 [DNSSEC / DANE](https //tools.ietf.org/html/rfc6698)|DNSSEC]] - authoritarian
- Namecoin - libertarian (US)
- RAINS - nationalist
- GNS - anarchist

---
links: [[211 AC2 TOC - DPKI|AC2 TOC DPKI]] - [[themes/000 Index|Index]]