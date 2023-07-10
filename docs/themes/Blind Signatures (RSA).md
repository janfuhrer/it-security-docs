tags: #asymmetric #blinding #blind-signature #RSA

# Blind Signatures (RSA)

links: [[212 AC2 TOC - GNU Taler|AC2 TOC - GNU Taler]] - [[205 AC2 TOC - Digital Signatures|AC2 TOC - Digital Signatures]] - [[themes/000 Index|Index]]

---

Blind signatures are a form of digital signature where the content of a message is disguised (blinded) before it is signed. The entity signing the message cannot see its contents, but other entities can still verify the signature.

Like this a certain degree of anonymity can be established by allowing an intermediate to sign a blinded value and letting everybody verify the signature. Since the signature is not of the original sender but the intermediate, the receiver doesn't know who actually sent the message. The intermediate party therefore acts as trusted third party where the sender trusts that the TTP doesn't reveal who he is and the receiver trusts the TTP to only sign messages from trustworthy senders. 

## Full Domain Hash (FDH)

FDH is an [[RSA]]-based signature scheme that follows the [[RSA Signature Scheme#Hash-and-Sign|hash-and-sign]] paradigm. FDH involves hashing a message using a function whose image size equals the size of the RSA modulus, and then raising the result to the secret RSA exponent.

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

### For dummies

The goal is to retrieve a valid signature for my message $m$ without letting the signer know what is signed. For this we first blind the hash of the message with the random number $r$ to gather a blinded hash. Then we send the blinded hash to the signer who signs it and sends the signed blinded hash back to me. I now can remove the parameter $r$ by calculating the inverse $r^{-1}$ multiplied the signed blinded hash $s'$ modulo $n$ to retrieve the valid signature of my unblinded message $m$. Now I send my message to the receiver who then can verify the signers signature with the signers public key. The verifier now knows that the message originates from someone who is trusted by the signer.

---
links: [[212 AC2 TOC - GNU Taler|AC2 TOC - GNU Taler]] - [[205 AC2 TOC - Digital Signatures|AC2 TOC - Digital Signatures]] - [[themes/000 Index|Index]]
