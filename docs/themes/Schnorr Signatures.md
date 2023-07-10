tags: #asymmetric 

# Schnorr Signatures

links: [[212 AC2 TOC - GNU Taler|AC2 TOC - GNU Taler]] - [[205 AC2 TOC - Digital Signatures|AC2 TOC - Digital Signatures]] - [[themes/000 Index|Index]]

---

Way nicer and simpler than [[DSA Signature Scheme|DSA/ECDSA]].

Hint: For elliptic curves we use additive notation for groups

* $G$ : base point of the elliptic curve
* $q$ : order of the elliptic curve
* $\mathbb{Z_q}$ : Set of integers modulo $q$
* $d$ : private key
* $P$ : public key
* $m$ : message

## Key Generation

1. Generate private key: $d \leftarrow \mathbb{Z_q}$
2. Calculate public key: $P = dG$

## Signature Generation

Sign message $m$

1. Generate random nonce: $r \leftarrow \mathbb{Z_q}$
2. Compute point: $R = rG$
3. Hash nonce (x-coordinate) and message: $e = H(Rx\;||\;m)$
4. Compute $s = r - ed \mod q$
5. The signature is: $(s, e)$

## Signature Verification

Verify a signature $(s,e)$ on a message $m$ with the public key $P$

1. Compute: $R' = sG + eP$
2. Compute: $e' = H(R'x\;||\;m)$
3. Signature is valid if $e' = e$

Schnorr signatures have several appealing properties, including:

- **Provable Security**: Schnorr signatures have a strong security proof in the random oracle model.
- **Efficiency**: Schnorr signatures involve relatively efficient computational operations.
- **Non-malleability**: It's computationally infeasible to modify a Schnorr signature into a valid signature for a different message or a different signer.
- **Linearity**: Schnorr signatures have a linear structure, which allows for multi-signature (group of signers signs a message) and threshold signature schemes.

---
links: [[212 AC2 TOC - GNU Taler|AC2 TOC - GNU Taler]] - [[205 AC2 TOC - Digital Signatures|AC2 TOC - Digital Signatures]] - [[themes/000 Index|Index]]
