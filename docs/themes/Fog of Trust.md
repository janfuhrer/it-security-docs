tags: #asymmetric #WebOfTrust #FogOfTrust

# Fog of Trust

links: [[211 AC2 TOC - DPKI|AC2 TOC DPKI]] - [[themes/000 Index|Index]]

---

## Problems of Web of Trust

- publishing who certified whom exposes the social graph
- **Solution**: do not publish the graph, use "secure multi-part computation" ([[Distributed Computing#Secure Multipart Computation (SMC)|SMC]]) protocol for private set intersection cardinality with signatures.
	- We will only consider paths with **one** intermediary

Measuring and comparing private set intersection cardinality means that we are able to calculate how much similarities two sets have. To do this without exposing the social graph (which would leak information about who trusts whom), we can use [[Distributed Computing#Secure Multipart Computation (SMC)|SMC]] and sign the result to make it verifiable for the counterpart. This method is used in the straw-man protocol.

## Straw-man protocol

> a *straw-man proposal* is a brainstormed simple draft proposal intended to generate discussion of its disadvantages and to spur the generation of new and better proposal.

### Version 1: Straw-man protocol

- Alice wants to compute $n := |\mathcal{L_A} \cap \mathcal{L_B}|$, where $\mathcal{L_A}$ and $\mathcal{L_B}$ are the sets of trusted public keys of Alice (as verifiers) and Bob (as signers). $n$ describes the number of keys which both trust. If $n$ is high enough, Alice might trust Bob and therefore his list of public keys of signers. If Alice trusts enough verifiers, whose signatures are deemed trustworthy by Bob, Alice might trust the signature ob Bob's trusted signers.
- suppose each user has a private key $c_i$ and the corresponding public key is $C_i := g^{c_i}$ where $g$ is the generator

**Setup**

- $\mathcal{L_A}$: set of public keys representing Alice trusted verifiers
- $\mathcal{L_B}$: set of public keys representing Bob's signers
- Alice picks an ephemeral private scalar $t_A \in \mathbb{F}_p$, Bob picks $t_B \in \mathbb{F}_p$

![[straw-man-protocol.png]]

1. Alice sends a set $\mathcal{X}_A$ which contains the trusted verifiers public keys to the power of the ephemeral private scalar $t_A$ to Bob (blinded trusted verifiers)
2. Bob calculates two sets: 
	1. Set $\mathcal{X}_B$ which contains the trusted signers public keys to the power of the ephemeral private scalar $t_B$ **and** 
	2. Set $\mathcal{Y}_B$ which contains the blinded verifiers of Alice to the power of the ephemeral private scalar $t_B$
	3. Bob then sends $\mathcal{X}_B$ and $\mathcal{Y}_B$ to Alice
3. Alice can now calculate $\mathcal{Y}_A$ by taking each element of Bob's $\mathcal{X}_B$ (blinded trusted signers of Bob)
4. Alice can now compare $\mathcal{Y}_A$ with $\mathcal{Y}_B$ and count the amount of equal values which gives the value $n = |\mathcal{Y}_A \cap \mathcal{Y}_B|$ she is looking for (linear cost).

Since the trusted verifiers of Alice and the trusted signers of Bob are blinded by their respective ephemeral private scalars $t_A$ and $t_B$ (which leads to some double blinding behaviour), the identities of the verifiers and signers is not leaked and therefore the social graph remains secret.

(Because [[Distributed Computing#Secure Multipart Computation (SMC)|SMC]] works on [[Group Theory#^0078b7|homomorphic]] groups, this works because the values structurally remain the same, due to the properties of the mapping function $f$ between the different groups)

**Attacks**

![[straw-man-protocol_attacks.png]]

This means that if Bob can control two verifiers of Alice's trusted verifiers set, Bob can betray her by manipulating the resulting $n$ for Alice as he suggests by choosing a sub quantity $K$ of the Field $\mathbb{F}_p$ such that the quantities $\mathcal{X}_B$ and $\mathcal{Y}_B$ contain as much trusted signers as he wants make Alice believe are intersecting with her trusted verifiers. Since the blinded trusted verifiers of $\mathcal{X}_A$ are randomized (hash), Alice cannot find out that Bob is blinding the same verifier $k$-times.

### Version 1: Cut & choose

The above described attack can be omitted by implementing a Cut & Choose mechanism as follows:

- assume a fixed system security parameter $k \geq 1$
- let Bob use secrets $t_{B,i}$ for $i \in \{1,...,k\}$, and let $\mathcal{X}_{B,i}$ and $\mathcal{Y}_{B,i}$ be blinded sets over the different $t_{B,i}$ as in the straw-man version
- For any list or set $Z$, define $Z' := \{h(x)|x \in Z\}$

![[cut-and-choose.png]]

1. Alice again computes the blinded trusted verifiers Set $\mathcal{X}_A$ but sorts the set before sending it to Bob
2. Bob responds with $k$ commitments $\mathcal{X'}_{B_i}$ and $\mathcal{Y'}_{B_i}$ for $i \in \{1,...,k\}$. 
3. Alice now chooses a subset $J$ of all the commitments supplied by Bob and sends the subset of interest to Bob
4. Bob then reveals $\mathcal{X}_{B_j}$ for $j \in J$ **plus** all private ephemeral scalars $t_{B_j}, j \notin J$ which are **not** part of the chosen subset $J$.
5. Alice can now **verify** that Bob is not lying to her: 
	1. Alice crosschecks all commitments inside $\mathcal{Y'}_{B_j}$ for all received private ephemeral scalars $t_{B_j}, j \notin J$ of Bob
	2. Verifies the commitment of all $\mathcal{X}_{B_j}, j \in J$ and computes $\mathcal{Y}_{A_j}$ by taking each element of Bob's trusted signers set to the power of Alice ephemeral private scalar $t_A$ for all $j \in J$.
	3. Alice can now also blind her $\mathcal{Y}_{A_j}$ to receive $\mathcal{Y'}_{A_j}$. Since she earlier received $\mathcal{Y'}_{B_i}$ and knows the subset $J$ (since she chose it earlier), she can now calculate $n = |\mathcal{Y'}_{A_j} \cap \mathcal{Y'}_{B_j}|$ for each $j \in J. Each received $n$ should be equal to the others. If this is the case Alice can be sure, that Bob didn't fool her into trusting untrustworthy signers.

**Verification**

(for explanation check points 5 to X above)

![[cut-and-choose_verification.png]]

### Version 2: Private Set Intersection with Subscriber Signatures

- Naturally, signers are willing to *sign* that Bob's key is Bob's key
- We still want the identities of the signer to be private!
- [[Advanced Cryptographic Primitives#Boneh–Lynn–Shacham (BLS) signatures|BLS signatures]] are compatible with our blinding $\rightarrow$ integrate them with our cut & choose version of the protocol
- Costs are linear in set size, unlike prior work this **needs no CA**

---
links: [[211 AC2 TOC - DPKI|AC2 TOC DPKI]] - [[themes/000 Index|Index]]