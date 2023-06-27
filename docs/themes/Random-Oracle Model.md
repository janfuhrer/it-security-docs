tags: #symmetric
links:  [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---
# Random-Oracle Model

### Idealized Model

An approach that has been hugely successful in practice, and which offers a "middle ground" between a fully rigorous proof of security on the one hand and no proof whatsoever on the other, is to introduce an *idealized model* in which to prove the security of cryptographic schemes. A popular example of this approach is the *random-oracle model*, which treats a cryptographic hash function as a truly random function.

### The Random Oracle Model

> The random-oracle model posits the existence of a public, random function $H$ that can be evaluated only by "querying" an oracle.

The oracle is simply a "black box" that takes a bit-string as input and returns a bit-string as output. The internal workings of the box are unknown and inscrutable. Everyone (including the adversary), can interact with the box. The box is **consistent**, if the box ever outputs $y$ for a particular input $x$, then it always outputs the same answer $y$ when given the same input again.

$H$ can either be viewed as being chosen the outputs "**in one shot**" uniformly from the set of all functions or "**on-the-fly**" as needed. In the second case we can view the function as being defined by a table that is initially empty. When the oracle receives a query $x$ it first checks whether $x$ is already in the table and otherwise chose a uniform string $y$, returns it and store it in the table.

The hope is that the cryptographic hash function used is "sufficiently good" at emulating a random oracle.

**Random oracle vs. pseudorandom functions**

- A pseudorandom function is only pseudorandom if the key is *secret*. In the random oracle model all parties need to be able to compute the function, thus there can be no secret key.
- In the random oracle model, the random function is used as part of a construction itself

**Problems**

- its not clear what it means for a hash function to be "sufficient good" at emulating a random oracle, nor is it clear that this is an achievable goal.
- $H$ is always fixed and its code is known, so a proof of security in the oracle model is not a rigorous proof that any real-world instantiation of the scheme is secure.
- there is currently debate within the cryptographic community about how to interpret proofs in the random-oracle model.

---
links:  [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]