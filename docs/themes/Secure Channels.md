tags: #symmetric 

# Secure Channels

links:  [[108 AC1 TOC - From Symmetric Encryption to Secure Channels|AC1 TOC - From Symmetric Encryption to Secure Channels]] - [[themes/000 Index|Index]]

---

## What is a secure channel?

- By secure channel we refer to a logical channel running on top of some insecure link (typically the Internet) that provides
	- Confidentiality  
	- Integrity and authenticity
	- Message freshness
- Secure channels are probably one of the most important applications of crypto in the real world.
- Many well known secure network protocols such as TLS/SSL, VPNs, IPSec, WPA etc but also application specific (e.g., secure VoIP), and proprietary protocols (maybe Skype?) make use of secure channels.
- It is also possible to get it wrong, e.g., the WEP protocol has a series of security flaws.


## secure-send / secure-receive

pseudo code representing secure-send (encryption)
![[secure-send.png]]

pseudo code representing secure-receive (decryption)
![[secure-receive.png]]

- The freshness property based on counters guarantees the following: If m1, m2, . . . , mn denote the messages send using secure-send(), then secure-receive() can guarantee that the messagesm1,m2,...,mn beingreceivedaresubsequenceof the messages sent.
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

**Off-the-record (OTR) protocol**
Protocol that allows to authenticate and keep repudiation by publishing MAC keys after message is sent.
https://robertheaton.com/otr3

**3DH**
https://signal.org/blog/simplifying-otr-deniability/

---

links:  [[108 AC1 TOC - From Symmetric Encryption to Secure Channels|AC1 TOC - From Symmetric Encryption to Secure Channels]] - [[themes/000 Index|Index]]