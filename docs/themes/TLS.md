tags: #AC2 #symmetric #asymmetric #tls

# TLS

links: [[209 AC2 TOC - Secure messaging and channels|AC2 TOC - Secure messaging and channels]] - [[themes/000 Index|Index]]

---

## What is TLS?

Demo: [See this page fetch itself, byte by byte, over TLS](https://subtls.pages.dev/)

Transport Layer Security (TLS) is a cryptographic protocol designed to provide secure communication over a computer network. This protocol uses asymmetric cryptography to authenticate the communication parties, symmetric encryption to maintain privacy of the transmitted data, and message authentication codes for message integrity. Before TLS there was Secure Socket Layer (SSL). TLS is a successor protocol of SSL.

![[TLS.png]]

## Why does TLS use records instead of streams?

There is a [[MAC]] at the end of every record which allows the receiver to check integrity right when the record arrives. With [[Stream Cipher|stream ciphers]], if the [[MAC]] is at the end he might need to wait for the whole message to arrive before integrity can be checked. Most applications process/display data incrementally anyway.

To avoid re-order or replay attacks, a sequence number is put into the [[MAC]] (see [[Authenticated Encryption#Secure Communication Sessions|Secure Communication Sessions]])

To avoid that an attacker could truncate / cut off the TCP stream (attacker sending TCP FIN packet to sender) without the receiver noticing, *special record types are used to indicate and end of a stream.*

## What are problems of TLS?

- TLS protocol is way too complex  
- Many implementations in use  
- Vulnerabilities in protocol design and implementations (lots of attacks in the past, e.g. BEAST, CRIME, ...)
- There are different SSL/TLS modes which built "authenticated encryption" by combining auth and enc. Many attacks could have been avoided if a primitive that implements both in one was used ([[Authenticated Encryption#GCM (Galois Counter Mode)|AES-GCM]] or [[Authenticated Encryption#ChaCha20-Poly1305|ChaCha20-Poly1305]])
- Anything using [[Block Cipher#Electronic Code Block (ECB) mode|ECB]], [[Block Cipher#Cipher Block Chaining (CBC) mode|CBC]], CFB, [[Block Cipher#Output Feedback (OFB) mode|OFB]], [[Block Cipher#Counter (CTR) mode|CTR]] is likely broken (only when used on its own $\rightarrow$ CTR is used in AES-GCM)
- Even [[Authenticated Encryption#GCM (Galois Counter Mode)|AES-GCM]] could lead to problems if a nonce is actually reused (bad implementation / misuse)

**Security Requirements**

- TLS has a lot of requirements to be used securely
	- Implementation has to be secure
	- Secure cipher suite has to be used and agreed upon with other party
	- use [[X.509 certificates]]
	- Tell client you support TLS: Strict-Transport-Security header (forces HTTPS)
	- Secure certificate chains against bad CA
		- HTTP Public Key Pinning ([[X.509 CA Alternatives#Alternative 2 [HTTP PublicKey Pinning (HPKP)](https //www.owasp.org/index.php/Certificate_and_Public_Key_Pinning)|HPKP]])
		- Certificate Patrol
		- Certificate Transparency (CT)
- see [Recommendations for strong cipher configuration](https://syslink.pl/cipherlist/)

## What is keeping TLS from becoming better?

Deprecation blocks connections because older clients might only support older primitives. What percentage of clients / servers is it OK to block? Many middleboxes (firewalls, NATs, load balancers, deep packet inspection) require insecure versions too. Using primitives they don't support might break connectivity. On the other hand if old versions are supported, downgrade attacks are possible where the attacker forces the other party to use a less secure primitive.

**Example of why TLS is complex**

1. We have a version negotiation mechanism
2. Servers have broken TLS implementations on version negotiation
3. Browsers implement workaround (“protocol dance”)
4. Workaround introduces security issue (downgrade)
5. Workaround for security issue introduced by workaround gets standardized.

## TLS 1.3

TLS 1.3 is trying to break away from the attack-patch-attack-patch design cycle of previous versions. The research community is more involved to make sure the primitives are secure. It's better but there are still lots of extensions and lots of modes and the client still begins negotiation with ClientHello.

- **TLS 1.3 Full Handshake**: This is the process that a client and server go through when they're communicating for the first time, or when they can't use an existing session for some reason.

![[TLS-Full-Handshake.png]]

- **TLS 1.3 Abbreviated Handshake**: When a client and server have already established a connection in the past, the PSK can be reused & the certificate is not send to save traffic.

![[Abbreviated-Handshake.png]]

- **TLS 1.3 0-RTT Handshake**: The 0-RTT handshake allows the client to send data to the server in the very first message of the handshake, without waiting for the server to respond. This data is encrypted with keys derived from a PSK from a previous session. This reduces the latency of the handshake even further, but it has additional security considerations because the data could potentially be replayed by an attacker. As a result, 0-RTT should be used carefully and only in situations where replay attacks can be effectively mitigated.

![[0.5-RTT-Handshake.png]]

### Problems

TLS 1.3 deprecated lots of insecure ciphers but still has downgrade attack problem. X.509 certificates are still used.

---
links: [[209 AC2 TOC - Secure messaging and channels|AC2 TOC - Secure messaging and channels]] - [[themes/000 Index|Index]]