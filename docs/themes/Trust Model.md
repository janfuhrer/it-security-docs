tags: #asymmetric 

# Trust Model

links: [[211 AC2 TOC DPKI|AC2 TOC DPKI]] - [[themes/000 Index|Index]]

---

## Trust on First Use (TOFU)

- client creates a trust relationship with a not-yet-trusted and unknown endpoint
- the public key of the endpoint is not verified, but subsequent connections to the same peer require that the information & key remain the same
- Used in **SSH** and in **HTTP Public Key Pinning (HPKP)**

## The Web of Trust

- Alice has certified many of her contacts and *flagged* some as *trusted*
- Bob has been certified by many of his contacts
- Alice has **not** yet certified Bob, but wants to securely communicate with him
- **Web of Trust**: find paths in the certification graph

![[web-of-trust.png]]

## Certificate Trust Models

- **Direct Trust**
	- one trust in a relationship between "public key" and "identity"
	- verified by itself (directly/personally)
	- $\rightarrow$ zero-solution: key management is complex, legal validity/liability not possible
- **Web of Trust**
	- one accepts "public keys", where the identity binding is validated by others
	- accept other entities as trustworthy authorities
	- $\rightarrow$ Flexible solution: usable in bigger scope (e.g. community), online key server, legal validity/liability not possible
- **Hierarchical Trust**
	- one accepts "public keys", where the identity binding is validated by trustworthy authority
	- $\rightarrow$ Strict solution: only validated keys by authority, national or global scope, key management complex, legal validity/liability possible

---
links: [[211 AC2 TOC DPKI|AC2 TOC DPKI]] - [[themes/000 Index|Index]]