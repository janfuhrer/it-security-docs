tags: #asymmetric 
links:  [[Topic 10 - Anonymity]], [[themes/000 Index|Index]]

---
# Distributed Computing

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

---
links:  [[Topic 10 - Anonymity]], [[themes/000 Index|Index]]