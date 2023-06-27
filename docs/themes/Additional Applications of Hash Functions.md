tags: #symmetric

# Additional Applications of Hash Functions

links:  [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

## Fingerprinting and Deduplication

- use hash (or digest) as fingerprint of a file, used e.g. for
	- *Virus fingerprinting*: compare only hash of a file with a hash database of virus-files
	- *Deduplication*: eliminate duplicate copies of data, only store once
	- *Peer-to-peer (P2P) file sharing*: server store files and broadcasting the hashes of those files, allow client to easily find out on which servers host a file is

## Password Hashing

One of the most common and important uses of hash functions in computer security is for password protection. to authenticate a user, some form of the user's password has to be stored. To mitigate the risk of stolen passwords, only a hash of the password can be stored instead of the password itself. Operating systems or web services only checks whether $H(PW) \stackrel{?}{=} hpw$.
The hash functions should be "moderately hard to compute" when evaluated once (e.g. on a client/server side) but prohibitively expensive to evaluate tens of thousands of times.

**Rainbow Tables**

A so called "rainbow table" refers to a precomputed table that contains the password hash value for some (or all possible) strings in a domain. This tabes only need to be generated once and is highly effective at recovering passwords.

**Salt**

To mitigate the problem of rainbow tables, we can introduce a *salt*. When a user registers their password, the laptop/server will generate a long random value $s$ (a "salt") unique to that user, and store ($s, hpw = H(s,pw)$) instead of merely storing $H(pw)$. Since $s$ is unknown to the attacker in advance, preprocessing is ineffective and a separate brute-force search is needed to recover each user's password.


## Key Derivation

> a key-derivation function provides a way to obtain a (close to) uniformly distributed string from any distribution with high min-entropy.

## Commitment Schemes

A *commitment scheme* allows one party to "commit" to a value $m$ by sending a *commitment* $com$, and then to reveal $m$ (by "opening" the commitment) at a later point in time.

**Properties**

- *Hiding*: the commitment $com$ reveals nothing about $m$
- *Binding*: it is infeasible for the committer to output a commitment $com$ that it can later "open" as two different messages $m, m'$ (commitment is truly on one value).

---
links:  [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]