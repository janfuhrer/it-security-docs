tags: #symmetric #mac

# MAC

links: [[themes/106 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]

---

## Secrecy vs. Integrity

- **Secrecy**: encryption can be used to prevent a **passive** eavesdropper from learning anything about messages sent over an open channel.
- **Integrity**: Guarantee *message integrity* (or *message authentication*) against an **active** adversary who can inject messages on the channel or modify messages in transit.

## Encryption vs. Message Authentication

Encryption does not (in general) provide any integrity! Ciphertexts in this case are very easy to manipulate: flipping any bit in the ciphertext results in the same bit being flipped in the message that is recovered upon decryption. In fact, the same attack applies to the one-time pad encryption scheme, showing that even perfect secrecy is not sufficient to ensure the most basic level of message integrity.

## Message Authentication Codes (MACs)

Prevent an adversary from modifying a message sent by one party to another, or from injecting a new message, without the receiver detecting that the message did not originate from the intended party $\rightarrow$ both parties share a common secret

There are tow canonical application scenarios for MACs:

1. ensuring integrity for two parties communicating with each other
2. one user communicating "with himself" over time (e.g. web cookies or a user protecting the contents of his hard drive)

### Formal definition

A *message authentication code* (or MAC) consists of three probabilistic polynomial-time algorithms ($Gen, Mac, Vrfy$) such that:

1. $Gen$: takes as input $1^n$ and outputs a key $k$ with $|k| \geq n$
2. $Mac$: takes as input a key $k$ and a message $m \in \{0, 1\}^*$, and outputs a tag $t$. Since this algorithm may be randomized, we write this as $t \leftarrow Mac_k(m)$.
3. $Vrfy$: takes as input a key $k$, a message $m$ and a tag $t$. It outputs a bit $b = 1$ meaning valid and $b = 0$ meaning invalid. Is deterministic, so we write $b := Vrfy_k(m,t)$

## Security of MACs

A secure MAC is said to be *existentially unforgeable under an adaptive chosen-message attack*. "Existentially unforgeable" refers to the fact that the adversary is unable to forge a valid tag on any message; this should hold even if the attacker can carry out an "adaptive chosen-message attack" by which it is able to obtain tags on arbitrary messages chosen adaptively during its attack.

### Replay attacks

The above definition offer **no protection against replay attacks** in which an attacker simply re-sends a previously authenticated message along with its valid tag. A example would be a authenticated transfer of $1000 from Alice to Bob wich can be repeated.
A MAC by itself cannot protect against such attacks since **verification is stateless**.
To prevent replay attacks, we can use **sequence numbers** or **time-stamps**.

### Strong unforgeability

It may be possible for an adversary to generate a *different* valid tag on some *previously* authenticated message. In standard applications of MACs, this is not a concern. Nevertheless, in some settings it is useful to consider a stronger definition of security for MACs.
This definition is called a **strongly secure** MAC.

### MAC verification

MAC verification should use *time-independent* string comparison that always **compares all bytes**

## Constructing Secure MACs with pseudorandom function

### A Fixed Length MAC

- Let $F$ be a (length preserving) pseudorandom function. Define a fixed-length MAC for messages of length $n$ as follows:
	- $Mac$: input a key $k$ and message $m$, output the tag $t := F_k(m)$
	- $Vrfy$: input a key $k$, a message $m$ and a tag $t$, output 1 iff $t \stackrel{?}{=} F_k(m)$

### Domain Extension for MACs

- how MAC handling arbitrary-length messages from any fixed-length MAC

![[mac_arbitrary_length.png]]

---
links: [[themes/106 AC1 TOC - Random Oracle & Applications|AC1 TOC - Random Oracle & Applications]] - [[300 Modern Cryptography MOC|Modern Cryptography MOC]] - [[themes/000 Index|Index]]