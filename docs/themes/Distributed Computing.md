tags: #asymmetric 

# Distributed Computing

links: [[210 AC2 TOC - Anonymity|AC2 TOC - Anonymity]] - [[themes/000 Index|Index]]

---

## The 8 Fallacies of Distributed Computing

1. The network is reliable
2. Latency is zero
3. Bandwidth is infinite
4. The network is secure
5. Topology does not change
6. There is one administrator
7. Transport cost is zero
8. The network is homogeneous

## Limits on authentication

**Boyd's Theorem I**

> "Suppose that a user has either a confidentiality channel to her, or an authentication channel from her, at some state of the system. Then in the previous state of the system such a channel must also exist. By an inductive argument, such a channel exists at all previous states."

**Example**

- **Now**: Alice sends an encrypted message to Bob. The message is confidential because only Bob, who has the decryption key, can read it.
- **Before**: According to Boyd's Theorem I, since the message is confidential now, it must have been confidential in the previous moment as well. This could be the moment when Alice was typing the message on her computer. Since no one else has access to her computer, the message is confidential at this time as well.
- **Even Before**: Going one step back, even when Alice was thinking about what to write in the message, the information was still confidential because it was only in her mind.

**Boyd's Theorem II**

> "Secure communication between any two users may be established by a sequence of secure key transfers if there is a trusted chain from each one to the other"

**Example**

Consider Alice wants to send a secure message to Bob, but they have never met, and therefore, haven't exchanged any encryption keys. But Alice knows and trusts Charlie, who in turn knows and trusts Bob. Alice can securely give Charlie an encryption key (since she trusts him). Charlie can then pass this key to Bob (since Bob trusts him). Now, Bob has the encryption key, and he can use it to decrypt any messages that Alice sends him. Even though Alice and Bob have never met, they can still communicate securely because of the chain of trust involving Charlie.

## Zfone Authentication (ZRTP)

1. **Diffie-Hellman exchange**: This establishes the initial secure communication channel, tying into Boyd's Theorem I.
2. **Use of keying material from previous sessions**: Even if an attacker is present during one call, they can't affect future calls, which provides continuity of the secure channel across different states.
3. **Generation of Short Authentication String (SAS)**: ZRTP generates a Short Authentication String (SAS), a hash of the DH public keys.
4. **Reading the SAS**: Alice and Bob read the SAS to each other. They both recognize each other's voices, providing a form of human authentication.

$\rightarrow$ ZRTP fails standard man-in-the-middle-attack

## Self stabilisation

This is a concept introduced by Dijkstra in 1974. It's a property of a system that guarantees its ability to recover and stabilize itself, regardless of the initial state it starts from.

1. **Convergence**: This refers to the system's ability to eventually reach a correct state, no matter what state it started in.
2. **Closure**: This means that once the system is in a correct state, it will remain in that state, assuming no new faults are introduced.

> Self-stabilization enables a distributed algorithm to recover from a transient fault **regardless of its nature**

Example: Spanning-tree Protocol from Networking

## Secure Multipart Computation (SMC)

> Compute result in distributed manner without revealing what exactly is computed.

- Enabling multiple parties to jointly compute a function over their inputs while keeping those inputs private
- Usually only one learns the result
- Can be useful e.g. in privacy-preserving medical research studies (compute averages, correlations on encrypted data)

**Example**

Suppose there are three friends, Alice, Bob, and Charlie, and they want to know who has the highest salary, but none of them wants to disclose their individual salaries. Secure multipart computation allows them to compute the function (in this case, finding the maximum salary) without revealing their individual inputs.

1. Alice, Bob, and Charlie each encrypt their salaries.
2. They then collectively perform computations on these encrypted values. In this process, the encryption ensures that no one can infer the original values.
3. After the computations, the result is decrypted to reveal the maximum salary. Importantly, this result does not allow them to infer individual salaries.

---
links: [[210 AC2 TOC - Anonymity|AC2 TOC - Anonymity]] - [[themes/000 Index|Index]]