tags: #AC1 #symmetric #StreamCipher #Keccak #SHA-3

# Sponge Construction

links: [[105 AC1 TOC - Private Key Encryption|AC1 TOC - Private Key Encryption]] - [[themes/000 Index|Index]]

---

The sponge construction is a quite novel approach to design cryptographic ciphers. One can think of a sponge which absorbs water when put into water and releases the water when squeezed. This concept is used in the sponge construction. In the first phase the ciphers absorbs information (takes input). In the second phase one can squeeze out output (generates output).

![](sponge_construction.png)

### Algorithms / Building Blocks

#### Constants

The sponge construction possesses four constants which define the sizing of an implementation:
 - $r$ defines the number of bits which are absorbed per absorb cycle.
 - $c$ defines the number of 'shuffle'-bits.
 - $l$ defines the sum $r + c$ and represents the size of the sponges internal state.
 - $v$ defines the number of bits which are squeezed per squeeze cycle.

#### Unkeyed, random Permutation

The most important internal is an unkeyed, random permutation. This permutation is fixed and doesn't change (can be hardcoded and be public #Kerckhoff principle).

#### Padding

If the input to be hashed does not have the minimal length of $r$ bits, the input must be padded.

#### Absorb

In the absorbing phase, we

#### Squeeze

In the squeeze phase, we can take out $v$ bits from the current state before the permutation $P$ is executed again.

### Case-Study

#### Scenario

Suppose we have following configuration (the permutation does not fulfill the requirements of a real implementation):

- $r = 4$
- $c = 4$
- $l = r + c =  4 + 4 = 8$
- $v = 3$
- $P(x) =  {x} \lor {0000 0000}$

Now we want to create a hash of length 12 bit and are given binary $input = 1001 0010$ (146).

#### Initialization

Initially, the sponge construction is initialized to zero. This means the initial state is just a bit-string consisting of only zeros. One can seed the sponge construction by doing an absorbing phase prior to the normal absorbing phase. 

#### Absorbing Phase

First cut the input in parts of length $r$. If the last block is to short apply a the padding. In our scenario this is not necessary because ${len(input) \over r} = {8 \over 4} = 2$ and therefore fits perfect without rest:

1. absorb first $r$ bits (LSB): $m_1 = 0010$ 
2. update state by XOR $m_1$ and first r bits of the state: $0010 \lor 0000 = 0010$
3. apply $P(state)$  = $0010 0000 \lor 00000000$ = $0010 0000$
4. absorb second $r$ bits (LSB): $m_2 = 1001$
2. update state by XOR $m_2$ and first r bits of the state: $1001 \lor 0010 = 1011$
5. apply $P(state) = 10110000 \lor 00000000 = 10110000$

At the end of the absorbing phase the sponge construction has $state = 10110000$

#### Squeezing Phase

Now that the absorbing phase is finished, we can squeeze  until we got enough bits for our needs. We want 12 bits. In our scenario we squeeze 3 bits per squeeze cycle. This means we must squeeze 4 times to gather 12 bits:

1. squeeze: take first $v$ bits (MSB) of current state: $o_1 = 1011$
2. apply $P(state) = 10110000 \lor 00000000 = 10110000$ 
3. squeeze: take first $v$ bits (MSB) of current state: $o_2 = 1011$ 
4. apply $P(state) = 10110000 \lor 00000000 = 10110000$
5. squeeze: take first $v$ bits (MSB) of current state: $o_3 = 1011$ 
6. apply $P(state) = 10110000 \lor 00000000 = 10110000$
7. squeeze: take first $v$ bits (MSB) of current state: $o_4 = 1011$ 
8. apply $P(state) = 10110000 \lor 00000000 = 10110000$

Appending the results of the squeeze cycles to one another results in $1011 1011 1011 1011$ which represents the result.

### Building Ciphers with Keccak

* Generating a One Time Pad for the required message length. This gives us as a possibility to build a Stream-Cipher. We just continue to squeeze more bits out of the XOF if needed.
* Keccak can also be used for a Block-Cipher. Ascon-128 is such a cipher.
	1. Absorb-Phase: Add the key and a counter
	2. Squeeze-Phase: Take out the length of one block

---
links: [[105 AC1 TOC - Private Key Encryption|AC1 TOC - Private Key Encryption]] - [[themes/000 Index|Index]]