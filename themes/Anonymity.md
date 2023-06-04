### What is anonymity?
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

### What is pseudonymity
- A pseudonym is an identity for an entity in the system. It is a “false identity” and not the true identity of the holder of the pseudonym.
- Nobody, but (maybe) a trusted party may be able to link a pseudonym to the true identity of the holder of the pseudonym.
- A pseudonym can be tracked. We can observe its behaviour, but we do not learn who it is.

### How can a user be identified?
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

### What is the difference between Sender Anonymity and Reciever Anonymity?
- Sender anonymity is when the sender's identity is hidden during message transmission. However, potential traces like IP addresses or metadata may provide a path back to the sender. R
- Receiver anonymity allows the recipient to receive messages without revealing their identity. Since the receiver is not generating traffic, the chance of tracing back to them is less, unless the system logs incoming connections. The level of anonymity depends on the system and protocols used.

### How can anonymity be evaluated?
- number of known attacks
- lowest complexity of successful attacks
- informationleaked through messages and maintenance procedures
- number of users

### What is probability distribution?
It's a statistical function describing all possible values and their likelihoods for a random variable. It gives a mathematical overview of the outcomes of a random event and their corresponding probabilities.

Example: In a dice roll, the outcome can be 1 through 6, each with an equal probability of 1/6. This forms the probability distribution for a fair six-sided die roll.

### What is an anonymity set and what role does it play in anonymity?
It's the group of all potential users that could be responsible for an action, contributing to the anonymity of the actual user.

Examples of large anonymity sets:
- Any human
- Any human with Internet access
- Any human speaking German
- Any human speaking German with Internet access awake at 3am CEST

The larger and more evenly distributed the anonymity set, the greater the anonymity. Each user in this set is a potential suspect, making it harder to identify the actual user.

### What is maximum likelihood?
It's the highest probability that a particular user in the anonymity set is responsible. Legal cases require varying levels of ML for successful prosecution.

### What is entropy in anonymity
GPT:
Entropy's Role in Anonymity: Entropy, as a concept from information theory, quantifies the level of uncertainty or randomness in a set of data. In the context of anonymity, entropy represents the measure of uncertainty about the identity of a user within an anonymity set. A higher entropy denotes a greater degree of anonymity, as there's more uncertainty for an attacker trying to identify a specific user.

The link between entropy and probability stems from the fact that entropy captures the uncertainty linked to the various probabilities of different outcomes. For instance, if all users in an anonymity set are equally likely to be the party of interest to an attacker, the uncertainty (and hence entropy) is at its maximum. However, if some users are more likely to be the target (perhaps due to partial information the attacker has obtained), the uncertainty (and entropy) decreases.

This leads to the concept of "bits of additional information." In information theory, a bit is a unit that reduces uncertainty by half. When we say "entropy is the expected number of bits of additional information that the attacker needs to definitely identify the user," we refer to the theoretical amount of information needed to eliminate all uncertainty, i.e., to pinpoint the user's identity amongst the anonymity set with certainty. This doesn't directly translate to discrete pieces of knowledge, but rather to an overall reduction of uncertainty in a probabilistic sense.

An illustrative example involves a deck of 52 playing cards. If a card is drawn randomly, the uncertainty (or entropy) about which card is chosen is log2(52) ≈ 5.7 bits, as there are 52 equally likely possibilities. If the attacker learns that the drawn card is a heart, the number of possibilities reduces to 13, and the entropy drops to log2(13) ≈ 3.7 bits. This reduction in entropy of about 2 bits represents the additional information the attacker gained. In this case, the remaining entropy (3.7 bits) symbolizes the amount of further information theoretically needed to identify the exact card drawn. The higher the initial entropy, the more additional information is needed, and thus, the stronger the initial degree of anonymity.

![[Pasted image 20230603165249.png]]
# Wieso wird hie /1000 und /10 grächnet?

### What are possible attacks to reveal someones identity?

#### All nodes collaborate against the victim
This is the most severe scenario. Every single node in the entire network is conspiring against the victim, monitoring and sharing information about their activities. It means that no matter which path the victim's data takes, it's being tracked.

#### All directly adjacent nodes collaborate
This is a less severe situation than the first, but still serious. Only the nodes directly connected to the victim (those the victim communicates with directly) are conspiring. While this might not capture all of the victim's network activity (depending on the network's topology and routing), it captures a significant amount, especially if the network is decentralized and the victim communicates with many nodes.

#### All non-collaborating adjacent nodes are made unreachable from the victim
This scenario describes a situation where the nodes directly connected to the victim that aren't conspiring (and hence would provide secure, anonymous paths for the victim's data) are somehow taken offline or blocked. This could force the victim to use the collaborating nodes, effectively turning this into scenario 2.

#### The victim is required to prove his innocence
This scenario is a bit different, as it's not about the network's nodes colluding against the victim. Instead, it's about a situation where the victim is accused of wrongdoing and must provide proof of innocence, which could potentially involve revealing personal information or specific activities that compromise their anonymity. This is a challenging situation because it forces a conflict between maintaining anonymity and addressing the accusation.

### What is the problem with the economy of anonymity?

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

### Explain the Dining Cryptographers Problem
Every two cryptographers establish a shared one-bit secret. Everyone then makes an XOR out of the two shared one-bit secrets and reveals the result.

- If they payed they invert the XOR
- If they didn't pay they just reveal the XOR of the shared one-bit secrets

Finally the revealed results are XORed aswell

- If the result is 1 then someone payed but this person stays anonymous
- If the result is 0 then the NSA payed

### What is mixing and how does it work?
A cryptographic protocol used to provide anonymity for network communications. This approach to maintaining privacy is implemented by a mix network, owhich uses a chain of mix nodes.

**Example**
1. Each message is encrypted with the public keys of the mix nodes in reverse order of the nodes it will pass through. The initial encryption might use the public key of the last node, then the next-to-last, and so on, until finally the message is encrypted with the key of the first node.

2. The message is then sent through the network, passing through each mix node in order.

3. Each mix node, upon receiving a message, uses its private key to decrypt its layer of encryption. This reveals the address of the next node to which the message should be sent.

4. Additionally, each mix node changes the appearance of the message even if it can't read its contents. It does this by decrypting and re-encrypting the message, making it difficult to link the incoming and outgoing messages. The node might also batch multiple messages together, changing the order before forwarding them, which further obscures the origin-destination link.

5. This process is repeated until the message reaches its final destination.

### What are different types of mixing?
**Threshold Mix**
A type of mix that waits until it has received messages from a certain number of users (the threshold) before it sends them out in a random order.

**Timed Mix**
This mix collects messages for a certain period of time before sending them out in a random order.

**Pool Mix**
In a pool mix, incoming messages are added to a pool. A certain number of messages are randomly selected from the pool and sent out, while the remaining messages stay in the pool for the next round.

### What is Mixminion?
Mixminion is an anonymous remailer protocol that was designed to improve upon earlier protocols by offering better resistance to attacks, and more reliable delivery of messages. It's a mixmailer which uses mix networks for email communication, effectively anonymizing the sender and recipient of an email. Compared to previous mixers it has some advantages.

**Possibility to Reply**
One major advancement Mixminion brings over previous remailer protocols is the ability for recipients to reply to anonymous emails without knowing the sender's actual identity.

**Directory Servers and Reputation System**
Directory servers in Mixminion keep track of available mix nodes (remailers) and their reputations. This system helps users to select reliable and trustworthy nodes for routing their messages.

**Exit Policies**
Just like with Tor, mix nodes in Mixminion can have exit policies which allow the operator of the node to determine what type of traffic is allowed to exit their node and to where. This can help to manage legal and ethical considerations associated with running a node.

### How do replies work in Mixminion?

Example in which Alice sends a message to Bob and Bob can answer without knowing Alice:
1. Alice prepares her message to Bob and includes the path for Bob's reply within her message. This path includes a "crossover" node and the second leg of the path after the crossover. It's worth noting that the path is encrypted, and the encryption layering matches the order of nodes in the path.

2. Alice then selects a series of nodes (the first leg) in the Mixminion network through which to send her message. She adds this to the existing path information (creating a complete path from Alice to Bob and back to Alice), and then encrypts the message and path data in layers, where each layer corresponds to a node in the path.

3. Alice sends her message into the Mixminion network. Each node in the path decrypts its layer of the message, revealing where to send the message next, and then re-encrypts the message before sending it on to help maintain anonymity.

4. Eventually, the message arrives at Bob's email address. Bob can read Alice's message because it was encrypted for him. He can see the encrypted reply path but cannot decipher it because it is encrypted for the nodes in the path, not for him.

5. Now, Bob prepares his reply and attaches Alice's encrypted reply path to it. He then chooses his own series of nodes (a new first leg) to reach the crossover node, encrypts his message and the entire path in layers, and sends it into the Mixminion network.

6. When Bob's reply reaches the crossover node, the node decrypts its layer of the message to find out where to send the message next. The remaining part of the path is still encrypted and unreadable to the crossover node.

7. The message continues to travel along the second leg of the path that Alice originally provided. Finally, the reply arrives back at Alice's email address.