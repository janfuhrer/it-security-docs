tags: #symmetric #secure-channel #repudiation #non-repudiation #OTR #off-the-record #forward-secrecy

# Secure Channels

links: [[107 AC1 TOC - Secure Channels|AC1 TOC - From Symmetric Encryption to Secure Channels]] - [[themes/000 Index|Index]]

---

## What is a secure channel?

- By secure channel we refer to a logical channel running on top of some insecure link (typically the Internet) that provides
	- Confidentiality  
	- Integrity and authenticity
	- Message freshness
- Secure channels are probably one of the most important applications of crypto in the real world.
- Many well known secure network protocols such as TLS/SSL, VPN, IPSec, WPA etc. but also application specific (e.g., secure VoIP), and proprietary protocols (maybe Skype?) make use of secure channels.
- It is also possible to get it wrong, e.g. the WEP protocol has a series of security flaws.

## secure-send / secure-receive

pseudo code representing secure-send (encryption):

![[secure-send.png]]

pseudo code representing secure-receive (decryption):

![[secure-receive.png]]

- The **freshness property** based on counters guarantees the following: If $m1, m2, . . . , mn$ denote the messages send using secure-send(), then secure-receive() can guarantee that the messages $m1,m2,...,mn$ being received are sub sequence of the messages sent.
- Counters give **no timing guarantees**, i.e. the adversary Mallory can delay messages at will.
- Timing guarantees can be achieved using
	- Time-stamps
	- Challenges
- No security protocol can prevent Mallory from discarding messages.
- MACs provide not just integrity protection but also authenticity, as discussed earlier.
- Typically, secure-send() and secure-receive() are run by both parties using a secure channel.
- Each party will have an independent key-pair (enc & MAC).
- In practice, one introduces the notion of a session (e.g. e-banking). Consists of a session ID in the header, which allows the receiver to look-up session state (keys, counters etc.) when receiving a message.
- Generally better is the use of authenticated encryption, where the block-cipher mode guarantees confidentiality and integrity.

## Repudiation vs. non-repudiation

- Digital signatures allow proving that someone said something
- Alice may be happy to authenticate to Bob, but not to Eve or Mallory!
- Bob may turn “evil” and use Alice’s statements against her later
- Signatures may provide too much (authentication and non-repudiation)

### Off-the-record (OTR) protocol

Protocol that allows to authenticate and **keep repudiation** by publishing [[MAC]] keys after message is sent.

Achieved using two signatures and a DH handshake.

## How OTR works

see [How OTR Works](https://robertheaton.com/otr3)

1. Each participant has a long-term identity key (A and B) that they use to sign an ephemeral key (a and b), which they exchange and use to calculate a shared secret. 
2. The shared secret from this key exchange is used to derive a sending and receiving cipher key for each party, as well as a set of [[MAC]] keys for each party.
3. Every transmitted message includes a [[MAC]], which the message’s recipient can verify.

Since the key used to construct and verify the [[MAC]] was derived from the shared secret, and since the shared secret was derived from a key exchange that was in turn signed by the sender’s long-term identity key, the recipient can be sure that the message was really constructed by their peer in the conversation.

The message is “deniable,” however, because the MAC keys are derived from a _shared_ secret. Unlike PGP signatures, where the sender is the only person capable of producing the signature, the recipient of an OTR message is _also_ capable of producing a sender’s MAC. This doesn’t compromise the integrity of the conversation for its participants, but does prevent a message’s recipient from revealing the MAC’d message to a third party as proof that it was produced by the sender, since it could have just as easily been constructed by the recipient themselves.

### Triple Diffie-Hellman (3DH)

Replaces the two DSA signatures from OTR and does everything with 3 DH key exchanges.

* A: Public Identity (Key) Alice
* B: Public Identity (Key) Bob
* a: Ephemeral key Alice
* b: Ephemeral key Bob


![[3DH.png]]

**But wait how is there authenticity? -- There is not**

Before or after an X3DH key agreement, the parties may compare their identity public keys A and B through some authenticated channel. For example, they may compare public key fingerprints manually, or by scanning a QR code. _Methods for doing this are outside the scope of this document._

_If authentication is not performed, the parties receive no cryptographic guarantee as to who they are communicating with._ [Signal Documentation](https://signal.org/docs/specifications/x3dh/)

**Advantages**

- **Reduced Algorithmic Complexity**: eliminated DSA, only DH now
- **Increased Forgability**: no signatures involved $\rightarrow$ Now anyone is capable of easily producing a forged message from anyone else, whether they’ve actually had a conversation with them before or not.
- **Reduced Protocol Complexity**
- **Maintained Forward Secrecy**
- **Smaller Payloads**

see [Simplifying OTR Deniability](https://signal.org/blog/simplifying-otr-deniability/)

**Some more details**

If Alice's private key $(a, T_a)$ is compromised in the 3DH protocol, the attacker could not only decrypt messages meant for Alice, but could also impersonate Alice in her communications. This is because Alice's private key is used both to decrypt messages sent to her and to create a digital signature that verifies her identity. If an attacker has access to Alice's private key, they can forge this digital signature and send messages that appear to be from Alice.

Compromising Alice's private key would not allow an attacker to decrypt past session keys, because 3DH provides forward secrecy. **Forward secrecy** is a feature of specific key agreement protocols that ensures that even if the private key is compromised, past session keys will not be compromised. Each session key is generated independently with a unique ephemeral key pair, so even if Alice's long-term private key is compromised, the session keys used for past secure communications would remain secure.

---
links: [[107 AC1 TOC - Secure Channels|AC1 TOC - From Symmetric Encryption to Secure Channels]] - [[themes/000 Index|Index]]