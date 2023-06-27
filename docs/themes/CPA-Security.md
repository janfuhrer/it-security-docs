tags: #symmetric #cpa

# CPA-Security

links:  [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

The attacker can e.g. influence and observe what messages get encrypted. At some later point in time, the attacker observes a ciphertext corresponding to some unknown message encrypted using the same key $k$. Let us even assume that the attacker knows that $m$ is one of two possibilities $m_0, m_1$. Security against CPA means that even in this case the attacker cannot tell which of those two messages was encrypted with probability significantly better than random guessing.

**Example**

A simple example is given by an attacker typing on a terminal, which in turn encrypts everything the adversary types using a key (unknown to the attacker) shared with a remote server. Here the attacker exactly controls what gets encrypted, and the encryption scheme should still reveal nothing when it is used—with the same key—to encrypt data typed by another user.

**Take aways**

- CPA-security is nowadays the minimal notion of security an encryption scheme should satisfy
- Any private-key encryption scheme that is CPA-secure is also CPA-secure for **multiple** encryptions

## Constructing a CPA-Secure Encryption Scheme

### Pseudorandom Functions and Permutations

*Pseudorandom functions (PRFs)* generalize the notion of pseudorandom generators. Now, instead of considering "random-looking" *strings* we consider "random-looking" *functions*.

> A pseudorandom function is a keyed function $F$ such that $F_k$ (for uniform $k \in {0, 1}^n$) is indistinguishable from $f$ (for uniform $f \in Func_n$)

### CPA-Security from a Pseudorandom Function

- uses **randomized encryption**: applying a pseudorandom function to a *random value* $r \in {0,1}^n$ 
- the ciphertext includes both the result as well as $r$ (to enable the receiver to decrypt)
- a *fresh* pseudorandom pad - that depends on $r$ - is used each time a message is encrypted
- for any key $k$, every message $m$ has $2^n$ corresponding ciphertexts
- encryption for fixed length messages
- *Example*: $r$ is the IV/nonce, the seed/key is used for the pseudorandom function (as in the EAV construction)

![[cpa_with_prf.png]]

**Construction**

- $Enc$: $c := \langle r, F_k(r) \oplus m \rangle$
- $Dec$: ciphertext $c = \langle r,s \rangle$ output message $m := F_k(r) \oplus s$

---

### Definitions
- $Func_n$: set of all functions mapping $n$-bit strings to $n$-bit strings.

---
links:  [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]