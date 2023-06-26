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