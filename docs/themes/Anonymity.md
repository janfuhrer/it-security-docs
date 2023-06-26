tags: #asymmetric #social 
links:  [[Topic 10 - Anonymity]], [[themes/000 Index|Index]]

---
# Anonymity

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
Identity
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

Example: In a dice roll, the outcome can be 1 through 6, each with an equal probability of 1/6. This forms the probability distribution for a fair six-sided dice roll.


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
High-reputation anonymizing servers with a lot of traffic are likely targets for compromise due to their value for attackers. These servers handle substantial data, making them attractive for malicious actors seeking valuable information or aiming to deanonymize users. Despite this, good security measures can help protect these servers, but their risk of compromise is higher due to their prominence.

---
links:  [[Topic 10 - Anonymity]], [[themes/000 Index|Index]]