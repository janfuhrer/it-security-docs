tags: #AC2 #asymmetric #math

# Generating Random Group Elements and Generators

links:  [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[themes/000 Index|Index]]

---

## Generating Random Bit Strings

$randBits(k)$ generates a random bit string of length k picked uniformly at random from the set $\{0, 1\}^k$ (set of all strings of length $k$ which can be formed from 0 and 1)

We write $r \leftarrow randBits(k)$ to denote the integer $r= \displaystyle\sum_{i=0}^{k-1}(r_i * 2^i \in\{0,...,2^k-1\})$

## Generating Random Elements of $Z_n$

![[Generating-Random-Elements-Of-Zn.png]]

- $Z_n$ = additive group of integers modulo n
- $randBits(k) \mod n$ is not a proper solution because this would cause some numbers to be more likely to appear than others. 


## Generating Random Elements of $Z_{ub} \textbackslash Z_{lb}$

![[Generating-Random-Elements-Of-Zub-Zlb.png]]


## Generating Random Elements of $Z_n^*$

![[Generating-Random-Elements-Of-ZnStar.png]]

- $Z_n^*$ = multiplicative group of integers modulo n and set of numbers coprime with n
- $r$ can only be part of $Z_n^*$ if it is coprime to $n$ ($gcd(r,n) = 1$). Every element of the group needs to have a multiplicative inverse $b \in Z_n^*$ such that $(a*b) \mod n = 1$. Being coprime to $n$ guarantees that the number $r$ has a multiplicative inverse modulo $n$.


## Generating Random Elements of $G_q \subset Z_p^*$

![[Generating-Random-Elements-Of-Gq-Zp.png]]

- $p$ is a safe prime if $p = 2q + 1$ where $q$ is also prime

**Quadratic residue**
A quadratic residue modulo p is a number that can be represented as a perfect square mod p. For example, if p=7, the quadratic residues are the remainders when the squares of the numbers {1, 2, ..., 6} are divided by 7.

1. 1^2 mod 7 = 1
2. 2^2 mod 7 = 4
3. 3^2 mod 7 = 2
4. 4^2 mod 7 = 2
5. 5^2 mod 7 = 4
6. 6^2 mod 7 = 1

So, the quadratic residues modulo 7 are {1, 2, 4}.


## Generating Random Group Elements

![[Generating-Random-Group-Elements.png]]

- Given $g \in G$ and $q = |G|$, $g$ is a generator of $G$ if for every element $h$ in $G$, there exists an integer $i$ such that $g^i = h$ ("modulo" the operation of the group).


## Testing for Generator

![[Testing-For-Generator.png]]

*GPT*
In a cyclic group $G$ of order $q$, an element $g$ is a generator if and only if it can generate every other element in the group via repeated application of the group operation. In the case of a multiplicative group, this means for every element $h$ in $G$, there is an integer $i$ such that $g^i = h$.

The order of an element $g$ in $G$, denoted $ord(g)$, is the smallest positive integer $i$ such that $g^i$ equals the identity element of the group (usually denoted 1 in a multiplicative group). According to Lagrange's theorem from group theory, the order of any element divides the order of the group. Therefore, if $g$ is a generator of $G$, then $ord(g) = |G| = q$.

To test whether $g$ is a generator, we can use the factorization of $q$. The prime factorization of $q$ is represented as $q = \displaystyle\prod_{i=1}^{k} p_i^{e_i}$, where $p_i$ are the distinct prime factors of $q$ and $e_i$ are their corresponding exponents.

Here's the reasoning: if $g$ is a generator of $G$, then $g^q$ should be equal to the identity element of $G$. However, that's not enough to ensure $g$ is a generator because, as per Lagrange's theorem, $g^i$ could equal the identity for any $i$ that divides $q$. Therefore, we need to check whether $g^{(q/p_i)}$ equals the identity for any prime factor $p_i$ of $q$. If it does, then $g$ is not a generator because its order is a divisor of $q$, not $q$ itself. If $g^{(q/p_i)}$ is not the identity for all prime factors $p_i$ of $q$, then $g$ is a generator of $G$.

In summary, knowing the prime factorization of $q$ is necessary to efficiently test whether a given element is a generator of a cyclic group $G$ of order $q$.

---

links:  [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[themes/000 Index|Index]]