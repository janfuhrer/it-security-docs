tags: #AC1 

# Naming Systems

links:  [[111 AC1 TOC - Naming Systems|AC1 TOC - Naming Systems]] - [[themes/000 Index|Index]]

---

## What are security goals for name systems?

*GPT*
- **Query Origin Anonymity:** This aims to protect the identity of the user initiating the query. Essentially, it should not be possible to trace who is asking for the resolution of a specific name.

- **Data Origin Authentication and Integrity Protection:** This goal ensures that the data received has indeed originated from a trusted source and that it has not been tampered with during transit.

- **Zone Confidentiality:** This ensures that specific details about the domain (zone) remain confidential and are not leaked during the name resolution process. It's about protecting sensitive information in the zone from unauthorized access.

- **Query and Response Privacy:** This goal is about protecting the privacy of both the query and the response. It should not be possible for an eavesdropper to determine what name was queried and what was the corresponding response.

- **Censorship Resistance:** This aims to ensure that the name system can resist attempts to block or filter certain names. The system should still resolve names even if a party tries to prevent the resolution of certain names.

- **Traffic Amplification Resistance:** This is about preventing attacks that involve causing a small query to generate a large amount of traffic, overwhelming the system or a target. The name system should be designed to resist such amplification attacks.

- **Availability:** The name system should always be available and operational, able to resolve queries. This involves preventing denial-of-service attacks that could disrupt the service and ensuring that failures in one part of the system don't take down the whole system.


## What are ways to add cryptography to DNS?

*GPT*
- **DNSSEC (Domain Name System Security Extensions):** This approach adds digital signatures to DNS data to ensure the data's authenticity and integrity. It protects against DNS spoofing attacks but doesn't provide confidentiality.

- **DNSCurve:** DNSCurve uses elliptic curve cryptography to provide confidentiality, authentication, and integrity. However, it doesn't provide the same level of backward compatibility as DNSSEC.

- **DNS-over-TLS (Transport Layer Security):** DNS-over-TLS encrypts DNS queries using TLS, providing confidentiality in addition to the integrity and authenticity offered by DNSSEC. It requires both the client and the server to support it.

- **DNS-over-HTTPS:** This method sends DNS queries over the HTTPS protocol, allowing them to blend in with regular web traffic and thereby enhancing privacy. It also encrypts the queries, providing confidentiality, integrity, and authenticity.

- **RAINS:** New protocol designed by ETH Zürich

## Case study 1

*“The IETF is standardizing DNS over HTTPS (DOH), where all DNS queries are sent over the HTTPS protocol to some well-known HTTPS server (such as Google’s 8.8.8.8 or Cloudflare’s 1.1.1.1). This will prevent local governments from manipulating DNS traffic and improve the user’s privacy with respect to their ISPs and governments. However, Google or Cloudflare will see the DNS queries and replies of the users, and they must be expected to have weak privacy policies and are subject to US law which includes secret rules and court orders. The NSA has a history of snooping on (MORECOWBELL) and manipulating (QUANTUMDNS) DNS traffic.”*

### Virtues

**Confidentiality and privacy**
Queries are encrypted, ISPs and governements can't see or change the DNS traffic

**Censorship Resistance**
Censorship efforts can be bypassed which can be helpful in regions with stringent internet restrictions

### Vices

**Centralisation and Trust**
Users have to trust large providers because they can see the queries which might cause privacy risks

**Legal issues**
Governments can force google to give up certain information in certain legal cases

**Transparency**
There is no transparency and users can't be sure that google isn't sharing their information with governments

## Case study 2

*“The ETH Zurich is developing a new name system called RAINS with a new trust anchor operated by the regional Internet service provides, aka the local Isolation Service Domain (ISD). RAINS does not change the privacy of DNS (provides can continue to monitor traffic, all zone data becomes public) and allows the local authorities to block Web sites to improve public safety and enforce local laws (see also: ”Glu ̈cksspielgesetz in Switzerland”). At the same time, foreign censorship efforts are less likely to be effective (unless they foreign government forces the DNS authority to alter the authoritative records).”*

###  General infos

* Feels a bit like splitting up the internet and each country is in power of their own part of the internet.
* Every entry in RAINS is signed, ensuring the integrity and authenticity of the data.
* RAINS uses an object-oriented approach, where each entry has an object type (like IP address, email, etc.) and a set of attributes. This allows RAINS to be more flexible and scalable than DNS, able to accommodate a wider variety of services.
* Queries in RAINS can be done over secure channels, preventing eavesdropping.
* In DNS, each record has a Time To Live (TTL), which specifies how long the record should be cached. RAINS replaces this with explicit validity periods, which specify a start and end time for the validity of each record. This can make caching more efficient and reduce unnecessary network traffic.
* To ensure resilience and availability, RAINS supports sharding and replication of its name servers. This means that the data stored in RAINS can be distributed across multiple servers, reducing the impact of any single server going down.

### Virtues

**Availability**

RAINS aims to decentralize trust by allowing for multiple trust anchors, compared to DNS's single root of trust. This could promote resilience and reduce single points of failure.

**Censorship Resistance against adversaries abroad**

With the decentralized trust model, RAINS could potentially limit the global reach of censorship attempts by a single entity.

**end-to-end integrity**

Entries are signed to ensure data integrity and authenticity. This enhances the reliability of the system and builds user trust. Queries in RAINS can also be done over secure channels, preventing eavesdropping.

### Vices

**Compartmentalisation**

By allowing ISPs or individual countries to serve as trust anchors, RAINS may inadvertently enable fragmentation of the internet, with each country or region potentially controlling and shaping access to information.

**Censorship Resistance at home**

If each ISP or country is given control over its portion of the name system, this could enable regional censorship, where a country or an ISP could decide what to block.

**Privacy**

ISPs can already monitor your IP internet traffic. With RAINS they can also monitor your DNS requests. 


## Case study 3

*“Namecoin establishes a new name system on the blockchain (where thus zone data is also public), but where public authorities cannot block information. Queries are performed against a local copy of the blockchain and thus also private. There is no WHOIS, so the owner of a name can also be anonymous. However, Namecoin uses much more bandwidth and energy as blockchain payments are used for registration and name resolution. Names are registered on a first-come, first-served basis. Trademarks, copyrights anti-fraud or anti- terrorism judgements cannot be used to force owners of names to relinquish names.”*

### Virtues
**Censorship resistance**
It is a decentralized naming system which means no authority can clock access to information

**Privacy and anonymity**
There is no WHOIS service so the owner of a name remains anonymous. It's private because queries are performed against a local copy of the ledger.

**end-to-end integrity**
Since entries are on the blockchain they are (almost) immutable

### Vices
**Energy consumption**
Blockchains use a lot of energy

**Absence of Legal Enforcement**
first-come, first-served could lead to problems with trademarks and copyrights since a given name can't be forcefully changed.

**Potential for abuse**
Websites promoting illegal activities can be freely registered on namecoin

**Scalability and adoption challenges**
It's a new technology and potentially complex which makes it difficult to adopt


## How does the ethereum naming system work?

*GPT*
- **Name Registration:** Users can register a domain name (like 'yourname.eth') on the ENS by interacting with the ENS smart contract on the Ethereum blockchain. This usually involves sending a transaction with a bid for the name. The highest bidder gets to own the name. Note that the process for initial registration and auction can vary.

- **Resolution:** Once a name is registered, it can be used to resolve to various types of resources, not just Ethereum addresses. This is done by setting up a resolver contract for the name, which can return resources like Ethereum addresses, IPFS hashes for decentralized websites, and more. A user or a dApp can query the ENS contract to resolve a name into its associated resources.

- **Ownership and Transfers:** The owner of an ENS name (i.e., the account that won the initial auction) has full control over the name and can transfer it to another Ethereum address at any time.

- **Renewals:** Unlike traditional DNS, ENS names are not owned permanently. They need to be renewed regularly (currently every year), which involves sending a transaction and paying a renewal fee.

---
links:  [[111 AC1 TOC - Naming Systems|AC1 TOC - Naming Systems]] - [[themes/000 Index|Index]]