tags: #asymmetric 
links:  [[Topic 10 - Anonymity]], [[themes/000 Index|Index]]

---
# Attacks

## What are possible attacks to reveal someones identity?

**All nodes collaborate against the victim**
This is the most severe scenario. Every single node in the entire network is conspiring against the victim, monitoring and sharing information about their activities. It means that no matter which path the victim's data takes, it's being tracked.

**All directly adjacent nodes collaborate**
This is a less severe situation than the first, but still serious. Only the nodes directly connected to the victim (those the victim communicates with directly) are conspiring. While this might not capture all of the victim's network activity (depending on the network's topology and routing), it captures a significant amount, especially if the network is decentralized and the victim communicates with many nodes.

**All non-collaborating adjacent nodes are made unreachable from the victim**
This scenario describes a situation where the nodes directly connected to the victim that aren't conspiring (and hence would provide secure, anonymous paths for the victim's data) are somehow taken offline or blocked. This could force the victim to use the collaborating nodes, effectively turning this into scenario 2.

**The victim is required to prove his innocence**
This scenario is a bit different, as it's not about the network's nodes colluding against the victim. Instead, it's about a situation where the victim is accused of wrongdoing and must provide proof of innocence, which could potentially involve revealing personal information or specific activities that compromise their anonymity. This is a challenging situation because it forces a conflict between maintaining anonymity and addressing the accusation.


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

---
links:  [[Topic 10 - Anonymity]], [[themes/000 Index|Index]]