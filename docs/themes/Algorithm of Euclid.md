tags: #AC2 #asymmetric #math 

# Algorithm of Euclid

links: [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[themes/000 Index|Index]]

---

## Algorithm of Euclid

![[Euclid.png]]

- maximal iterations are the number of bits of $n$

## Extended Algorithm of Euclid

![[Extended-Euclid.png]]

### Bézout's Lemma Use Cases

**Solving Linear Diophantine Equations**

These are equations of the form $ax + by = c$, where $a$, $b$, $c$ are given integers, and $x$, $y$ are unknown integers. Bézout's Lemma tells us that a solution exists if and only if the greatest common divisor (gcd) of $a$ and $b$ divides $c$. Furthermore, once one solution is found, all other solutions can be expressed in terms of it.

**Finding Inverses Modulo n**

In the context of modular arithmetic, Bézout's Lemma can be used to find [[Multiplicative Inverse|multiplicative inverses]]. The multiplicative inverse of a modulo $n$ is a number $x$ such that $(a*x) \mod n = 1$. This is important in cryptographic algorithms, such as the [[RSA]] algorithm, which rely on the existence and calculation of such inverses.

---
links: [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[themes/000 Index|Index]]