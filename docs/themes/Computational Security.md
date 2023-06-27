tags: #symmetric
links:  [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---
# Computational Security

*Computational Security* definitions take into account computational limits on an attacker, and allow for a small probability that security is violated.

**Relaxations relative to information-theoretic notions of security**

1. Security is only guaranteed against **efficient** adversaries that run for some feasible amount of time. If we can make the resources required to break the scheme larger than those available to any realistic attacker, however, then for all practical purposes the scheme is unbreakable.
2. Adversaries can potentially succeed with some **very small probability**. If we can make this probability sufficiently small, we need not worry about it.

### The Concrete Approach

The security of a cryptographic scheme by explicitly bounding the maximum success probability of a (randomized) adversary running for some specified amount of time (or amount of computational effort).

**Conclusion**

- Gives concrete guarantees for security of scheme
- concrete guarantees are difficult to provide: 
	- an adversary running for 5 years can break a given scheme with probability better than $\varepsilon$ $\rightarrow$ what type of computing power does this assume? Do we have dedicated hardware for some algorithms? ...

### The Asymptotic Approach

If we describing schemes abstractly, it is convenient to use the *asymptotic* approach. This approach, rooted in complexity theory, introduces the **security parameter**, denoted by $n$.

> A scheme is **secure**, if any $PTT$ adversary succeeds in breaking the scheme with at most negligible probability.

Viewing the security parameter as the key length, this corresponds to the fact that the time required for an exhaustive-search attack grows exponentially in the length of the key.

### Defining Computationally Secure Encryption

> A **private-key encryption scheme** consists of three probabilistic polynomial-time algorithms $(Gen, Enc, Dec)$ such that:
> 
> 	1. $k \leftarrow Gen(1^n)$: the key-generation algorithm takes as input $1^n$ ($n$ is security parameter)
> 	2. $c \leftarrow Enc_k(m)$: the encryption algorithm takes as input a key $k$ and a plaintext message $m$. $Enc$ may be randomized.
> 	3. $m := Dec_k(c)$: the decryption algorithm takes as input a key $k$ and a ciphertext $c$ and outputs a message or an error (denoted by $\bot$)

---

### Definitions

- $PTT$ stands for *Probabilistic polynomial-time*
- **Negligible success probability**: A negligible function is one that is asymptotically smaller than any inverse polynomial function $f(n) < \frac{1}{p(n)}$

---
links:  [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]