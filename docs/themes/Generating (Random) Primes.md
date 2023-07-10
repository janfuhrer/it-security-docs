tags: #AC2 #asymmetric #math

# Generating (Random) Primes

links: [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[themes/000 Index|Index]]

---

## Generating Random k-Bit Primes

![[Generating-Random-k-Bit-Primes.png]]

- First number can't be 0 because it has to be at least $2^{k-1}$ and last bit is 1 to avoid even numbers

## Testing Primality (Naive Approach)

![[Testing-Primality-Naive-Approach.png]]

## Testing Primality (Probabilistic Approach)

![[Testing-Primality-Probabilistic-Approach.png]]

![[Pseudocode-isPrime.png]]

Instead of completely testing all possibilities and making sure that a number is prime, a function $isComposite()$ is used to decide that $n$ is *likely* prime. Users can decide themselves how sure they want to be if $n$ is prime by running the algorithm multiple times.

## Fermat

![[Testing-Primality-Fermat.png]]

This check is not enough because **Carmichael Numbers** would return false even though they aren't prime (should return true). Miller-Rabin algorithm solves this.

## Miller-Rabin

![[Testing-Primality-Miller-Rabin.png]]

- the Miller-Rabin primality test is most widely used in practice
- the failure probability of a single test is $\alpha \leq 0.25$

**Example**

Suppose we have an odd integer $n > 3$ that we want to test for primality, and we've chosen a random integer a in the range $[2, n-2]$.

1. Write $n-1$ as $2^r * d$, where $d$ is an odd number ($r$ must be as large as possible).
2. Compute $x = a^d \mod n$ using fast exponentiation.
3. If $x$ equals $1$ or $n-1$, then n passes the test for base $a$.
4. Otherwise, square $x$ repeatedly mod $n$ up to $r-1$ times. If, in any of these squarings, we get $n-1$, then $n$ passes the test for base $a$.
5. If we haven't found $1$ or $n-1$ by this point, then $n$ is composite, and we say that $a$ is a witness to the compositeness of $n$.

Let's consider an example. Suppose we want to check whether $n = 221$ is prime, and we choose $a = 174$.

1. We can write $220$ as $2^2 * 55$, so $r = 2$ and $d = 55$.
2. Compute $x = 174^55 \mod 221$, which equals $47$.
3. Since $x$ is not $1$ or $220$, we square $x$ to get $47^2 \mod 221 = 220$.
4. At this point, we've found $220$ (which is $n-1$), so $221$ passes the test for base $174$. Either $221$ is prime or $174$ is a strong liar for $221$

We do the same for $a = 137$

1. Compute $x = 137^{55} \mod 221$, which equals $188$.
2. Since $x$ is not $1$ or $220$, we square $x$ to get $188^2 \mod 221 = 205$.
3. We squared $x$ once ($r-1$) and have not reached $x = 1$ or $x = 220$ hence $137$ is a witness that $221$ is not prime

---
links: [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[themes/000 Index|Index]]