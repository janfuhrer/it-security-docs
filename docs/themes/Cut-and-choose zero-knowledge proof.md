tags: #asymmetric 

# Cut-and-choose zero-knowledge proof

links: [[212 AC2 TOC GNU Taler|AC2 TOC GNU Taler]] - [[themes/000 Index|Index]]

---

The general idea is that the prover prepares several instances of the proof and the verifier "cuts" a subset of them to check, while the remaining instances are used to construct the proof. If the prover is cheating, they would have to cheat on all instances to be sure of not being caught, which makes the protocol more robust.

- The **commitment** phase is where some evidence is provided, but not enough to convince a verifier or reveal the secret.
- The **cut-and-choose** phase is where the verifier randomly checks some of this evidence, and the prover has no way to know in advance which part will be checked.
- The **proof** phase is where the prover demonstrates knowledge related to the unchecked evidence.

A cut-and-choose proof does not guarantee to 100% that you counterpart did not lie. It's just a probability.

In Taler for example your money is taken in case you are caught lying. So it's not economical to lie as you will always loose money in the long term.

---
links: [[212 AC2 TOC GNU Taler|AC2 TOC GNU Taler]] - [[themes/000 Index|Index]]