tags: #symmetric #hash

# Hash Functions

links: [[themes/106 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

> Hash functions are simply functions that take inputs of some length and *compress* them into short, fixed-length outputs.

Hash functions can be viewed as lying between the worlds of private- and public-key cryptography, because they have important applications in both settings.

**Cryptographic Hash Functions**

- a hash function with a fixed output length
- has to be deterministic
- Collision resistant (wich implies pre-image- and second-image resistant)
- hash must therefore be a "one way" function

## Collision Resistance

- a function $H$ is *collision resistant* if it is infeasible for any probabilistic polynomial-time algorithm to find a collision in $H$.
- The domain of a hash function is normally larger than their range $\rightarrow$ in this case collisions *must exist*, but such collisions should be hard to find.

## Keyed hash functions

- **Keyed hash functions**: $H$ takes as input a key $s$ and a string $x$ and outputs a string $\rightarrow$ the key is generally not kept secret!
- Cryptographic hash functions used in practice are generally *unkeyed* and have a fixed output length

## Weaker Notions of Security

**Second-preimage resistance**

We have $x$ and cannot find a $x'$ wich results to the same Hash $y$ for both $x$ and $x'$

**Preimage resistance**

$H$ is one-way, if we have $y$ ($y = H(x)$) we cannot go back to find a $x'$ to compute $y$

## Compress Functions

### Merkle-Damgård Transform

- maps inputs of arbitrary length to outputs of length $n$

![[merkle_damgard_transform.png]]

### Davies-Meyer

- Davies-Meyer is a compress function from a block cipher
- $F$ is a strong pseudorandom permutation

![[davies_meyer-construction.png]]

## Attacks on Hash Functions

- in symmetric-key using an $n$-bit secret key is vulnerable to a *brute-force attack* in which an attacker enumerates all $2^n$ possible keys
- for a hash function $H$ to be collision resistant against attackers running in time $2^n$ it is required that $H$ have **output at least $2n$ bits long**

### Birthday attacks

- if $q$ people are in a room, what is the probability that some two of them share a birthday? $\rightarrow$ matching birthdays correspond to collisions
- if $H$ has an output length of $l$, $q = \Theta(2^{l/2}) \rightarrow$ **yields a collision with probability roughly $1/2$** 

## Universal Hash Function

> Universal hashes can be extremely cheap to evaluate - much cheaper than block ciphers, pseudorandom functions, and especially collision-resistant hashes.
> (...)
> Universal hashing gives us strong guarantees with extremely cheap options

- selecting a hash function at random from a family of hash functions with a certain mathematical property
- Example of universal hash families: [[Cryptographic MACs#GMAC (Galois Message Authentication Code)|GMAC]] or [[Cryptographic MACs#Poly1305|Poly1305]]

Source: [Link](https://crypto.stackexchange.com/a/67639)

---
links: [[themes/106 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]