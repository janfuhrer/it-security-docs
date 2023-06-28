tags: #symmetric #ascon #aead #sponge-construction

# Ascon

links:  [[107 AC1 TOC - AEAD|AC1 TOC - AEAD]] - [[themes/000 Index|Index]]

---

Ascon was Submitted on May 31, 2021 to NIST. It provides authenticated encryption wit associated data (AEAD) and hashing functionality. For full information see the [NIST Submission](https://ascon.iaik.tugraz.at/files/asconv12-nist.pdf)

## Functions

The Ascon suite consists of:

**Authenticated Cyphers:**

- Ascon-128
- Ascon-128a
- Ascon-80pq

**Hash Functions:**

- Ascon-Hash
- Ascon-Hasha

**Extendable Output Functions (XOF):**

- Ascon-XOF
- Ascon-XOFa

## Definition

In this section the several parts of Ascon will be described briefly for a visualization see the images down below. For the full explanation see the [NIST Submission](https://ascon.iaik.tugraz.at/files/asconv12-nist.pdf)

### Initialization

The initial state of Ascon is 320 bits. It is formed by the secret key, the nonce $N$ and an $IV$ initializing the algorithm (including the key size $k$, the rate $r$, the initialization and finalization round number $a$ and the intermediate round number $b$).

During the initialization $a$ rounds of $P$ (permutation / transformation) are applied. Followed by an XOR of the secret key $K$.

### Associated Data

Ascon appends a single $1$ and the smallest number of $0$'s to $A$ to make it a multiple of $r$ bits. $A$ is then divided into blocks of $r$ bits.

Each block $A_i$ is XORed with the first $r$ bits of $S_R$ of the state $S$. Then a $b$-round permutation $p^b$ is applied to $S$.

### Plaintext

**Encryption**

As with the associated data, the plaintext is padded to a multiple of $r$ bits and then divided into blocks of size $r$.

Each iteration on the plaintext block $P_i$ is XORed with the first $r$ bits of $S_r$. Then a ciphertext block $C_i$ is extracted. After the initial state $S$ is transformed by the permutation $p^b$ using $b$ rounds.

**Decryption**

The plaintext block $P_i$ is computed by XORing $C_i$ with the first $r$ bits of $S_r$. Then the first $r$ bits of $S$ are replaced by $C_i$. Finally, $S$ is transformed using the $b$-round permutation $p^b$.

### Finalization

The secret key $K$ is XOR'ed with $S$ and $S$ is transformed by the permutation $p^a$ using a round. The tag $T$ consists of the last 128 bits of $S$ XORed with the last 128 bits of $K$.

The encryption returns $T$ with the ciphertext.
Decryption returns the plaintext if the computed tag value matches $T$.

![[Ascon_operation.png]]

![[Ascon_notion.png]]

---
links:  [[107 AC1 TOC - AEAD|AC1 TOC - AEAD]] - [[themes/000 Index|Index]]