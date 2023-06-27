tags: #symmetric #meta
links:  [[101 AC1 TOC - Intro]] - [[themes/000 Index|Index]]

---
# Computer Security Dictionary

**Information Security**

> Information security is concerned with the preservation of confidentiality, integrity and availability of information. In addition, properties such as authenticity, accountability, non-repudiation and reliability can also be involved –ISO/IEC 27000:2016

**Information assets**

Information has monetary value. Thus we speak about information assets.

**CIA**

* Confidentiality
* Integrity
* Availability

**AAA**

- Authenticity
- Accountability
- Auditablity (Non-repudiation)

**Risk**

Risk is value (cost of potential damage) multiplied by the probability of this
damage occurring.

**Vulnerability**

Inability of a system to withstand the effects of a hostile environment.

**Threat**

Possible danger that might exploit a vulnerability.

**Attack**

Attempt to expose, alter, disable, destroy, steal or gain unauthorized access to or make unauthorized use of an information asset.

**Exploit**

Action that takes advantage of a vulnerability.

**Information security incident**

Event that could lead to loss of control over an information asset.

**Cryptography** ^51231c

Practice and study of techniques for secure communication in the presence of adversaries.

![[Overview_Cryptography.png]]

**Cryptographic primitives**

Primitives are the building blocks for cryptographic protocols.

**Keys**

Keys are short information assets used for certain cryptographic operations.

**Kerckhoffs’ principle** ^8ae895

A cryptosystem should be secure even if everything about the system, except the key, is public knowledge.

**Brute-force**

A brute-force attack involves trying all the keys (until the one that works is found).

**Entropy**

Entropy describes the information content of a key or message.
A key with 128 bits of entropy requires $2^{128}$ brute-force attempts.

**Digital signatures**

Cryptographic method to add non-repudiation and message integrity features to an information asset.

**Encryption**

Encryption is the process of encoding of a message in such a way that only authorized parties can access (“decrypt”) it.

**Attacker origins**

- Insider  
- Ex-insider (“disgruntled former employee”) 
- Competitor  
- Hacktivist  
- Criminal  
- State actor  
- Researcher

**Attacker objectives**

- Fame
- Stealing information (business secrets, credentials)
- Modifying information (e.g. bank transactions)
- Abusing infected systems (e.g. spamming)
- Attacking other systems (origin obfuscation)
- Hiding (avoid detection, achieve long-term persistence)
- Contact command and control (C2) for instructions

**Vulnerability origins**

- Hardware
- Software
- Humans
- Environment

**Attack strategies**

- Large scale
- Targeted

**Defense strategies**

- Access control (physical, logical)
- Deterrance (legal, counter-attacks, auditing, accounting)
- Redundancy
- Obfuscation
- Comprehension (simplification, transparency, education) 
- Monkey wrench / havoc
- Defense-in-depth

**Protocols**

- “A protocol is a series of steps, involving two or more parties, designed to accomplish a task.”
- Everyone involved must know the steps in advance and agree to follow it.
- The protocol must be complete and unambiguous.
- For cryptographic protocols, it should not be possible to do more or learn more than what is specified in the protocol.

**Dramatis Personae**

- Alice, Bob, Carol and Dave
- Eve – Eavesdropper
- Mallory – Malicious active attacker
- Trent – Trusted arbitrator
- Walter – Warden
- Peggy – Prover
- Victor – Verifier

**Attack Personae**

- Eavesdroppers  
- Passive cheaters  
- Active cheaters  
- Real-world adversaries – Mallory

**Efficiency**

- Number of steps in protocol
- Size of messages
- Conflict resolution cost

**Statistics**

- mathematical techniques for drawing general conclusions from data samples 
- means, medians, distributions, samples, significance, bias  
- resulting aggregates may have meaning, or not  
- no hard assurances about individual inputs, only probabilities

**Machine Learning**

* Ask computer to figure out which inputs matter!
* Different techniques:
	* Supervised learning: given example inputs and desired outputs, derive “general rule”
	* Unsupervised learning: find hidden structure in data  
	* Reinforecment learning: algorithm selects actions, receives feedback based on result(s)  
* Shared outcome: data in, statistical predictors out

---
links:  [[101 AC1 TOC - Intro]] - [[themes/000 Index|Index]]