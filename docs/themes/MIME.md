tags: #AC2 #smtp #mime

# MIME

links: [[209 AC2 TOC - Secure messaging and channels|AC2 TOC - Secure messaging and channels]] - [[themes/000 Index|Index]]

---

## MIME

Multipurpose Internet Mail Extensions (MIME) are extensions of the internet standard RFC 822 (replaced by RFC 5322 in 2008) which defines the format of E-Mails.

**Problems of RFC 822**

- Messages can only contain ASCII which means that binary files have to be converted (UUencode)
- Same problem for simple text since, for example, german text contains letters which are not part of 7-bit ASCII
- MTA (mail transport agent) may do strange things with messages:
	- reject messages over a certain size
	- delete, add, reorder CR and LF characters
	- truncate or wrap lines longer than 76 characters
	- remove trailing white space (tabs and spaces)
	- pad lines in a message to the same length
	- convert tab characters into multiple spaces

**Encoding**

Several encoding schemes can be used to encode arbitrary bytes (0-255) into 7-bit ASCII (Quoted-Printable, Base64 etc.). The used encoding is specified in the MIME Header. Content formats and transfer encodings in the header protect the content from alteration by the mail transfer system.

	Content-Type: image/gif
	Content-Transfer-Encoding: base64

**MIME Header Fields**

- Mandatory fields
	- MIME-Version
	- Content-Type
	- Content-Transfer-Encoding

- Optional fields
	- Content-ID
	- Content-Description

**Content types**

Tells recipient UA (User Agent) about appropriate way to deal with content (how to represent it to the user)

Top-level media types:

- discrete types: text, image, audio, video, application
- composite types
	- message (used for forwarding emails)
	- multipart (multiple different parts each with its own MIME types)

Example Multipart Message

![[Multipart.png]]

*MIME uses inbound signaling which is generally a bad idea because this allows injection attacks. It would be better to use content length*

**Quoted-Printable**

![[Quoted-Printable.png]]

## S/MIME

*GPT*:
S/MIME (Secure/Multipurpose Internet Mail Extensions) is a standard for public key encryption and signing of MIME (Multipurpose Internet Mail Extensions) data, primarily used for securing email communications. While MIME is used to support text in character sets other than ASCII, non-text attachments, multi-part message bodies, and header information, S/MIME takes it a step further by providing additional security features:

1. **Encryption**: S/MIME allows for the encryption of messages, ensuring that only the intended recipient can read the message content. This is done by using the recipient's public key to encrypt the message.
2. **Digital Signatures**: S/MIME supports the creation of digital signatures, providing a way to verify the authenticity of the sender and the integrity of the message. This is done by hashing the message content and encrypting the hash with the sender's private key.

S/MIME uses [[PKCS]]#7/CMS structures to encapsulate the signed or encrypted MIME data, allowing for nested structures when both signing and encrypting are needed. The recipient can then use the corresponding keys to decrypt the message and verify the signature

> [[PKCS]]#7 has no type to do both sign and encrypt, so nesting is used (usually first sign, then encrypt $\rightarrow$ normally we do [[Authenticated Encryption#Authenticated Encryption Schemes|encryption first, then sign]]!)

In summary, while MIME extends the capabilities of basic email to handle different types of content, S/MIME further enhances email communication by adding encryption and digital signatures to ensure confidentiality, authenticity, and integrity.

**Content-types**

- S/MIME is the standard to include [[PKCS]]#7 objects as MIME "attachments"
- there are following *Content-types*
	- Multipart/Signed (original message is signed but not enveloped $\rightarrow$ some parts can be encrypted/signed, some not)
	- Application/PKCS7-Signature (signed but not enveloped)
	- Application/PKCS7-MIME (entire message is encrypted or signed)
- content-transfer-encoding is base64

> Signed and enveloped data can be nested in any order!

**S/MIME Processing**

![[S-MIME-Processing.png]]

**S/MIME Enveloped Data**

![[S-MIME-Enveloped-Data.png]]

**S/MIME Signed Data**

![[S-MIME-Signed-Data.png]]

**S/MIME Multipart/Signed Data**

![[S-MIME-Multipart-Signed-Data.png]]

**Efail Direct exfiltration attack**

- Exploits vulnerabilities in the OpenPGP and S/MIME standards to reveal the plaintext of encrypted emails
- Abuses active content of HTML emails, for example externally loaded images or styles, to exfiltrate plaintext through requested URLs.
- Attacker first needs access to the encrypted emails, modifies it and sends this modified encrypted email to the victim.
- ﻿﻿The victim's email client decrypts the email and loads external content, thus exfiltrating the plaintext to the attacker.

![[Efail.png]]

---
links: [[209 AC2 TOC - Secure messaging and channels|AC2 TOC - Secure messaging and channels]] - [[themes/000 Index|Index]]