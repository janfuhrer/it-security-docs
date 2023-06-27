tags: #AC1 #Randomness #symmetric #Pseudorandom
links: [[themes/000 Index|Index]],  [[100 AC1 MOC|Applied Cryptography 1]], [[103 AC1 TOC - Randomness|Randomness]]

---
## Pseudorandom Number Generator (PRNG)
A PRNG is a deterministic function which produces a bit-string of length `l` which "looks like" random. This means that there isn't a pattern to be found that could predict the next bit. While [[103 AC1 TOC - Randomness|RNG]] must guarantee randomness and be effectively random, a PRNG is allowed to create `l`-bit-strings which are *almost* random. This means that a distinguisher `D` is unable to distinguish the output of the PRNG from the true RNG with **negligible deviation** from the optimal probability. A PRNG is **deterministic** which means, that the output of a PRNG can be reproduced if you know the seed (the initialization value of the PRNG). The optimal proability is $1 \over {k_{states}}$ , where $k_{states}$ is the number of possible states a sign in the generated output-string can have (e.g. in a bit-string a sign can have to states: `1` and `0`, which results in $\mathbb{P}(s_i = 1) \approx \mathbb{P}(s_i = 0) \approx {1 \over 2}$ for each sign $s_i \in s$, $s$ a bit-string).

### Distinguisher 
To understand PRNG it is important to understand the concept of the distinguisher (as described by Lindell & Katz, p. 61). A distinguisher is a statistical test which shall return 1, given the output string of a PRNG, with the same probability as if the input to D was a uniformly distributed string of same length.

## Requirements
For a PRNG to be secure, it requires a few assumptions to be met:
- $l(n) > n$ . This means that for any security parameter `n`, the length of the output must be at least as long as the security parameter (otherwise it would mean a security downgrade, because the this would lead to shorter pads resulting in a lower security parameter.
- The probability for a bit $s_i, i \in 1,.., l(n)$  in bit-string $s$ to be 1 or 0 must be equal $1 \over 2$ with some negligible deviation $negl(n)$ which is dependent from the security parameter $n$
$$\mathbb{P}(s_i = 1) \approx \mathbb{P}(s_i = 0) \approx  {1 \over 2} + negl(n)$$
- If using a PRNG for security purposes, the **seed of the PRNG must be kept secret**, otherwise it's easy to recreate the random bit-strings.

#### Construct PRG from PRF


#### Sub-Key derivation

---
links: [[themes/000 Index|Index]],  [[100 AC1 MOC|Applied Cryptography 1]], [[103 AC1 TOC - Randomness|Randomness]]