tags: #symmetric #mac #hash

# Hash-and-Mac

links: [[themes/106 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

## General Construction

- use a fixed-length MAC for $l(n)$-bit messages and a collision-resistant hash function with $l(n)$-bit output length
- Then we can authenticate an arbitrary-length message $m$ by using the MAC to authenticate the *hash* of $m$
- This is secure because the MAC ensures that the attacker cannot authenticate any new hash value, while collision resistance ensures that the attacker will be unable to find any new message that hashes to a previously used hash value

**Formal description**

- $Mac$:  takes as input the keys $k$ and $s$ and a message $m$, outputs $t \leftarrow Mac_k(H^s(m))$
- $Vrfy$: takes as input the keys $k$ and $s$, a message $m$ and a tag $t$, output 1 iff $Vrfy_k(H^s(m), t) \stackrel{?}{=} 1$

**Drawbacks**

- implementing two cryptography primitives: a hash function and a block cipher (for MAC)
- mismatch between the output length of hash functions and the block length of block ciphers $\rightarrow$ AES with 128-bit block, but hash has to be at least 256 bits for a meaningful collision resistance

## HMAC

- see [[Cryptographic MACs#HMAC (Hash-based Message Authentication Code)|HMAC]]

## Attacks

### Length-Extension Attack

- see article on https://github.com/marcelo140/length-extension

The length-extension attack allows an attacker to extend the length of a given hash value, without knowing the original message or the secret key. By appending additional data to the hash output and calculating a new MAC, the attacker can generate valid MACs for extended messages, potentially leading to unauthorized access or forgery.