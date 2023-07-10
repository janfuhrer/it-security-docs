tags: #AC2

# SMTP

links: [[209 AC2 TOC - Secure messaging and channels|AC2 TOC - Secure messaging and channels]] - [[themes/000 Index|Index]]

---

## SMTP

*GPT*
Simple Mail Transfer Protocol (SMTP) is a communication protocol used to send email over the internet. SMTP operates in a client-server model over a reliable transport, typically TCP/IP, ensuring that data is delivered without errors and in the correct sequence.

There are two main components in SMTP communication: the content and the envelope.

1. **Content**: This is the object to be delivered to the recipient, typically the email message itself. It includes the body of the email and any attachments, as well as the subject line, and the "From", "To", and "Cc" fields. The content is what the recipient sees when they open the email.

2. **Envelope**: This is the information needed to transmit and deliver the email. It's like the physical envelope of a traditional letter, containing the delivery instructions for the mail servers. The envelope includes the sender's and recipient's email addresses, but these are used by the mail servers for routing and delivery purposes and are separate from the "From" and "To" fields in the content. The recipient does not see the envelope information when they open the email.  

![[SMTP.png]]

In an SMTP session, the client (the sender's email server) establishes a connection with the server (the recipient's email server) over a reliable transport. The client then sends the envelope information to the server, followed by the content of the email. The server uses the envelope information to route and deliver the email to the recipient's mailbox.

SMTP is a simple, text-based protocol, but it's also quite powerful and flexible, allowing for features like forwarding, carbon copies (Cc), and blind carbon copies (Bcc). However, SMTP itself does not include any built-in security features, so it's often used in conjunction with other protocols like TLS or SSL to ensure the confidentiality and integrity of email messages.

**Example Header**
![[SMTP-Header.png]]

Delivery path of messages can be traced back due to the Received header information

![[Received-Header-Info.png]]

---
links: [[209 AC2 TOC - Secure messaging and channels|AC2 TOC - Secure messaging and channels]] - [[themes/000 Index|Index]]