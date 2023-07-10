tags: #asymmetric 

# Blind Signatures (RSA)

links: [[212 AC2 TOC - GNU Taler|AC2 TOC - GNU Taler]] - [[205 AC2 TOC - Digital Signatures|AC2 TOC - Digital Signatures]] - [[themes/000 Index|Index]]

---

Blind signatures are a form of digital signature where the content of a message is disguised (blinded) before it is signed. The entity signing the message cannot see its contents, but other entities can still verify the signature.

## Full Domain Hash (FDH)

FDH is an RSA-based signature scheme that follows the hash-and-sign paradigm. FDH involves hashing a message using a function whose image size equals the size of the RSA modulus, and then raising the result to the secret RSA exponent.

## Blinding

1. Obtain the public key of the signer: $(e, n)$
2. Hash the message using FDH: $h := FDH(m)$
3. Pick a blinding factor: $r \in \mathbb{Z}_n$
4. Send blinded hash to the signer: $h' := hr^e \mod n$

## Signing

1. Receive blinded hash: $h'$
2. Compute signature: $s' := h'^d \mod n$
3. Send signed hash back: $s'$

## Unblinding

1. Receive signed hash: $s'$
2. Unblind: $s := s'r^{-1} \mod n$

---
links: [[212 AC2 TOC - GNU Taler|AC2 TOC - GNU Taler]] - [[205 AC2 TOC - Digital Signatures|AC2 TOC - Digital Signatures]] - [[themes/000 Index|Index]]
