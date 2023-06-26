## What is a blockchain?

A blockchain is a distributed ledger which stores data in a series of blocks. Blocks contain lists of transactions and the hash of the previous block. Adding the hash of the previous block links every block to the next which leads to the formation of a chain. Altering data in a older block becomes more difficult over time because the hashes in all the following blocks have to be altered aswell.

## Advertised properties of blockchain

### Immutability

**Claim**
When something is written to the blockchain it can not be altered anymore and stays there forever.

**Reality**
Given sufficient computing power an attacker can gain more mining power than the rest of the network. This allows them to change data inside a block and then recalculate the following blocks.

It's possible to simply start an additional blockchain or fork the initial blockchain and change / remove transactions.

It's possible that the network partitions for some time and then merges again. Depending on the protocol this either breaks consensus and some central power has to step in and fix the problem or the longer chain is chosen as the valid one which leads to transations in the shorter chain getting lost.

### Transparency

**Claim**
All transactions are publicly available. Every participant in the network can verify that the protocol is followed and there are no malicious transactions (for example double spending).

**Reality**
While all transactions are public, there is no personal data required to make a transaction on a blockchain. Every wallet (available money to spend) is represented as a public key (pseudonym) and for an outsider there is nothing to learn from single transactions.

### Anonymity

**Claim**
Anonymity can be achieved with some wallets (changing public key after every transaction) and pseudonymity is always "given" since no personal information has to be given to anyone to use a blockchain.

**Reality**
The most common way to buy cryptocurrency (interacting with a blockchain) is over an exchange which requires kyc (know your customer). The exchange sends the money to your wallet (public key) which essentially links your personal information to your public key. The same is the case when using the money to buy something on the internet. Normally personal information has to be given to buy something on the internet.

There are ways to mitigate those issues but it is up to the protocol to decide if those are required or not. For example monero has privacy and anonymity baked into the protocol. This can lead to other issues though. In the case of monero no one can verify that there is no inflation bug in the protocol since no one knows who has how much money.

### Decentralization

**Claim**
Anyone can run a bitcoin node, anyone can mine bitcoin and everyone can see the blockchain and verify that everything is correct. It is believed / hoped that no single actor can gain power over the network and alter / stop / remove transactions. Decentralization is important because it eliminates the need to trust a central authority. The blockchain is supposed to run trustlessly

**Reality**
In reality blockchains often have a tendency to become more centralized. Places with cheaper energy and less regulation can mine cryptocurrencies cheaply which can lead to mining centralization. Miners are built by companies which gives those companies power. Early adopters of currencies might have a big amount of the currency which allows them to affect the price and in the case of proof of stake have a bigger voting power for new blocks and higher staking rewards.

### Irreversibility

**Claim**
Once a transaction is on the blockchain it cannot be undone.

**Reality**
See Immutability

### Autonomy

**Claim**
Every user owns his own money and can send it to anyone else without being censored by a central power (bank or government).

**Reality**
While the claims can be true there are problems that come with it. Users need to self custody their money which is similar to having money under the mattress. A user error leads to lost funds and no way to recover them (hackers, losing private key, security bug in wallet / protocol). Those properties lead users to store their funds on central exchanges. Since there is not much regulation currently when it comes to internet money, those exchanges can not always (never) be trusted.


## What is proof of work / mining?

Proof of work (POW) is what a miner does to append a block to the blockchain. User transactions are propagated through the network and end up in the mempool (memory pool) of the nodes. Mempool is just a list of pending transactions. A miner (node) then takes some transactions and puts them in a block and adds the hash of the previous block. The miner has to make sure that the chosen transactions are valid (no double spending and user must have enough available funds). A miner has to have all the balances from all users in the network loaded in memory to be able to verify new transactions in reasonable time. This means that every miner initially has to parse the whole blockchain (around 500GB for bitcoin) and load the current balances of all the users.

Mining means adding a random string to the block and hashing the block until some goal is reached. Normally the goal is to find a hash which has a number of leading 0's (finding a partial collision). The number of the leading 0's is the difficulty. The difficulty can be adjusted based on the computing power of the network (how long it takes on average to find a new block). This happens automatically based on the rules in the protocol.

When a miner finds a block he propagates it through the network. Every miner/node reads the random string from the block, hashes the block and confirms that the resulting hash has enough leading 0's to reach the difficulty goal. If that's the case they remove those transactions from their mempool, add the block to their local copy of the blockchain (ledger) and continue mining.

Mining is usually done with ASICs (application-specific integrated circuit) to get the most out of the available power. Mining on CPU / GPU is possible but normally not economically viable.


## What is bitcoin?

The most popular implementation of blockchain internet money / cryptocurrency is bitcoin. Every user has at least one public / private key pair. Money can be sent to other users public keys and private keys are used to sign transactions.

Bitcoins are created (minted) when a block in mined. A miner can add a transaction in the block which essentially creates some bitcoin (6.25 currently) out of nothing and give it to himself. This is called the block reward. Regular users have to provide transaction fees when doing a transaction. The miner can add those fees to his own address as well.

Normal block time is 10 minutes. This means that the protocol tries to adjust the difficulty so that around every 10 minutes a miner finds a block. If too many blocks are found the difficulty is increased which means miners have to find hashes with more leading 0's.

Bitcoin has a maximum available supply of 21 million. Every ~4 years the block reward is cut in half. This means that to keep miners incentivised to mine the price of bitcoin needs to double every 4 years. If that is not the case then some miners will not be profitable anymore and might have to stop mining. This leads to less security for the network. In the year 2140 all 21 million bitcoin will be mined. It is not yet clear what is going to happen at this point. The current idea is that the block rewards will be replaced by transaction fees.
![[bitcoin_payment_flow.png]]

## What are problems of bitcoin?

**Conflicting blocks**
It's possible that two miners mine a block at the same time. This means that one partition of the network has has Block A as latest block and the other partition has Block B as latest block. This problem is easily solved by the fact that bitcoins protocol always choses the longest chain. If a miner which has Block A as latest block mines Block C then all nodes which have Block B as latest block will notice that they are not part of the longest chain anymore and will have to either resync with the rest of the network or fork.

**Forking**
Forking means that one or more nodes decide to mine their own blockchain independently from the rest of the network. This allows them to change the history of the blockchain, remove parts of the blockchain or change the protocol entirely.
In the case of a protocol change, the history of the blockchain stays the same. This means that users who had money on the old blockchain will have the same amount on the new blockchain and will be able to spend the money on both blockchains.

The most prominent fork is the bitcoin fork of 2016 which lead to the creation of bitcoin cash. For bitcoin nothing really changed through this fork. Some people sold off their bitcoin because they believe bitcoin cash is the real bitcoin but most users sold their newly forked bitcoin cash and kept their bitcoin which lead to bitcoin cash being orders of magnitude less valuable than bitcoin.

**Finality / Latency**
Because of the double spending problems it is recommended to wait around 6 blocks until a transaction is confirmed. Reversing a transaction after only 1 block is easier than reversing it after 6 additional blocks have already been mined. An attacker would need to change the transaction and then shadow mine (mine locally without broadcasting) all the previous blocks and catch up with the longest chain. An attacker needs at least 51% of the mining power to achieve this attack but the older the transaction the more mining power is needed to catch up with the current state of the chain in a reasonable time. For every shadow mined block the actual block chain has a 49% chance to also find a block which means the attacker need to shadow mine even more.

Compared to mastercard the waiting time for finality isn't too bad. On Mastercard settlement only happens after 1-2 business days and even after that a chargeback can still be made weeks or months after the transaction happened.

**Privacy**
Transactions are only private as long as your personal information are not linked to your public key. All transactions are transparent and public available.

**Storage**
The bitcoin blockchain grows linearly over time. It's currently around 500GB and there is no garbage collection. Spent transactions are only used for parsing the blockchain and for nodes to verify themselves that every transaction that ever happened is valid. Removing part of the blockchain would theoretically add trust because new nodes will have to trust that previous transactions were valid. This is an open discussion and the blockchain can be pruned (remove old transactions) in the future if consensus can be reached.

**Power consumption**
Mining takes up a lot of energy. The spent energy can be considered as wasted. If bitcoin has actual value or not is a debatable topic and the amount of energy spent on creating it is linked to this discussion. It is believed that mining uses as much energy as Denmark today. There is no way to actually verify this claim.

**Rate**
The bitcoin network supports around 7 transactions per second which is very little. This leads to high transactions fees. Other solutions like the lightning network or central exchanges help with this problem but they lead to less security (lightning network) or less decentralization / more trust (central exchanges) -> blockchain trilemma

**Accountability**
Because personal information is not linked to bitcoin public keys it used to be used for criminal activity. Because of the pseudonymity it is not the best solution since the police can still find bad actors if they can link the public key to a person in any way (buying bitcoin on exchange or spending it). Solutions like monero are better suited for criminal activity.


## What are altcoins

Altcoins are cryptocurrencies which are not bitcoin.

**Dogecoin**
Memecoin which essentially works like bitcoin, only slight protocol changes

**Zcash**
Uses ZKSNARKs (Zero-Knowledge Succinct Non-Interactive Argument of Knowledge) to hide transactions

**Ethereum**
Allows users to deploy smart contracts (programs) on the blockchain which miners will execute in decentralized way. Allows the creation of additional altcoins on top of ethereum.


## Case study

“A company is developing new software for private payments. This will enable its customers to transact with “complete” privacy (like cash). The solution does not include backdoors, and thus the company cannot block payments to support trade embargos or anti money laundering efforts.”

### Virtues
**Privacy**
Users can transact money privately

**Autonomy**
Users can do whatever they want with their money and no one can stop them

**Inclusivity**
Users who might not had a bank account before get to use money on the internet which might not have been possible previously

### Vices
**Illicit activities**
Users can use this system to do illegal activities like monay laundering or tax evasion

**Lack of consumer protection**
Reversing fraudulent transactions is not possible if everything is private

**Regulatory compliance**
Anti-money laundering efforts can not be supported which might make this system illegal in some parts of the world


## What are security goals for name systems?

*GPT*
- **Query Origin Anonymity:** This aims to protect the identity of the user initiating the query. Essentially, it should not be possible to trace who is asking for the resolution of a specific name.

- **Data Origin Authentication and Integrity Protection:** This goal ensures that the data received has indeed originated from a trusted source and that it has not been tampered with during transit.

- **Zone Confidentiality:** This ensures that specific details about the domain (zone) remain confidential and are not leaked during the name resolution process. It's about protecting sensitive information in the zone from unauthorized access.

- **Query and Response Privacy:** This goal is about protecting the privacy of both the query and the response. It should not be possible for an eavesdropper to determine what name was queried and what was the corresponding response.

- **Censorship Resistance:** This aims to ensure that the name system can resist attempts to block or filter certain names. The system should still resolve names even if a party tries to prevent the resolution of certain names.

- **Traffic Amplification Resistance:** This is about preventing attacks that involve causing a small query to generate a large amount of traffic, overwhelming the system or a target. The name system should be designed to resist such amplification attacks.

- **Availability:** The name system should always be available and operational, able to resolve queries. This involves preventing denial-of-service attacks that could disrupt the service and ensuring that failures in one part of the system don't take down the whole system.


## What are way to add cryptography to DNS?

*GPT*
- **DNSSEC (Domain Name System Security Extensions):** This approach adds digital signatures to DNS data to ensure the data's authenticity and integrity. It protects against DNS spoofing attacks but doesn't provide confidentiality.

- **DNSCurve:** DNSCurve uses elliptic curve cryptography to provide confidentiality, authentication, and integrity. However, it doesn't provide the same level of backward compatibility as DNSSEC.

- **DNS-over-TLS (Transport Layer Security):** DNS-over-TLS encrypts DNS queries using TLS, providing confidentiality in addition to the integrity and authenticity offered by DNSSEC. It requires both the client and the server to support it.

- **DNS-over-HTTPS:** This method sends DNS queries over the HTTPS protocol, allowing them to blend in with regular web traffic and thereby enhancing privacy. It also encrypts the queries, providing confidentiality, integrity, and authenticity.

- **RAINS:** https://britram.github.io/rains-prototype/draft-trammell-rains-protocol.html#rfc.section.4


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

...

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


## What is key revocation

The process of invalidation a cryptographic key pair. It's used when a key is compromised or no longer required. 

**Certificate Revocation Lists (X.509)**
CRL is a list of certs which have been revoked by the issuing CA before their scheduled expiration date.

**Online Certificate Status Protocol (OCSP)**
Protocol used to obtain the revocation status of a cert. Instead of having to parsing a list of revoked certs itself, a client sends a query to an OCSP responder and receives information about a single cert.

**OCSP Stapling (TLS)**
The server itself periodically retrieves OCSP response for its own cert and "staples" it to the TLS handshake which means the client doesn't have to contact the OCSP himself.

**Publish Revocation in blockchain**
Revocations could be published on the blockchain. Similar to CRL but decentralised, don't have to trust CA.

**Controlled flooding**
Revocations (signed with private key) can be flooded through a network. It's controlled in that each message is only re broadcasted a certain number of times to prevent endless loops. Efficient set reconciliation is used to compare the sets of revoked certs when nodes first connect to make sure they both have the same state. Proof of work is used to limit DoS-potential. POW can be calculated ahead of time and stored offline to have them read in case they are needed.


## Explain efficient set union and how it can be achieved

The problem to solve is that two nodes each have a sets with small differences and they want to sync up their sets so they end up with the same combined sets.

The naive approach is that both nodes send their sets to the other nodes and they each compare the other nodes set and add whatever they are missing. This gives a communication cost of BigOh(|A| + |B|) which is not great. Instead of sending the actual set, hashes of the elements can be sent but that doesn't improve complexity. The ideal solution would complexity of BigOh(diff(A/B)).

**Bloom filters**
Take an array of 0's and the hash of the first element in the set. Flip the corresponding bits in the array. Repeat for the following elements in the set. If a bit is already flipped to 1 leave it on 1.

Send the array to the other node. The node can check its set elements by hashing them and checking if all the bits are set to 1. If they are then it is likely that all the elements are also present in the set of the sending node. If a bit of an element is not set to 1 then this element is definitely not part of the other nodes set. The probability can be adjusted through the size of the array. The larger the array the lower the chance for false positives.

![[bloom_filter_1.png]]
![[bloom_filter_2.png]]

**Counting bloom filter**
Bloom filters where buckets (array fields) hold positive integers instead of only 0 and 1. This means that elements can also be removed. This leads to the possibility of false negatives. This can happen when an element, which was not previously added, is removed from the CBF. 

The receiver of a CBF can subtract all the elements from its set and when the CBF ends up being negative, the CBF represents the elements that are missing in the other nodes set.

**Invertible Bloom Filters**
Extension of CBF. They allow negative counts are they store XOR-sums of the elements hashes in the buckets. This allows extraction of elements from the IBF and the construction of a symmetric difference.

**Extraction**
