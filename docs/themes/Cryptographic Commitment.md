tags: #symmetric #commitment #commitment-scheme

# Cryptographic Commitment

links:  [[106 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[themes/000 Index|Index]]

---

## Definition

A *commitment scheme* allows one party to "commit" to a value $m$ by sending a commitment $com$ and then to reveal $m$ (by "opening" the commitment) at a later point in time.

## Properties

- **Perfect hiding**: The commitment can be opened/revealed 

- *Perfect Hiding*: the commitment $com$ reveals nothing about $m$
- *Binding*: it is infeasible for the committer to output a commitment $com$ that it can later "open" as two different messages $m, m'$ (commitment is truly on one value).

---
links:  [[106 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[themes/000 Index|Index]]