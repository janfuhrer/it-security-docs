tags: #AC2 #exercise 

# WEP Insecurity

links: [[209 AC2 TOC - Secure messaging and channels|AC2 TOC - Secure messaging and channels]] - [[themes/000 Index|Index]]

---

Read the Article "Intercepting Mobile Communications: The Insecurity of 802.11" ([[WEP-mobicom.pdf]])

- **Keystream reuse**: Capture ciphertexts with the same IV and key $\rightarrow$ if we know some of the one plaintext, we can easily compute the other plaintext
- **Decryption Dictionaries**: the size of the dictionary depends of the size of the IV, not the key length $\rightarrow$ only 24bit!
- **Key Management**: use 4 keys $\rightarrow$ most installations use a single key for all connections
- **Message Modification**: messages can be modified without fear of detection $\rightarrow$ is also possible for unknown messages (XOR message & CRC)
- **Message Injection**: Knowledge of plaintext & ciphertext reveals the keystream $\rightarrow$ with one keystream, we can send any packet with the same IV (which is allowed)

![[WEP-Insecurity-Solution.png]]

---
links: [[209 AC2 TOC - Secure messaging and channels|AC2 TOC - Secure messaging and channels]] - [[themes/000 Index|Index]]