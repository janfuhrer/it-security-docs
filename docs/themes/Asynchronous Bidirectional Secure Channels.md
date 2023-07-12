tags: #AC2 #asymmetric  #axolotl #forward-secrecy #future-secrecy

# Asynchronous Bidirectional Secure Channels

links: [[209 AC2 TOC - Secure messaging and channels|AC2 TOC - Secure messaging and channels]] - [[themes/000 Index|Index]]

---

## Forward secrecy

If the **long-term secret key** is compromised, decryption is only possible for future sessions, not for past sessions.

## Future secrecy

If a **session key** is compromised, it doesn't affect the security of future session keys.

## Silent Circle Instant Message Protocol (SCIMP)

> Forward Secrecy

Protocol which uses hashes of the private key to encrypt data instead of using the actual key. This leads to forward secrecy because if the current key ($h_3(h_2(h_1(k)))$) gets leaked the attacker can't go back to previous hashes of the key. Past encryptions stay secure.

## Axolotl / Signal Protocol

> Forward & Future Secrecy

The protocol combines the Double Ratchet algorithm, prekeys, and a triple Elliptic-curve Diffie–Hellman ([[Secure Channels#Triple Diffie-Hellman (3DH)|3DH]]) handshake, and uses Curve25519, AES-256, and [[Cryptographic MACs#HMAC (Hash-based Message Authentication Code)|HMAC-SHA256]] as primitives.

![[Axolotl-Signal-Protocol.png]]

---
links: [[209 AC2 TOC - Secure messaging and channels|AC2 TOC - Secure messaging and channels]] - [[themes/000 Index|Index]]