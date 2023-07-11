tags: #asymmetric 

# Attacks

links: [[210 AC2 TOC - Anonymity|AC2 TOC - Anonymity]] - [[themes/000 Index|Index]]

---

## Attacks to avoid

Hopeless situations:

- All nodes collaborate against the victim
- All directly adjacent nodes collaborate
- All non-collaborating adjacent nodes are made unreachable form the victim
- The victim is required to prove his innocent $\rightarrow$ not possible in an anonymous system!

## Sybil Attacks

- Insert a node multiple times into a network, each time with a different identity
- Position a node for next step on attack:
	- Attack connectivity of the network
	- Attack replica set
	- In case of majority votes, be the majority

**Mitigation**

- Use authentication with trusted party that limits identity creation
- Use “external” identities (IP address, MAC, e-mail)
- Use “expensive” identities (solve computational puzzles, require payment)

> Without trusted authority to certify identities, no realistic approach exists to completely stop the Sybil attack.

## Eclipse Attacks

- Separate a node or group of nodes from the rest of the network
- isolate peers (DoS, surveillance) or isolate data (censorship)
- **Techniques**: use Sybil attack to increase number of malicious nodes, take over routing tables/ peer discovery

**Mitigation**

- Large number of connections (reduce risk of being isolated)
- Replication (replicating data across multiple nodes, cross-verify data with copies)
- Diverse neighbour selection (different IP subnets/ geographic locations, make it more difficult for an attacker to control all communications)
- Aggressive Discovery ("continuous" bootstrap, regularly finding and connecting to new peers)
- Audit neighbour behaviour (if possible, detect eclipse attack)
- Prefer long-lived connections / old peers

## Poisoning Attacks

- **Attack**: Nodes provide false information:
	- wrong routing tables
	- wrong meta data
	- wrong performance measurements
- **Aim**: undermine trust within the network, spread of false information (e.g. in a blockchain network)

**Mitigation**

- robust data verification methods
- trust- or reputation-based networking models

## Timing Attacks

- Nodes can:
	- measure latency to determine origin of data (guess about where the data originated)
	- delay messages (disrupt the operation of the network timeouts)
	- send messages using particular timing patterns to aid correlation
	- include wrong timestamps

**Mitigation**

- Uniform response time
- Random delays
- Timestamp validation
- Anomaly detection systems

---
links: [[210 AC2 TOC - Anonymity|AC2 TOC - Anonymity]] - [[themes/000 Index|Index]]