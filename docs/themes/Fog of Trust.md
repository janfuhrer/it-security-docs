tags: #asymmetric 

# Fog of Trust

links: [[211 AC2 TOC DPKI|AC2 TOC DPKI]] - [[themes/000 Index|Index]]

---

## Problems of Web of Trust

- publishing who certified whom exposes the social graph
- **Solution**: do not publish the graph, use "secure multi-part computation" (SMC) protocol for private set intersection cardinality with signatures.

## Straw-man protocol

- a *straw-man proposal* is a brainstormed simple draft proposal intended to generate discussion of its disadvantages and to spur the generation of new and better proposal.

### Version 1: Straw-man protocol

- Alice wants to compute $n := |\mathcal{L_A} \cap \mathcal{L_B}|$
- suppose each user has a private key $c_i$ and the corresponding public key is $C_i := g^{c_i}$ where $g$ is the generator

**Setup**

- $\mathcal{L_A}$: set of public keys representing Alice trusted verifiers
- $\mathcal{L_B}$: set of public keys representing Bob's signers
- Alice picks an ephemeral private scalar $t_A \in \mathbb{F}_p$, Bob picks $t_B \in \mathbb{F}_p$

![[straw-man-protocol.png]]

**Attacks**

![[straw-man-protocol_attacks.png]]

### Version 1: Cut & choose

- assume a fixed system security parameter $k \geq 1$
- let Bob use secrets $t_{B,i}$ for $i \in \{1,...,k\}$, and let $X_{B,i}$ and $Y_{B,i}$ be blinded sets over the different $t_{B,i}$ as in the straw-man version
- For any list or set $Z$, define $Z' := \{h(x)|x \in Z\}$

![[cut-and-choose.png]]

**Verification**

![[cut-and-choose_verification.png]]

### Version 2: Private Set Intersection with Subscriber Signatures

- Naturally, signers are willing to *sign* that Bob's key is Bob's key
- We still want the identities of the signer to be private!
- [[Advanced Cryptographic Primitives#Boneh–Lynn–Shacham (BLS) signatures|BLS signatures]] are compatible with our blinding $\rightarrow$ integrate them with our cut & choose version of the protocol
- Costs are linear in set size, unlike prior work this **needs no CA**

---
links: [[211 AC2 TOC DPKI|AC2 TOC DPKI]] - [[themes/000 Index|Index]]