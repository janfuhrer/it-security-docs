tags: #AC2

# Intro Public Key Cryptography

links:  [[201 AC2 TOC - Intro Public Key Encryption|TOC - Intro Public Key Encryption]] - [[themes/000 Index|Index]]

---

## Limitation of Symmetric-Key Encryption

For a full intro to symmetric-key encryption visit [[Private Key Encryption|Private Key Encryption]].

### Key Distribution Problem

One of the biggest problems with symmetric key encryption is the **key distribution problem**. There are only a few possible secure channels such as

- Personal contact
- Trusted postal service (e.g. sealed or registered letters)
- Codebook (like in World War II)
- Courier (like the "red phone" between Moscow and Washington during the Cold War)

In general, secure channels are expensive and inefficient.

### Key Management Problem

In addition to the key distribution problem, there is also the **key management problem**.

In symmetric key encryption, pairwise communication between $N$ parties requires the following number of different keys:

$$keys(N) = \frac{N(N-1)}{2}$$

Examples: $keys(6) = \frac{6\cdot 5}{2}$, $keys(1000) \approx 500000$


Each of the $N$ parties needs to store $N-1$ keys, and the keys should be renewed periodically.

### Non-Repudiation

- In any communication based on symmetric key encryption, the key is known to at least two parties.
- After sending the ciphertext $c$ to Bob, Alice could deny being the author of $m$ because Bob could have created it himself.
- Using only symmetric key cryptography (encryption, MAC), non-repudiation can't be archived.
- Non-repudiation is essential for digital contracts.

---

links:  [[201 AC2 TOC - Intro Public Key Encryption|TOC - Intro Public Key Encryption]] - [[themes/000 Index|Index]]