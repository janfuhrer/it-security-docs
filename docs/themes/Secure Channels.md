tags: #symmetric #secure-channel #repudiation #non-repudiation #OTR #off-the-record #forward-secrecy

# Secure Channels

links: [[107 AC1 TOC - From Symmetric Encryption to Secure Channels|AC1 TOC - From Symmetric Encryption to Secure Channels]] - [[themes/000 Index|Index]]

---

## What is a secure channel?

- By secure channel we refer to a logical channel running on top of some insecure link (typically the Internet) that provides
	- Confidentiality  
	- Integrity and authenticity
	- Message freshness
- Secure channels are probably one of the most important applications of crypto in the real world.
- Many well known secure network protocols such as TLS/SSL, VPN, IPSec, WPA etc but also application specific (e.g., secure VoIP), and proprietary protocols (maybe Skype?) make use of secure channels.
- It is also possible to get it wrong, e.g., the WEP protocol has a series of security flaws.


## secure-send / secure-receive

pseudo code representing secure-send (encryption):

![[secure-send.png]]

pseudo code representing secure-receive (decryption):

![[secure-receive.png]]

- The freshness property based on counters guarantees the following: If m1, m2, . . . , mn denote the messages send using secure-send(), then secure-receive() can guarantee that the messages m1,m2,...,mn being received are sub sequence of the messages sent.
- Counters give no timing guarantees, i.e., the adversary Mallory can delay messages at will.
- Timing guarantees can be achieved using
	- Time-stamps
	- Challenges
- No security protocol can prevent Mallory from discarding messages.
- MACs provide not just integrity protection but also authenticity, as discussed earlier.
- Typically, secure-send() and secure-receive() are run by both parties using a secure channel.
- Each party will have an independent key-pair (enc & MAC).
- In practice, one introduces the notion of a session (e.g., e-banking). Consists of a session ID in the header, which allows the receiver to look-up session state (keys, counters etc.) when receiving a message.
- Generally better is the use of authenticated encryption, where the block-cipher mode guarantees confidentiality and integrity.


## Repudiation vs. non-repudiation

- Digital signatures allow proving that someone said something
- Alice may be happy to authenticate to Bob, but not to Eve or Mallory!
- Bob may turn “evil” and use Alice’s statements against her later
- Signatures may provide too much (authentication and non-repudiation)

### Off-the-record (OTR) protocol

Protocol that allows to authenticate and keep repudiation by publishing MAC keys after message is sent.

Achieved using two signatures and a DH handshake.

[How OTR Works](https://robertheaton.com/otr3)

### Triple Diffie-Hellman (3DH)

Replaces the two signatures from OTR and does everything with 3 DH key exchanges.

[Simplifying OTR Deniability](https://signal.org/blog/simplifying-otr-deniability/)

If Alice's private key $(a, T_a)$ is compromised in the 3DH protocol, the attacker could not only decrypt messages meant for Alice, but could also impersonate Alice in her communications. This is because Alice's private key is used both to decrypt messages sent to her and to create a digital signature that verifies her identity. If an attacker has access to Alice's private key, they can forge this digital signature and send messages that appear to be from Alice.

Compromising Alice's private key would not allow an attacker to decrypt past session keys, because 3DH provides forward secrecy. **Forward secrecy** is a feature of specific key agreement protocols that ensures that even if the private key is compromised, past session keys will not be compromised. Each session key is generated independently with a unique ephemeral key pair, so even if Alice's long-term private key is compromised, the session keys used for past secure communications would remain secure.

---
links: [[107 AC1 TOC - From Symmetric Encryption to Secure Channels|AC1 TOC - From Symmetric Encryption to Secure Channels]] - [[themes/000 Index|Index]]