tags: #AC2 #asymmetric 

# Asynchronous Bidirectional Secure Channels

links: [[209 AC2 TOC - Secure messaging and channels|AC2 TOC - Secure messaging and channels]] - [[themes/000 Index|Index]]

---

## Forward secrecy

*GPT*
Forward secrecy is a property of secure communication protocols where the compromise of long-term keys does not lead to the compromise of past session keys and consequently, past sessions remain secure. Long-term keys, typically private keys used in the key exchange or key agreement process, are keys that remain constant over a long period and are used across multiple sessions. If an attacker gets hold of a user's long-term private key, they would ideally be able to decrypt all past and future communication sessions. However, with forward secrecy, even if an attacker manages to compromise a user's long-term private key, they cannot decrypt past sessions. This is because each session uses a unique session key, generated for that specific session and discarded afterward. These session keys are generated in a way that even someone with the long-term private key cannot retrospectively compute them.


## Future secrecy

*GPT*
Future secrecy is a property that ensures that if a session key is compromised, it doesn't affect the security of future session keys. Session keys, also known as ephemeral keys, are temporary keys used for a single session and discarded afterward. If an attacker manages to compromise a session key (for instance, by exploiting a vulnerability in the system or through some form of side-channel attack), they would be able to decrypt the contents of that particular session. However, with future secrecy, this compromise doesn't allow them to compromise any future sessions, even if the long-term private key remains the same. This is because future session keys are generated involving fresh randomness, making them independent of the compromised session key.

## **Silent Circle Instant Message Protocol** (SCIMP)

Protocol which uses hashes of the private key to encrypt data instead of using the actual key. This leads to forward secrecy because if the current key ($h_3(h_2(h_1(k)))$) gets leaked the attacker can't go back to previous hashes of the key. Past encryptions stay secure.


## Axolotl / Signal Protocol

![[Axolotl-Signal-Protocol.png]]

---
links: [[209 AC2 TOC - Secure messaging and channels|AC2 TOC - Secure messaging and channels]] - [[themes/000 Index|Index]]