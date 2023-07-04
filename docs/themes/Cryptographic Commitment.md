tags: #symmetric #commitment #commitment-scheme

# Cryptographic Commitment

links: [[105 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[themes/000 Index|Index]]

---

## Definition

A *commitment scheme* allows one party to "commit" to a value $m$ by sending a commitment $com$ and then to reveal $m$ (by "opening" the commitment) at a later point in time.

- *Hiding*: the commitment $com$ reveals nothing about $m$
- *Binding*: it is infeasible for the committer to output a commitment $com$ that it can later "open" as two different messages $m, m'$ (commitment is truly on one value).

## Properties

- **Perfect hiding**: The commitment provides unconditional security, i.e. is completely hidden from any adversary, regardless of the computational resources available to them.
- **Conditional hiding**: The commitment is hard to be opened/ revealed if the secret is unknown. The committed value is hidden in such a way that an adversary with limited computational resources cannot determine the value with a probability that is significantly better than random guessing.
- **Perfect binding**: The commitment can only be opened/ revealed to a single $m$. The committed value is perfectly secure against any type of change-attack, including those using unbounded computational power. It is impossible to change it without being detected.
- **Conditional binding**: The commitment is hard to be changed without being detected. The committed value is bound in such a way that an adversary with limited computational resources cannot change the value without being detected.

**Can you achieve perfect hiding and binding at the same time?**

The reason a scheme can't be both perfectly hiding and perfectly binding is essentially due to an information-theoretic argument. If it's perfectly hiding, an attacker with unbounded computational power could try every possible value until they found one that matched the commitment, thereby breaking the binding. On the other hand, if it's perfectly binding, then it must be possible, in theory, to extract the committed value from the commitment, thereby breaking the hiding property.

### Example

Example of a commitment scheme based on a sponge function:

- $m$: message
- $r$: random bit string
- $c$: output/ commitment
- function: $c := H(r \parallel m)$

![[commitment_scheme_example.png]]

---
links: [[105 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[themes/000 Index|Index]]