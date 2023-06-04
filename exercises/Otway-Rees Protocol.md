tags: #AC1 
links: [[exercises/000 Index|Index]]

---
# Otway-Rees Protocol

![[Otway-Rees_Protocol_Image.png]]

The protocol can be specified as shown in the security protocol notation above, where **A**lice is authenticating herself to **B**ob using a server **S** (TTP) (**M** is a session-identifier, $N_A$ and $N_B$ are nonces)
Note: The above steps do not authenticate **B** to **A**.

Pros:

* Only 4 messages as Kerberos, but completely different messages.
* Does not require clock synchronisation.

Cons:

**Interception attacks**
These attacks leave the intruder with the session key and may exclude one of the parties from the conversation.

1. Masquerading Attack: In this attack, the intruder intercepts the first message sent by Alice and pretends to be Bob. The intruder then constructs the second message, replacing Bob's identity with their own and using their own key to encrypt the message. When the server receives the second message, it associates the session key with the intruder's identity instead of Bob's. As a result, Alice unknowingly shares the session key with the intruder, excluding Bob from the conversation.
    
2. Arity Attack: In the arity attack, the intruder intercepts the second message sent by Bob. The intruder then responds to Bob using the two ciphertexts obtained from the intercepted message. Without any check to prevent it, the intruder manipulates the protocol in a way that the session key becomes known to the intruder, either as a shared key between Alice and Bob or as a key involving Alice, Bob, and the intruder. This attack compromises the security of the session key.
    
3. Message Removal Attack: In this attack, the intruder intercepts the first message sent by Alice and removes the plaintext values of A and B. The intruder then uses this modified message as if it were the fourth message in the protocol, omitting the actual second and third messages. This manipulation results in Alice communicating with the intruder using the session key M (or M,A,B) as if it were a legitimate session key between Alice and Bob.

**Disruptive attacks**
This attack allows the intruder to disrupt the communication but does not allow the intruder to gain access to it.

1. An intruder can arrange for A and B to end up with different keys. After message 3 B has got the shared key $K_{ab}$. The intruder can then intercept message 4 so that A does not get the key. The intruder can then resend message 2 and intercept the response before it reaches B. So the intruder got a new key $K'_{ab}$. This one the intruder then sends to A. So in the end A and B have a different key and can't communicate.


Sources: [Wikipedia](https://en.wikipedia.org/wiki/Otway%E2%80%93Rees_protocol) + ChatGPT

---
tags: #AC1 
links: [[exercises/000 Index|Index]]