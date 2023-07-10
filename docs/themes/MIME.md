tags: #AC2

# MIME

links: [[209 AC2 TOC - Secure messaging and channels|AC2 TOC - Secure messaging and channels]] - [[themes/000 Index|Index]]

---

## MIME

Multipurpose Internet Mail Extensions (MIME) are extensions of the internet standard RFC 822 (replaced by RFC 5322 in 2008) which defines the format of E-Mails.

**Problems of RFC 822**
- Messages can only contain ASCII which means that binary files have to be converted (UUencode)
- Same problem for simple text since, for example, german text contains letters which are not part of 7-bit ASCII
- MTA (mail transport agent) may do strange things with messages
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

*GPT*
S/MIME (Secure/Multipurpose Internet Mail Extensions) is a standard for public key encryption and signing of MIME (Multipurpose Internet Mail Extensions) data, primarily used for securing email communications. While MIME is used to support text in character sets other than ASCII, non-text attachments, multi-part message bodies, and header information, S/MIME takes it a step further by providing additional security features:

1. **Encryption**: S/MIME allows for the encryption of messages, ensuring that only the intended recipient can read the message content. This is done by using the recipient's public key to encrypt the message.
2. **Digital Signatures**: S/MIME supports the creation of digital signatures, providing a way to verify the authenticity of the sender and the integrity of the message. This is done by hashing the message content and encrypting the hash with the sender's private key.

S/MIME uses PKCS#7/CMS structures to encapsulate the signed or encrypted MIME data, allowing for nested structures when both signing and encrypting are needed. The recipient can then use the corresponding keys to decrypt the message and verify the signature.

In summary, while MIME extends the capabilities of basic email to handle different types of content, S/MIME further enhances email communication by adding encryption and digital signatures to ensure confidentiality, authenticity, and integrity.

**Content-types**
*GPT*
S/MIME uses specific content types to denote the kind of cryptographic protection applied to a MIME message. These content types are represented as `Content-Type` header fields in the MIME message and are essential for the receiving client to correctly interpret and process the message. Here are the main S/MIME content types:

1. **`application/pkcs7-mime` (or `application/x-pkcs7-mime`)**: This content type is used when the entire original message (header and body) has been enveloped (encrypted) or clear-signed (signature with plaintext). In the case of enveloped data, the recipient must decrypt the content using their private key. For clear-signed data, the recipient can verify the signature using the sender's public key.
2. **`application/pkcs7-signature` (or `application/x-pkcs7-signature`)**: This content type is used when the original message is signed but not enveloped. The signature is sent as a separate MIME body part along with the original message. The recipient can verify the signature against the original message using the sender's public key.
3. **`multipart/signed`**: This content type is used when the original message is signed but not enveloped, and the signature is included as a separate part of the message. This allows clients that don't understand S/MIME to display the original message.
4. **`multipart/encrypted`**: Although not commonly used with S/MIME, this content type can denote an encrypted message, similar to `application/pkcs7-mime` with enveloped data.

The confusion between S/MIME types and content types arises from the fact that the same cryptographic operation (like signing or encryption) can be represented by different content types, and the content type doesn't necessarily indicate the specific cryptographic operations used.

Additionally, signed and enveloped data can be nested in any order, but a common practice is to sign first and then encrypt, as this ensures the signature itself is also encrypted. This process involves creating a signed data structure (using `application/pkcs7-signature` or `multipart/signed`), and then encrypting that structure (resulting in `application/pkcs7-mime`).

The recipient of the message would first decrypt (if the message is enveloped) and then verify the signature (if the message is signed), performing the reverse of the sender's operations. The specific content types in the message indicate how these operations should be performed.

**S/MIME Processing**
![[S-MIME-Processing.png]]

**S/MIME Enveloped Data**
![[S-MIME-Enveloped-Data.png]]

**S/MIME Signed Data**
![[S-MIME-Signed-Data.png]]

**S/MIME Multipart/Signed Data**
![[S-MIME-Multipart-Signed-Data.png]]

**Efail Direct exfiltration attack**
*GPT*
Efail is a set of vulnerabilities discovered in 2018 that affect S/MIME and OpenPGP encrypted emails. One of the main attack methods in Efail is direct exfiltration.

In the direct exfiltration method, an attacker who has access to encrypted emails (for instance, by intercepting network traffic or breaching an email server) alters the emails by injecting malicious HTML tags such as an `img` tag. The `src` attribute of the tag is carefully crafted to begin with the ciphertext and end at an arbitrary point within the ciphertext.

The modified email is then sent to the victim. When the victim's email client decrypts the email, the decrypted plaintext replaces the ciphertext in the malicious `img` tag's `src` attribute. This forms a URL containing the plaintext of the email. If the email client automatically loads images, it will attempt to fetch the image at that URL, sending the plaintext of the email to a server controlled by the attacker.

Thus, Efail's direct exfiltration attack can lead to the unintended exposure of sensitive information contained in encrypted emails. Importantly, the attack relies on a combination of cryptographic vulnerabilities and the behavior of specific email clients, particularly those that automatically load images or other external content.

![[Efail.png]]

---

links: [[209 AC2 TOC - Secure messaging and channels|AC2 TOC - Secure messaging and channels]] - [[themes/000 Index|Index]]