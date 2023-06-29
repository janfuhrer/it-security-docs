tags: #AC1 

# Naming Systems

links: [[108 AC1 TOC - Blockchain|AC1 TOC - Blockchain]] - [[themes/000 Index|Index]]

---

## Security Goals for Name Systems

- **Query Origin Anonymity:** protect identity of user initiating a query $\rightarrow$ some anonymity by *Recursive Resolver* (IP is not sent with request)
- **Data Origin Authentication and Integrity Protection**: protect data during transit $\rightarrow$ DNSSEC
- **Zone Confidentiality**: protecting sensitive information in the zone from unauthorized access $\rightarrow$ DNS: yes, DNSSEC: no
- **Query and Response Privacy:** protect privacy of query and response (e.g. eavesdropper) $\rightarrow$ DNS: no
- **Traffic amplification resistance**: preventing attacks that involve causing a small query to generate a large amount of traffic
- **Availability**: preventing denial-of-service attacks

## Cryptography in DNS

- **DNSSEC**: *Domain Name System Security Extensions*, adds digital signatures to DNS, protects against spoofing attacks, provides integrity and authenticity but no confidentiality (no encrypted queries)
- **DNSCurve**: uses elliptic curves to provide confidentiality, authentication and integrity, not widely used
- **DNS-over-TLS**: providing confidentiality, Client *and* Server has to support it
- **DNS-over-HTTPS**: DNS queries over HTTP-Protocol
- **RAINS**: New protocol designed by ETH Zürich

## Ethereum Name System

- **Name Registration:** Users can register a domain name (like 'yourname.eth') on the ENS by interacting with the ENS smart contract on the Ethereum blockchain. This usually involves sending a transaction with a bid for the name. The highest bidder gets to own the name. Note that the process for initial registration and auction can vary.
- **Resolution:** Once a name is registered, it can be used to resolve to various types of resources, not just Ethereum addresses. This is done by setting up a resolver contract for the name, which can return resources like Ethereum addresses, IPFS hashes for decentralized websites, and more. A user or a App can query the ENS contract to resolve a name into its associated resources.
- **Ownership and Transfers:** The owner of an ENS name (i.e. the account that won the initial auction) has full control over the name and can transfer it to another Ethereum address at any time.
- **Renewals:** Unlike traditional DNS, ENS names are not owned permanently. They need to be renewed regularly (currently every year), which involves sending a transaction and paying a renewal fee.

---

## Case Studies

### Case study DOH

*“The IETF is standardizing DNS over HTTPS (DOH), where all DNS queries are sent over the HTTPS protocol to some well-known HTTPS server (such as Google’s 8.8.8.8 or Cloudflare’s 1.1.1.1). This will prevent local governments from manipulating DNS traffic and improve the user’s privacy with respect to their ISPs and governments. However, Google or Cloudflare will see the DNS queries and replies of the users, and they must be expected to have weak privacy policies and are subject to US law which includes secret rules and court orders. The NSA has a history of snooping on (MORECOWBELL) and manipulating (QUANTUMDNS) DNS traffic.”*

#### Virtues

- **Confidentiality and privacy**: Queries are encrypted, ISPs and governements can't see or change the DNS traffic
- **Censorship Resistance**: Censorship efforts can be bypassed which can be helpful in regions with stringent internet restrictions

#### Vices

- **Centralisation and Trust**: Users have to trust large providers because they can see the queries which might cause privacy risks
- **Legal issues**: Governments can force google to give up certain information in certain legal cases
- **Transparency**: There is no transparency and users can't be sure that google isn't sharing their information with governments

### Case study RAINS

*“The ETH Zurich is developing a new name system called RAINS with a new trust anchor operated by the regional Internet service provides, aka the local Isolation Service Domain (ISD). RAINS does not change the privacy of DNS (provides can continue to monitor traffic, all zone data becomes public) and allows the local authorities to block Web sites to improve public safety and enforce local laws (see also: ”Glücksspielgesetz in Switzerland”). At the same time, foreign censorship efforts are less likely to be effective (unless they foreign government forces the DNS authority to alter the authoritative records).”*

**General infos**

* Feels a bit like splitting up the internet and each country is in power of their own part of the internet.
* Every entry in RAINS is signed, ensuring the integrity and authenticity of the data.
* RAINS uses an object-oriented approach, where each entry has an object type (like IP address, email, etc.) and a set of attributes. This allows RAINS to be more flexible and scalable than DNS, able to accommodate a wider variety of services.
* Queries in RAINS can be done over secure channels, preventing eavesdropping.
* In DNS, each record has a Time To Live (TTL), which specifies how long the record should be cached. RAINS replaces this with explicit validity periods, which specify a start and end time for the validity of each record. This can make caching more efficient and reduce unnecessary network traffic.
* To ensure resilience and availability, RAINS supports sharding and replication of its name servers. This means that the data stored in RAINS can be distributed across multiple servers, reducing the impact of any single server going down.

#### Virtues

- **Availability**: RAINS aims to decentralize trust by allowing for multiple trust anchors, compared to DNS's single root of trust. This could promote resilience and reduce single points of failure.
- **Censorship Resistance against adversaries abroad**: With the decentralized trust model, RAINS could potentially limit the global reach of censorship attempts by a single entity.
- **end-to-end integrity**: Entries are signed to ensure data integrity and authenticity. This enhances the reliability of the system and builds user trust. Queries in RAINS can also be done over secure channels, preventing eavesdropping.

#### Vices

- **Compartmentalisation**: By allowing ISPs or individual countries to serve as trust anchors, RAINS may inadvertently enable fragmentation of the internet, with each country or region potentially controlling and shaping access to information.
- **Censorship Resistance at home**: If each ISP or country is given control over its portion of the name system, this could enable regional censorship, where a country or an ISP could decide what to block.
- **Privacy**: ISPs can already monitor your IP internet traffic. With RAINS they can also monitor your DNS requests. 


### Case study Namecoin

*“Namecoin establishes a new name system on the blockchain (where thus zone data is also public), but where public authorities cannot block information. Queries are performed against a local copy of the blockchain and thus also private. There is no WHOIS, so the owner of a name can also be anonymous. However, Namecoin uses much more bandwidth and energy as blockchain payments are used for registration and name resolution. Names are registered on a first-come, first-served basis. Trademarks, copyrights anti-fraud or anti- terrorism judgements cannot be used to force owners of names to relinquish names.”*

#### Virtues

- **Censorship resistance**: It is a decentralized naming system which means no authority can clock access to information
- **Privacy and anonymity**: There is no WHOIS service so the owner of a name remains anonymous. It's private because queries are performed against a local copy of the ledger.
- **end-to-end integrity**: Since entries are on the blockchain they are (almost) immutable

#### Vices

- **Energy consumption**: Blockchains use a lot of energy
- **Absence of Legal Enforcement**: First-come, first-served could lead to problems with trademarks and copyrights since a given name can't be forcefully changed.
- **Potential for abuse**: Websites promoting illegal activities can be freely registered on namecoin
- **Scalability and adoption challenges**: It's a new technology and potentially complex which makes it difficult to adopt

---
links: [[108 AC1 TOC - Blockchain|AC1 TOC - Blockchain]] - [[themes/000 Index|Index]]