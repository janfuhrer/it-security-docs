tags: #AC2 #prime #math

# Prime Numbers

links: [[202 AC2 TOC - Modular Arithmetic and Group Theory|AC2 TOC - Modular Arithmetic and Group Theory]] - [[themes/000 Index|Index]]

---

## Definition

- A prime number is a positive integer $p \gt 1$ that has no positive divisors other than $1$ and $p$
- Examples: $2, 3, 5, 7, 11, 13, 17, 19$
- Greatest known prime: $2^{82589933} -1$ (found in 2019)
- Euclid's theorem (300 BC) says that there are an infinite number of prime numbers.

**Prime counting function:** $\pi(n)$ is the number of primes smaller or equal to $n$. For example $\pi(13)=6$

**Prime number theorem:** $\pi(n) \approx \frac{n}{\ln n}$

In other words, when $n$ is large, then the probability that $n$ is prime is approximately:

$$
\frac{1}{\ln n} = \frac{\log e}{\log n}= \frac{1.44}{\log n}\approx \frac{1}{\log n}
$$

> To find a prime number of 2048 bit, we need about 2048 attempts.

## Safe prime

A prime $p$ is called safe prime, if $q = \frac{p-1}{2}$ is also prime. So $p = 2q+1$.

Examples: $5, 7, 11, 23, 47, 59, 83, ...$

---
links: [[202 AC2 TOC - Modular Arithmetic and Group Theory|AC2 TOC - Modular Arithmetic and Group Theory]] - [[themes/000 Index|Index]]