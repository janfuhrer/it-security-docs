tags: #AC2

# Modular Arithmetic

links: [[202 AC2 TOC - Modular Arithmetic and Group Theory|AC2 TOC - Modular Arithmetic and Group Theory]] - [[themes/000 Index|Index]]

---

## Fundamental Theorem of Arithmetic

Every integer $n \gt 1$ is either a prime number itself or a product of prime numbers.

## Greatest Common Divisor

The GCD of two positive integers $a$ and $b$, is the largest positive integer $d=\gcd(a,b)$ that divides both $a$ and $b$.

### Co-prime

- Two integers $a$ and $b$ are **relatively prime** (or **co-prime**), if $gcd(a,b) = 1$.
- Two numbers can be co-prime even if only one or both of them are prime!

## Euler's Totient Function $\phi$

This is a function that counts the number of positive integers up to a given number $n$ that are co-prime to $n$. For example, $\phi(9)=6$, because there are six numbers (1,2,4,5,7,8) that are less than 9 and co-prime to 9.

## Modulo Operator

The modulo operator (sometimes written as %): $r=a\mod n$ denotes the remainder $r$ $\in$ {$0,...,n-1$} of $a$ divided by $n$
$a = qn + r$ for $q$ $\in$ $\mathbb{Z}$

### Arithmetic

Addition modulo $n$ and multiplication modulo $n$ are defined by:

$a \;+_n \; b =(a+b)\mod{n} = ((a \mod n) + (b \mod n))\mod n$

$a \;\times_n \; b =(a\cdot b)\mod{n} = ((a \mod n) \cdot (b \mod n))\mod n$

Most of the times modular addition and multiplication are only written using the standard arithmetic operators $+$ and $\cdot$

## Fermat's (Little) Theorem

Let $p$ be a prime number and $a \in \{ 1,....,p-1\}$ then 

$$a^{p-1}\equiv 1 \quad (mod\; p)$$

## Euler's Theorem

If $\gcd (a,n) =1$ for positive integers $a$ and $n$ then

$$a^{\phi(n)}\equiv 1 \;(mod \; n)$$

## Primitive Root Modulo $n$

A "primitive root modulo $n$" is a number $g$ such that for any integer $a$ that's co-prime with n, there exists an integer k such that $g^k \equiv a \;(mod \; n)$.

Examples:

- 2 is a primitive root modulo 5
	- $2^4 \mod 5 = 1$,  $2^1 \mod 5 = 2$, $2^3 \mod 5 = 3$, $2^2 \mod 5 = 4$   
- 4 is not primitive root modulo 5
	- $4^1 \mod 5 = 1$, $4^2 \mod 5 = 1$, $4^3 \mod 5 = 4$ 

## Multiplicative Inverse Modulo n

The multiplicative inverse of $a$ modulo $n$ is an integer $a^{-1}$ such that

$$
a\cdot a^{-1} \equiv 1 \; (mod \;n)
$$

The multiplicative inverse of a modulo n exists iff $gcd(a, n) = 1$

---
links: [[202 AC2 TOC - Modular Arithmetic and Group Theory|AC2 TOC - Modular Arithmetic and Group Theory]] - [[themes/000 Index|Index]]