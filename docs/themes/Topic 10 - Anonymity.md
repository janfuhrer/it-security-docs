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


## Explain self stabilisation

This is a concept in distributed computing introduced by Dijkstra in 1974. It's a property of a system that guarantees its ability to recover and stabilize itself, regardless of the initial state it starts from.

1. **Convergence**: This refers to the system's ability to eventually reach a correct state, no matter what state it started in. Even if it begins in an incorrect or unstable state, it's guaranteed to arrive at a correct state after a finite amount of time.

2. **Closure**: This means that once the system is in a correct state, it will remain in that state, assuming no new faults are introduced. This property ensures that the system maintains stability over time.

Self-stabilization allows a distributed system to recover from transient faults, irrespective of their nature. In other words, even if something temporarily goes wrong, a self-stabilizing system is capable of returning to a stable, correct state by itself.

**Example - Spanning-tree Protocol**
This is a networking protocol that prevents loops in a network of connected nodes by creating a spanning tree. If a loop or other fault occurs, the protocol automatically recalculates the tree to remove the fault, demonstrating self-stabilization. It starts from any state, figures out the correct configuration (convergence), and maintains this correct configuration unless a change in the network occurs (closure).


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