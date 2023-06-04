## What is anonymity?
Definition:
- not named or identified: “an anonymous author”, “they wish to remain anonymous”
- of unknown authorship or origin: “an anonymous tip”
- lacking individuality, distinction, or recognizability: “the anonymous faces in the crowd”, “the gray anonymous streets”

Pfitzmann
- Anonymity is the state of being not identifiable within a set of subjects, the anonymity set
EFF
- Instead of using their true names to communicate, (...) people choose to speak using pseudonyms (assumed names) or anonymously (no name at all).
Grothoff
- A user’s action is anonymous if the adversary cannot link the action to the user’s identity

## What is pseudonymity
- A pseudonym is an identity for an entity in the system. It is a “false identity” and not the true identity of the holder of the pseudonym.
- Nobody, but (maybe) a trusted party may be able to link a pseudonym to the true identity of the holder of the pseudonym.
- A pseudonym can be tracked. We can observe its behaviour, but we do not learn who it is.

## How can a user be identified?
Identitiy
- real name
- fingerprint
- passport number
- IP address
- MAC address
- login name

Actions:
- Internet acces
- speach
- participation
- in demonstration
- puchase in a store
- walking across the street

## What is the difference between Sender Anonymity and Reciever Anonymity?
- Sender anonymity is when the sender's identity is hidden during message transmission. However, potential traces like IP addresses or metadata may provide a path back to the sender. R
- Receiver anonymity allows the recipient to receive messages without revealing their identity. Since the receiver is not generating traffic, the chance of tracing back to them is less, unless the system logs incoming connections. The level of anonymity depends on the system and protocols used.

## How can anonymity be evaluated?
- number of known attacks
- lowest complexity of successful attacks
- informationleaked through messages and maintenance procedures
- number of users

## What is probability distribution?
It's a statistical function describing all possible values and their likelihoods for a random variable. It gives a mathematical overview of the outcomes of a random event and their corresponding probabilities.

Example: In a dice roll, the outcome can be 1 through 6, each with an equal probability of 1/6. This forms the probability distribution for a fair six-sided die roll.

## What is an anonymity set and what role does it play in anonymity?
It's the group of all potential users that could be responsible for an action, contributing to the anonymity of the actual user.

Examples of large anonymity sets:
- Any human
- Any human with Internet access
- Any human speaking German
- Any human speaking German with Internet access awake at 3am CEST

The larger and more evenly distributed the anonymity set, the greater the anonymity. Each user in this set is a potential suspect, making it harder to identify the actual user.

## What is maximum likelihood?
It's the highest probability that a particular user in the anonymity set is responsible. Legal cases require varying levels of ML for successful prosecution.

## What is entropy in anonymity
GPT:
Entropy's Role in Anonymity: Entropy, as a concept from information theory, quantifies the level of uncertainty or randomness in a set of data. In the context of anonymity, entropy represents the measure of uncertainty about the identity of a user within an anonymity set. A higher entropy denotes a greater degree of anonymity, as there's more uncertainty for an attacker trying to identify a specific user.

The link between entropy and probability stems from the fact that entropy captures the uncertainty linked to the various probabilities of different outcomes. For instance, if all users in an anonymity set are equally likely to be the party of interest to an attacker, the uncertainty (and hence entropy) is at its maximum. However, if some users are more likely to be the target (perhaps due to partial information the attacker has obtained), the uncertainty (and entropy) decreases.

This leads to the concept of "bits of additional information." In information theory, a bit is a unit that reduces uncertainty by half. When we say "entropy is the expected number of bits of additional information that the attacker needs to definitely identify the user," we refer to the theoretical amount of information needed to eliminate all uncertainty, i.e., to pinpoint the user's identity amongst the anonymity set with certainty. This doesn't directly translate to discrete pieces of knowledge, but rather to an overall reduction of uncertainty in a probabilistic sense.

An illustrative example involves a deck of 52 playing cards. If a card is drawn randomly, the uncertainty (or entropy) about which card is chosen is log2(52) ≈ 5.7 bits, as there are 52 equally likely possibilities. If the attacker learns that the drawn card is a heart, the number of possibilities reduces to 13, and the entropy drops to log2(13) ≈ 3.7 bits. This reduction in entropy of about 2 bits represents the additional information the attacker gained. In this case, the remaining entropy (3.7 bits) symbolizes the amount of further information theoretically needed to identify the exact card drawn. The higher the initial entropy, the more additional information is needed, and thus, the stronger the initial degree of anonymity.

![[entropy_calculation_example.png]]
# Wieso wird hie /1000 und /10 grächnet?

## What are possible attacks to reveal someones identity?

**All nodes collaborate against the victim**
This is the most severe scenario. Every single node in the entire network is conspiring against the victim, monitoring and sharing information about their activities. It means that no matter which path the victim's data takes, it's being tracked.

**All directly adjacent nodes collaborate**
This is a less severe situation than the first, but still serious. Only the nodes directly connected to the victim (those the victim communicates with directly) are conspiring. While this might not capture all of the victim's network activity (depending on the network's topology and routing), it captures a significant amount, especially if the network is decentralized and the victim communicates with many nodes.

**All non-collaborating adjacent nodes are made unreachable from the victim**
This scenario describes a situation where the nodes directly connected to the victim that aren't conspiring (and hence would provide secure, anonymous paths for the victim's data) are somehow taken offline or blocked. This could force the victim to use the collaborating nodes, effectively turning this into scenario 2.

**The victim is required to prove his innocence**
This scenario is a bit different, as it's not about the network's nodes colluding against the victim. Instead, it's about a situation where the victim is accused of wrongdoing and must provide proof of innocence, which could potentially involve revealing personal information or specific activities that compromise their anonymity. This is a challenging situation because it forces a conflict between maintaining anonymity and addressing the accusation.

## What is the problem with the economy of anonymity?

**Infrastructure and Maintenance Cost**
Providing anonymity services often requires significant resources for infrastructure setup and maintenance. Anonymity networks require robust and resilient infrastructure to withstand various attacks and service disruptions. The cost associated with building and maintaining such a system can be substantial.

**Legal Liabilities**
Providers of anonymity services may face legal risks if their services are used for unlawful activities. These could include regulatory fines or legal costs associated with defending against allegations of facilitating illegal activities.

**Inefficiencies**
Anonymity often introduces inefficiencies into systems, such as slower data transmission due to routing through multiple nodes for obfuscation. These inefficiencies can make anonymous services less appealing to users and more costly to operate.

**Mitigation of Attacks**
Anonymity services are often targets for attacks, including denial-of-service attacks. The cost of implementing and maintaining security measures to defend against these attacks adds to the overall economic burden.

**Reputational Risk**
If an anonymity service is compromised or associated with illicit activities, it could suffer reputational damage, leading to a loss of users and potential revenue.

**The anonymizing server that has the best reputation (performance, most traffic) is presumably compromised**
High-reputation anonymizing servers with a lot of traffic are likely targets for compromise due to their value for attackers. These servers handle substantial data, making them attractive for malicious actors seeking valuable information or aiming to de-anonymize users. Despite this, good security measures can help protect these servers, but their risk of compromise is higher due to their prominence.

## Explain the Dining Cryptographers Problem
Every two cryptographers establish a shared one-bit secret. Everyone then makes an XOR out of the two shared one-bit secrets and reveals the result.

- If they payed they invert the XOR
- If they didn't pay they just reveal the XOR of the shared one-bit secrets

Finally the revealed results are XORed aswell

- If the result is 1 then someone payed but this person stays anonymous
- If the result is 0 then the NSA payed

## What is mixing and how does it work?
A cryptographic protocol used to provide anonymity for network communications. This approach to maintaining privacy is implemented by a mix network, owhich uses a chain of mix nodes.

**Example**
1. Each message is encrypted with the public keys of the mix nodes in reverse order of the nodes it will pass through. The initial encryption might use the public key of the last node, then the next-to-last, and so on, until finally the message is encrypted with the key of the first node.

2. The message is then sent through the network, passing through each mix node in order.

3. Each mix node, upon receiving a message, uses its private key to decrypt its layer of encryption. This reveals the address of the next node to which the message should be sent.

4. Additionally, each mix node changes the appearance of the message even if it can't read its contents. It does this by decrypting and re-encrypting the message, making it difficult to link the incoming and outgoing messages. The node might also batch multiple messages together, changing the order before forwarding them, which further obscures the origin-destination link.

5. This process is repeated until the message reaches its final destination.

## What are different types of mixing?
**Threshold Mix**
A type of mix that waits until it has received messages from a certain number of users (the threshold) before it sends them out in a random order.

**Timed Mix**
This mix collects messages for a certain period of time before sending them out in a random order.

**Pool Mix**
In a pool mix, incoming messages are added to a pool. A certain number of messages are randomly selected from the pool and sent out, while the remaining messages stay in the pool for the next round.

## What is Mixminion?
Mixminion is an type III anonymous remailer protocol that was designed to improve upon earlier protocols by offering better resistance to attacks, and more reliable delivery of messages. It's a mixmailer which uses mix networks for email communication, effectively anonymizing the sender and recipient of an email. Compared to previous mixers it has some advantages.

**Possibility to Reply**
One major advancement Mixminion brings over previous remailer protocols is the ability for recipients to reply to anonymous emails without knowing the sender's actual identity.

**Directory Servers and Reputation System**
Directory servers in Mixminion keep track of available mix nodes (remailers) and their reputations. This system helps users to select reliable and trustworthy nodes for routing their messages.

**Exit Policies**
Just like with Tor, mix nodes in Mixminion can have exit policies which allow the operator of the node to determine what type of traffic is allowed to exit their node and to where. This can help to manage legal and ethical considerations associated with running a node.

## How do replies work in Mixminion?

Alice --------------------------------------------> Bob
Alice <-- second leg -- Crossover <-- first leg-- Bob

Example in which Alice sends a message to Bob and Bob can answer without knowing Alice:
1. Alice prepares her message to Bob and includes the crossover node and the second leg for Bob's reply within her message. 

2. Alice then selects a series of nodes in the Mixminion network through which to send her message. She adds this to the existing path information and then encrypts the message and path data in layers, where each layer corresponds to a node in the path.

3. Alice sends her message into the Mixminion network. Each node in the path decrypts its layer of the message, revealing where to send the message next.

4. Eventually, the message arrives at Bob's email address. Bob can read Alice's message because it was encrypted for him. He can see the encrypted reply path but cannot decipher it because it is encrypted for the nodes in the path, not for him.

5. Now, Bob prepares his reply and attaches Alice's encrypted reply path to it. He then chooses his own series of nodes (a new first leg) to reach the crossover node, encrypts his message and the entire path in layers, and sends it into the Mixminion network.

6. When Bob's reply reaches the crossover node, the node decrypts its layer of the message to find out where to send the message next. The remaining part of the path is still encrypted and unreadable to the crossover node.

7. The message continues to travel along the second leg of the path that Alice originally provided. Finally, the reply arrives back at Alice's email address.

## How are replay attacks mitigated in Mixminion?
Mix nodes keep hashes of previously processed messages until the server key is rotated

## What are directory servers in a mixnet? (partitioning attack)
Directory servers in Mixminion provide users with information about available remailers and assess the reliability of participating servers. However, relying on only a subset of directory servers could make users vulnerable to partitioning attacks. To mitigate this risk, users are advised to query all directory servers to obtain a complete network view.

## What are Nymservers?
Nyms (short for pseudonyms) allow users to maintain long-term identities without revealing their true identities or their locations. Alice might use a nym when she wants to have continuing anonymous conversations with Bob without revealing her real email address or identity.

A nym server stores nyms and the associated reply blocks (path of nodes). When Alice sends a message to Bob using her nym, the message is first sent to the nym server. The server then attaches the stored reply block associated with Alice's nym and sends the message to Bob. When Bob replies, the message goes through the sequence of nodes in the reply block and finally reaches the nym server. The nym server then sends the message to Alice.

Using a nym server has the advantage that Alice does not have to include a reply block with each message, which can be bandwidth-intensive. Instead, she can update her reply block on the nym server from time to time for added security.

## What are problems of Nymservers?

**Reply Block Depletion via Spamming**
This attack vector involves an attacker spamming a particular pseudonym (nym) with numerous unnecessary messages. This could potentially inundate the sender with unwanted replies, making it difficult for them to find legitimate messages amid the spam. This acts as a form of Denial of Service (DoS) attack.

**Repeated Use of Reply Blocks**
If a single reply block is used multiple times for routing messages, an attacker observing traffic across several nodes could potentially correlate different messages using statistical analysis. This repeated use of reply blocks could increase the risk of compromising the sender's anonymity, which the remailer network is designed to protect.

**Mail Storage at Nym Servers**
If a nym server stores multiple messages and uses a single reply block to send all those messages together to conserve the anonymity provided by reply blocks, this also introduces potential vulnerabilities. The stored messages at the nym server could be exposed if the server is compromised, possibly revealing sensitive information. Furthermore, the use of the same reply block for multiple messages could make it easier for an attacker to correlate the messages and potentially uncover the sender's identity.

## What are problems of Mixminion?
- No benefits / incentives of running a mixer
- A lot of public key cryptography (slow)
- Users have to trust directory servers (those also don't have an incentive to act good)
- Servers have to keep state (resources)
- Service is limited to E-Mail because of high latency
- Exit nodes can be liable for legal action
- No functionality to avoid DoS attacks
- Statistical correlation of entities communicating over time is still possible if the whole network is observed
- Bridge between anonymous network and traditional a traditional protocol is difficult

## What is tor

P2P network of low-latency mixes which are used to provide anonymous communication between parties on the Internet. It works for any TCP-based protocol and traffic enters the network via SOCKS proxy. Commonly used for anonym web browsing.

## How does onion routing work?

- Client choses which mix servers he wants to use for comunication
- Set up symmetric key $K_{S_1}$ with first mix server
- Through first mix server set up symmetric key $K_{S_2}$ with second mix server
- Repeat until user has a key for every mix server
- Encrypt message with all symmetric keys $(K_{S_1}(K_{S_2}(m)))$ and send message to first mix server
- First mix server decrypts the message and sends the message to the next mix server until destination is reached.
![[tor_routing_1.png]]

Just like in mixminion, there are directory servers which keep track of contact information, public keys and statistics. Clients use directory servers to chose servers based on bandwidth and update. Circuits / Routes are of length three. 
![[tor_routing_2.png]]

In the example above
- Tor Node 1 is the **Entry node / Guard**
	- Generally long lived "good" nodes
	- Client (User) has to trust this node since it directly communicates with it
- Tor Node 5 is the **Relay / Middle node**
- Tor Node 8 is the **Exit node**
	- Visible to outside destination
	- Most vulnerable node in circuit / route
	- Supports filtering of outgoing traffic

## What are hidden services and how do they work?

Services inside the tor network which are only available from inside the tor network. They allow tor servers to receive incoming connections anonymously.

Slides page 51

1. **Service Setup**: The hidden service picks some random relay nodes in the Tor network, sets them up as introduction points, and builds circuits to them. The service assembles a hidden service descriptor containing its public key and a summary of each introduction point, and signs this descriptor with its private key. It uploads that descriptor to a distributed hash table (DHT). The descriptor is found by clients by using the .onion address which is a hash of the service's public key.

2. **Client Request**: When a client wants to connect to a hidden service, it loads the .onion address into a Tor-enabled client (like the Tor browser). This address corresponds to the public key of the hidden service. The client uses this key to check the DHT and retrieve the descriptor, which contains the introduction points and the service's public key.

3. **Introduction Points Connection**: After obtaining the introduction points and the service's public key, the client randomly picks a relay in the network to act as a rendezvous point and communicates it to the hidden service via one of the introduction points.

4. **Rendezvous Point**: The client builds a circuit to the rendezvous point and sends a rendezvous message there. The rendezvous point holds this message until the hidden service connects.

5. **Circuit Building**: In the meantime, the hidden service builds a circuit to the rendezvous point and sends a rendezvous message, which makes the rendezvous point connect the two circuits.

6. **Hidden Service Connection**: Now, the client and the hidden service are connected through Tor circuits and can communicate privately. The rendezvous point simply relays (end-to-end encrypted) messages from client to service and vice versa. It does not know the client's IP or the hidden service's IP. It also can't read the content of the messages because they are end-to-end encrypted between the client and the service.

## What types of attacks on tor are possible?
**Listening to traffic on exit servers**
It might be possible to see http traffic if tls isn't used. The source of the request stays hidden though

**Website fingerprinting**
An adversary could potentially monitor the entry node and use the patterns of data entering the Tor network to infer which sites are being visited. Even though the data is encrypted, the size and timing of packets could provide clues, as different sites will tend to generate characteristic traffic patterns.

**Traffic analysis**
A global passive adversary observing multiple nodes could correlate the timing and volume of traffic entering and leaving the Tor network to de-anonymize users. This requires extensive resources and is difficult to execute, but could theoretically compromise anonymity.

**Intersection Attack**
Over time, an adversary could observe when a user is active on the Tor network and correlate this with activity on a certain website or service. This is more a long-term statistical attack and could potentially reveal patterns of usage or, given enough data and time, de-anonymize a user.

**DoS**
An attacker could flood the Tor network, or specific nodes within the network, with an overwhelming amount of traffic, making it unusable for legitimate users. This doesn't compromise anonymity directly, but it disrupts the operation of the network.
--> Beispiel von Grothoff mit loop circuits

## What are the 8 Fallacies of Distributed Computing?

1. The network is reliable
2. Latency is zero
3. Bandwidth is infinite
4. The network is secure
5. Topology does not change
6. There is one administrator
7. Transport cost is zero
8. The network is homogeneous

## Explain Boyd's Theorem I and II

**Boyd’s Theorem I**

This theorem states that if at a particular moment in time a user has either a secure communication channel (confidentiality) to or from her, then this security must have also existed in the previous moment. And by logic, this secure channel must have existed at all times before that moment.

To illustrate, let's consider Alice and Bob communicating via encrypted messages.

- **Now**: Alice sends an encrypted message to Bob. The message is confidential because only Bob, who has the decryption key, can read it.
- **Before**: According to Boyd's Theorem I, since the message is confidential now, it must have been confidential in the previous moment as well. This could be the moment when Alice was typing the message on her computer. Since no one else has access to her computer, the message is confidential at this time as well.
- **Even Before**: Going one step back, even when Alice was thinking about what to write in the message, the information was still confidential because it was only in her mind.

**Boyd’s Theorem II**

This theorem states that secure communication between two parties can be established if there's a sequence of trusted intermediaries connecting them.

Consider Alice wants to send a secure message to Bob, but they have never met, and therefore, haven't exchanged any encryption keys. But Alice knows and trusts Charlie, who in turn knows and trusts Bob.

Alice can securely give Charlie an encryption key (since she trusts him). Charlie can then pass this key to Bob (since Bob trusts him). Now, Bob has the encryption key, and he can use it to decrypt any messages that Alice sends him. Even though Alice and Bob have never met, they can still communicate securely because of the chain of trust involving Charlie.

## Explain Zfone Authentication (ZRTP)

1. **Diffie-Hellman exchange**: Alice and Bob perform a Diffie-Hellman key exchange, which allows them to both arrive at the same secret key, without ever having to send the key itself over the network. This establishes the initial secure communication channel, tying into Boyd's Theorem I, where a secure communication channel must exist in all states.
    
2. **Use of keying material from previous sessions (duckling)**: ZRTP also uses a mechanism called "cached shared secrets", where key material from previous sessions is used in subsequent sessions to authenticate the Diffie-Hellman exchange. This means that even if an attacker is present during one call, they can't affect future calls, which provides continuity of the secure channel across different states.
    
3. **Generation of Short Authentication String (SAS)**: ZRTP generates a Short Authentication String (SAS), a hash of the Diffie-Hellman public keys. This SAS is designed to be read aloud by both parties over the phone.
    
4. **Reading the SAS**: Alice and Bob read the SAS to each other. They both recognize each other's voices, providing a form of human authentication. This process helps to confirm that there's no "man in the middle" intercepting and altering their communications, as such an attacker would not be able to convincingly mimic both voices.

## Examples for famous trilemmas

**CAP Theorem**
This theorem is a concept in distributed data store systems which states that it is impossible for a distributed data store to simultaneously provide more than two out of the following three guarantees: Consistency (all nodes see the same data at the same time), Availability (every request receives a response about whether it was successful or failed), and Partition Tolerance (the system continues to operate despite arbitrary partitioning due to network failures).

**Blockchain Trilemma**
This is a concept in blockchain technology that posits it's impossible to fully achieve all three of the following features at once: Security (the network can resist attacks), Scalability (the network can process a high number of transactions), and Decentralization (all peers in the network are equal, and there are no trusted third parties).

**Ryge's Trilemma**
This is a concept in information security where three desirable attributes - Anonymity, Free Speech, and Accountability - are in conflict. The idea is that you can have any two, but not all three together. If you have anonymity and free speech, you lose accountability. If you have free speech and accountability, you lose anonymity. And if you have anonymity and accountability, you lose free speech.

**Zooko's Triangle**
This is a concept in naming systems which argues that names can't be all three of the following: Secure (names honestly represent the identity of the named entity), Decentralized (no central authority is needed to control name allocation), and Human-meaningful (names are meaningful and memorable to humans). More recent developments in technology, such as blockchain systems, are challenging the notion of Zooko's Triangle, with claims that all three properties can be satisfied to some extent.

## Explain self stabilization

This is a concept in distributed computing introduced by Dijkstra in 1974. It's a property of a system that guarantees its ability to recover and stabilize itself, regardless of the initial state it starts from.

1. **Convergence**: This refers to the system's ability to eventually reach a correct state, no matter what state it started in. Even if it begins in an incorrect or unstable state, it's guaranteed to arrive at a correct state after a finite amount of time.

2. **Closure**: This means that once the system is in a correct state, it will remain in that state, assuming no new faults are introduced. This property ensures that the system maintains stability over time.

Self-stabilization allows a distributed system to recover from transient faults, irrespective of their nature. In other words, even if something temporarily goes wrong, a self-stabilizing system is capable of returning to a stable, correct state by itself.

**Example - Spanning-tree Protocol**
This is a networking protocol that prevents loops in a network of connected nodes by creating a spanning tree. If a loop or other fault occurs, the protocol automatically recalculates the tree to remove the fault, demonstrating self-stabilization. It starts from any state, figures out the correct configuration (convergence), and maintains this correct configuration unless a change in the network occurs (closure).

## What is a Sybil attack and how can it be mitigated

A Sybil attack involves a malicious entity creating multiple fake identities (nodes) in a network.

**Example**
In a peer-to-peer network where decisions are made based on a majority vote, a malicious user could create hundreds of fake identities. When a vote occurs, the attacker could then manipulate the outcome by making all their fake identities vote in their favor.

**Mitigation**

**Use authentication with trusted party that limits identity creation**
For instance, a network could require a trusted third party to verify each new identity. This could prevent a single entity from creating multiple identities.

**Use “external” identities (IP address, MAC, e-mail)**
By tying identities to real-world characteristics such as IP addresses, MAC addresses, or email accounts, it could make it more difficult for an attacker to create numerous fake identities.

**Use “expensive” identities (solve computational puzzles, require payment)**
By making identity creation costly, either through computational work (like solving puzzles) or actual monetary payment, the system could deter Sybil attacks. --> Mining in Bitcoin / Proof of Stake in Ethereum

## What is an eclipse attack and how can it be mitigated?

In an eclipse attack one or multiple nodes are separated / isolated from the rest of the network. The goals of this attack are DoS, surveilance and censorship. This attack can be combined with a sybil attack. First increase the number of nodes in the network which are under the attackers control and then use those nodes to isolate node(s) (Take over routing tables, peer discovery)

**Mitigation**
**Large Number of Connections**
By maintaining a large number of connections, a node can reduce the risk of being isolated. The more connections a node has, the harder it is for an attacker to control all its communications.

**Replication**
By replicating data across multiple nodes, the network can reduce the risk of any single node being fed false information. If a node is attacked, it can cross-verify its data with replicated copies.

**Diverse Neighbor Selection**
By choosing peers from diverse IP subnets and geographic locations, a node can make it more difficult for an attacker to isolate it. This is because the attacker would need to control nodes across a wider range of locations and IP addresses.
 
**Aggressive Discovery**
Also known as "continuous bootstrapping", this involves regularly finding and connecting to new peers. This increases the diversity of connections and makes it harder for an attacker to monopolize a node's peer list.

**Audit Neighbor Behavior**
If possible, monitor the behavior of neighboring nodes. Unusual behavior could indicate an eclipse attack.

**Prefer Long-Lived Connections / Old Peers**
Older peers are more likely to be trustworthy, as they've been part of the network for a long time without causing problems. By preferring these connections, a node can reduce its exposure to potentially malicious new nodes.

## What is a poisoning attack and how can it be mitigated?

Nodes provide false information:
- wrong routing tables
- wrong meta data
- wrong performance measurements

**Targeted Misinformation**
Can also involve the spread of false transaction information in a blockchain network, or false file information in a file-sharing network.

**Erosion of Trust**
The aim of such an attack could also be to undermine trust within the network, which can be particularly damaging in peer-to-peer networks where trust is essential for efficient operation.

**Attack Strategy**
Poisoning attacks can be both random (spread of general misinformation) and targeted (spread of misinformation aimed at specific nodes or parts of the network).

**Mitigation**
Mitigation strategies can include things like robust data verification methods, trust-based or reputation-based networking models, and effective audit and response systems to detect and handle false information.

## What is a timing attack and how can it be mitigated?

**Measure latency to determine origin of data**
A malicious node could analyze the time it takes for data to reach it, using that information to make guesses about where the data originated. For example, if it consistently receives data from a certain node faster than from others, it might deduce that the node is the originator of the data.
 
**Delay messages**
A node could deliberately delay forwarding messages. This could disrupt the operation of the network, cause timeouts, or change the perceived origin of messages (since messages from the actual originator will now take longer to arrive).

**Send messages using particular timing patterns to aid correlation**
A node could send messages in a specific pattern, allowing other nodes (or an external observer) to correlate those messages with certain activities or information. For instance, it might send messages in quick succession whenever a certain type of transaction occurs, signaling that transaction to any observer aware of the pattern.

**Include wrong timestamps (or just have the wrong time set...)**
A node could manipulate timestamps in its messages or have its system clock set to the wrong time, confusing other nodes about when events actually happened or disrupting time-based protocols.

**Mitigation**

**Uniform response times**
Designing systems so that they take a consistent amount of time to respond, regardless of the input, can make it difficult for an attacker to gain useful information from timing analysis.

**Random delays**
Adding random delays to certain operations can disrupt timing patterns and make correlation harder.

**Timestamp validation**
Ensuring that timestamps are consistent with other nodes' clocks can prevent attacks based on false timestamps.

**Anomaly detection systems**
Systems that monitor for unusual timing patterns can help detect potential timing attacks.

## What is Secure Multiparty Computation?
  
Secure Multiparty Computation (SMC) is a subfield of cryptography that focuses on enabling multiple parties to jointly compute a function over their inputs while keeping those inputs private. This is a powerful tool when dealing with confidential data that shouldn't be revealed to other participants.

Here's a simple example: Suppose there are three friends, Alice, Bob, and Charlie, and they want to know who has the highest salary, but none of them wants to disclose their individual salaries. Secure multiparty computation allows them to compute the function (in this case, finding the maximum salary) without revealing their individual inputs.

Here's how a broad process might work:

1. Alice, Bob, and Charlie each encrypt their salaries.
2. They then collectively perform computations on these encrypted values. In this process, the encryption ensures that no one can infer the original values.
3. After the computations, the result is decrypted to reveal the maximum salary. Importantly, this result does not allow them to infer individual salaries.

This process provides an output of the function they wanted to compute (the maximum salary), but none of the participants can learn anything more about the other parties' inputs (their individual salaries) apart from what can be inferred from the output.

Secure Multiparty Computation can be applied to more complex situations as well. For instance, in a privacy-preserving medical research study, researchers could compute statistical functions on encrypted health data from many participants. Each participant would provide encrypted inputs, and the researchers could compute averages, correlations, etc., on the encrypted data, learning the statistical results without ever seeing the individual health records.

SMC can be quite complex and requires careful implementation to ensure privacy and correctness. Its security is based on various cryptographic techniques like homomorphic encryption, secret sharing, and zero-knowledge proofs.

--> Beispiele sind ganz am Schluss bei den Slides. Versteht keiner.