tags: #asymmetric #social 

# Anonymity

links: [[210 AC2 TOC - Anonymity|AC2 TOC - Anonymity]] - [[themes/000 Index|Index]]

---

## Definition of anonymity

- **Merriam-Webster**
	- not named or identified: “an anonymous author”, “they wish to remain anonymous”
	- of unknown authorship or origin: “an anonymous tip”
	- lacking individuality, distinction, or recognizability: “the anonymous faces in the crowd”, “the gray anonymous streets”
- **Pfitzmann**:
	- Anonymity is the state of being not identifiable within a set of subjects, the anonymity set
- **EFF**
	- Instead of using their true names to communicate, (...) people choose to speak using pseudonyms (assumed names) or anonymously (no name at all).
- **Grothoff**
	- A user’s action is anonymous if the adversary cannot link the action to the user’s identity

## Pseudonymity

- A pseudonym is an identity for an entity in the system. It is a “false identity” and not the true identity of the holder of the pseudonym.
- Nobody, but (maybe) a trusted party may be able to link a pseudonym to the true identity of the holder of the pseudonym.
- **A pseudonym can be tracked**. We can observe its behaviour, but we do not learn who it is.

## A user's identity

Includes personally identifiable information, such as:

- real name
- fingerprint
- passport number
- IP address
- MAC address
- login name

Actions includes

- Internet access
- speech
- participation in demonstration
- purchase in a store
- walking across the street

## Evaluating Anonymity

- number of known attacks
- lowest complexity of successful attacks
- information leaked through messages and maintenance procedures
- number of users (more user = more security)

## Terms

- **Sender anonymity**: the sender's identity is hidden during message transmission. However, potential traces like IP addresses or metadata may provide a path back to the sender.
- **Receiver anonymity**: allows the recipient to receive messages without revealing their identity. Since the receiver is not generating traffic, the chance of tracing back to them is less, unless the system logs incoming connections.

## Anonymity Sets

- **Anonymity Set**: It's the group of all potential users that could be responsible for an action, contributing to the anonymity of the actual user:
- Example for large sets:
	- Any human
	- Any human with Internet access
	- Any human speaking German
	- Any human speaking German with Internet access awake at 3am CEST
- Attacker computes a **probability distribution** describing the likelihood of each participant to be the responsible party.

  > Anonymity is the stronger, the larger the anonymity set and the more evenly distributed the subjects within that set are.

### Maximum likelihood (ML)

The highest probability that a particular user in the anonymity set is responsible. Legal cases require varying levels of ML for successful prosecution (e.g. for successful civil prosecution in the US, the law requires $ML \gt 1/2$)

## Anonymity Metric: Entropy

[[Entropy]], as a concept from information theory, quantifies the level of uncertainty or randomness in a set of data. In the context of anonymity, entropy represents the measure of uncertainty about the identity of a user within an anonymity set. A higher entropy denotes a greater degree of anonymity, as there's more uncertainty for an attacker trying to identify a specific user.

> Expected number of bits of additional information that the attacker needs to definitely identify the user (with absolute certainty).

## Economics & Anonymity

- Providing anonymity services has economic disincentives
	- providing anonymity services is often not cheap
	- providers may face legal risks if their services are used for unlawful activities
	- services often introduces inefficiencies such as slower data transmission due to routing through multiple nodes for obfuscation
	- anonymity services are often targets for attacks (DoS)

> The anonymizing server that has the best reputation (performance, most traffic) is presumably compromised

---
links: [[210 AC2 TOC - Anonymity|AC2 TOC - Anonymity]] - [[themes/000 Index|Index]]