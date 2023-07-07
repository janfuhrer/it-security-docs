tags: #AC2 #asymmetric 

# Trust Issues in X.509

links: [[208 AC2 TOC - Centralized public-key infrastructures|AC2 TOC - Centralized public-key infrastructures]] - [[Public Key Infrastructure]] - [[themes/000 Index|Index]]

---

## Certificate validation issue examples

- BERserk was a catastrophic failure in the certificate validation of the NSS library (used by Firefox / Chrome)
- Most TLS libraries had a chain validation issue at some point


## X.509 CA challenges

**Questions to consider**
Everyone has to trust a CA
- Which one?
- What is it trusted to do?

Certificate bindings must be correct
- Which John Smith is this?
- Who authorizes attributes in a certificate?
- How long are these values valid for?
- What process is used to verify the key holder?

**Are CAs trustworthy?**
- Any public CA can issue certificates for any domain name without obtaining permissions
- Who are these organizations, which we allow to issue certificates with little supervision?
- Most public CAs follow political and economic interests
- Root CAs can sign certificates of intermediate CAs with no constratints
- 19 root CAs signed around 15430 intermediate CAs
- Only 94 intermediate CAs were owned by the signing CA organisations

[List of CA issues](http://wiki.cacert.org/Risk/History)

**Legal aspects**
What is a CA liable for?
- [[Public Key Infrastructure#^baee60 |Certificate policies (CP)]] define rights, duties and obligations of each party in a PKI
- These documents usually have a legal effect
- The CP should be publicly exposed by CAs on their website and inlude:
	- Registration procedures
	- Revocation procedures
	- Liability issues


## Domain Validation via E-Mail

- CA sends mail to defined aliases (admin, administrator, webmaster, hostmaster, postmaster, see [[Public Key Infrastructure#Certification Authority (CA)|Baseline Requirements]])
- If you offer E-Mail you **must** make sure that nobody can register such an address
- One could argue if this is a sane system but it is documented in Baseline Requirements
- live.fi / xs4all.nl issues caused by this validation method


## Certificate Revocation

- Sometimes it is necessary to immediately block usage of a certificate before its expiration date
- A revocation request allows an EE / issuing CA to revoke a still valid certificate
- The CA must publish the revocation subsquently on a specific infrastructure
- Two possible options
	- **Black-lists** via Certificate Revocation List ([[Trust Issues in X.509#Certificate revocation lists (CRL)|CRL]])
	- **White-lists** via Online Certificate status Protocol ([[Trust Issues in X.509#Online Certificate Status Protocol (OCSP)|OCSP]])

**In practice**
- Browsers use insecure soft-fail mode
	- *GPT*: This means that if a browser couldn't retrieve the CRL or get an OCSP response, it would consider the certificate as valid and continue the connection. This was primarily designed to prioritize usability over security. The idea was to prevent users from being unable to access websites due to intermittent network issues or problems with the CA's servers.
- Chrome and Firefox distribute their own blocklists, but they don't scale
- [[Trust Issues in X.509#OCSP Stapling in TLS|OCSP stapling]] could help, but needs a mechanism to indicate its use ([muststaple draft](https://blog.apnic.net/2019/01/15/is-the-web-ready-for-ocsp-must-staple/))

![[OCSP-Stapling.png]]


## Certificate revocation lists (CRL)

CA must maintain and publish a list of all revoked (but not expired) certificates.

Revocation reasons
- Users private key was compromised
- Content of certificate has changed

![[Certificate-Revocation-Lists.png]]


## Online Certificate Status Protocol (OCSP)

**Clients**
Check certificate status online by a OCSP Responder. Client can ask for status of multiple certificates per query

**Responder**
Replies witha signed message using a certificate with extension: extendedKeyUsage = OCSPSigning. Both messages are sent over port 80

**Information about certificate in response**
- good
- revoked
- unknown (e.g. certificate outdated)

The signed responses can be stored / cached by the client

**Problems**
- Performance and resource issues
	- OCSP may provide significant cost to a CA
		- High traffic website may generate huge volume of OCSP requests
		- OCSP slows down browsing, since it requires the lcient ot contact a third party (the CA) to confirm the validity of each certificate that it encounters
- Privacy
	- OCSP checking potentiallyleaks user privacy information to third party online OCSP service
- User (in)decision
	- If OCSP response fails, user often is challenged by incomprehensible options


## OCSP Stapling in TLS

OCSP stapling in TLS mitigates these problems
- The certificate holder queries the OCSP server itself at regular intervals to obtain a signed time-stamped OCSP response
- When browser of the client attemp to connect to the site, the response is included ("stapled") within the TLS handshake (ServerHello extension)
- The TLS client must explicitly request OCSP information as part of the ClientHello message


## Man in the middle proxies

**[Superfish](https://en.wikipedia.org/wiki/Superfish)**
Created a TLS man in the middle proxy, private key was static and part of the software (Komodia)

**[Privdog](https://www.heise.de/news/PrivDog-torpediert-die-Web-Sicherheit-im-Namen-der-Privatsphaere-2557756.html)**
Just disabled TLS verification completely (Privdog is founded by the CEO of Comodo)

Several Antiviruses do the same. Not fully broken, but all decrease the security of TLS. This is only an indirect problem of CAs and TLS. It should not be possible to undermine / bypass the security.

---

links: [[208 AC2 TOC - Centralized public-key infrastructures|AC2 TOC - Centralized public-key infrastructures]] - [[Public Key Infrastructure]] - [[themes/000 Index|Index]]