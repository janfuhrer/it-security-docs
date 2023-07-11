tags: #AC2 #asymmetric 

# Trust Agility

links: [[208 AC2 TOC - Centralized public-key infrastructures|AC2 TOC - Centralized public-key infrastructures]] - [[Public Key Infrastructure]] - [[themes/000 Index|Index]]

---

> What is fundamentally wrong with the current CA model?

- Trust of a CA is forever (also trust in Registrars, TLD's, ...)
- Trust is centralized
- Information is distributed
- not "own" trust
- (DNSSEC = CA System)

> What is the idea of "trust agility", and is it reasonable?

- User decides which CA should verify a website (not being forced to trust a pre-set list of CAs)
- A trust decision can easily revisited at any time

>  Understand the notion of "perspectives". Evaluate strengths and weaknesses of the perspective model.

- The Perspectives model is a system designed to enhance the security of certificate validation by using a network of "Notary" servers. When a client connects to a server, it can ask the Notaries what certificate they see for that server. If the client sees the same certificate as the Notaries, it can have higher confidence that the certificate is valid, even if the certificate is not signed by a trusted CA.
- **Advantages**:
	- can detect attacks to users or from specific network locations
	- allows for trust agility (as trust decisions can be based on the Notary rather than a fixed list of CAs)
- **Disadvantages**:
	- maintaining a network of Notaries
	- works only if an attacker cannot control or influence what certificate the Notaries sees
	- only works for the initial connection
	- privacy-concerns (use Notary proxy with TLS)
	- latency
	- trust of Notaries (money/ no business model)

---
links: [[208 AC2 TOC - Centralized public-key infrastructures|AC2 TOC - Centralized public-key infrastructures]] - [[Public Key Infrastructure]] - [[themes/000 Index|Index]]