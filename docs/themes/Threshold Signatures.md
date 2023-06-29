tags: #symmetric #private-key

# Threshold Signatures

links: [[109 AC1 TOC - Secret sharing|AC1 TOC - Secret sharing]] - [[themes/000 Index|Index]]

---

We assume the following:

> Everything is Broken!

Alice wants to create a cryptographic signature but:
- No single piece of hardware is trusted
- No single service provider is trusted

> But there is hope: Using $t$ independent signature service providers might be ok!

If we need $t$ providers we should sign up with $n$ providers initially so we can still create signatures if only $t/n$ are available.

## FROST

Flexible Round-Optimized Schnorr Threshold (FROST) is a t-out-of-n threshold signature scheme.

- Threshold signature schemes exist to facilitate shared ownership of a private key. Using a set of participants such that a threshold number of the set must cooperate to issue a signature. 
- $t$ of this set of $n$ participants must work collaboratively to create the digital signature.

## FROSIX

Free Software implementation of the threshold signature scheme using FROST.

- REST API to interact between signer and signing services
- Configurable authentication methods to authorize creation of signature
- To avoid single point of failure the client should still use multiple devices
- Command-Line tool to interact with FROSIX service providers

---
links: [[109 AC1 TOC - Secret sharing|AC1 TOC - Secret sharing]] - [[themes/000 Index|Index]]