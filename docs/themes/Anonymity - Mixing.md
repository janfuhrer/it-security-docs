tags: #asymmetric #mixing

# Mixing

links: [[210 AC2 TOC - Anonymity|AC2 TOC - Anonymity]] - [[themes/000 Index|Index]]

---

## Definition

- see [Dining cryptographers problem](https://en.wikipedia.org/wiki/Dining_cryptographers_problem)
- goal is: **destroying linkability**

![[mixing.png]]

## Types of mixing

### Threshold Mix

A type of mix that waits until it has received messages from a certain number of users (the threshold) before it sends them out in a random order.

![[threshold-mix.png]]

### Timed Mix

This mix collects messages for a certain period of time before sending them out in a random order.

- **Advantages**: performance guaranty
- **Disadvantages**: if only one input $\rightarrow$ same output, n-1 attack (send all inputs -1)

![[timed-mix.png]]

### Pool Mix

In a pool mix, incoming messages are added to a pool. A certain number of messages are randomly selected from the pool and sent out, while the remaining messages stay in the pool for the next round.

- **Advantages**: $P_{min}$ & $P_{max}$, n-1 attack not possible
- **Disadvantages**: a message may stay forever in the pool

![[pool-mix.png]]

### Mixminion

- *based on mixmailers*: uses mix networks for email communication, effectively anonymizing the sender and recipient of an email (only for email application)
- *possibility to reply*: without knowing the sender's actual identity
- *directory servers to evaluate participating remailers*: helps users to select reliable and trustworthy nodes for routing their message
- *exit policies*: like with Tor, nodes can have policies which allow the operator to determine what type of traffic is allowed to exit their node and to where (legal and ethical considerations)

**Key ideas**

- when a message traverses mixminion, each node must decrypt the message using its (ephemeral) private key
- the key idea behind the replies is splitting the path into two legs:
	- the first half is chosen by the responder to hide the responder identity
	- ﻿﻿the second half was communicated by the receiver to hide the receiver identity
	- ﻿﻿a crossover-node in the middle is used to switch the headers specifying the path

```
Alice -------------------------------------------> Bob
Alice <-- second leg -- Crossover <-- first leg -- Bob
```

**Replay attacks**

- servers keep hash of previously processed messages until the server key is rotated
- bounded amount of state in the server, no possibility for replay attack due to key rotation

**Directory Servers**

- inform users about servers
- probe servers for reliability
- allow partitioning attack $\rightarrow$ users are advised to query all directory servers to obtain a complete network view

**Nymservers**

- Nyms (short for pseudonyms) allow users to maintain long-term identities without revealing their true identities or their locations
- A nym server stores nyms and the associated reply blocks
- Vulnerable to DoS attacks

**Problems**

- No benefits / incentives of running a mixer
- A lot of public key cryptography (slow)
- Users have to trust directory servers (those also don't have an incentive to act good)
- Servers have to keep state (resources)
- Service is limited to E-Mail because of high latency
- Exit nodes can be liable for legal action
- No functionality to avoid DoS attacks
- Statistical correlation of entities communicating over time is still possible if the whole network is observed
- Bridge between anonymous network and a traditional protocol is difficult

---
links: [[210 AC2 TOC - Anonymity|AC2 TOC - Anonymity]] - [[themes/000 Index|Index]]