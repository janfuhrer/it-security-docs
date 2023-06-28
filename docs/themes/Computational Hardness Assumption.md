tags: #AC2 #asymmetric #math 

# Computational Hardness Assumption

links:  [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[themes/000 Index|Index]]

---

## One-Way Functions

![[One-Way-Functions.png]]

## Hardness Assumption

![[Hardness-Assumption.png]]

## The Factoring and RSA Assumptions

![[Factoring-RSA-Assumptions.png]]

*GPT*
- In the RSA cryptosystem, `e` and `d` are chosen such that they are coprime to `phi(n)`. They are exponents used for encryption and decryption, respectively, and are not required to be coprime to `n`. Their being coprime to `phi(n)` ensures they are multiplicative inverses of each other modulo `phi(n)`, which is a requirement for RSA to function correctly (`e * d ≡ 1 (mod phi(n))`).

![[RSA-Proof.png]]

- The message `m` in RSA encryption and decryption is an element of $Z_n$, the set of all integers modulo `n`. It is not required to be an element of $Z_n^*$ (the set of integers coprime to `n`), because the RSA processes involve exponentiation modulo `n` (not multiplication), and these operations don't require `m` to have a multiplicative inverse modulo `n`.

- However, in practice, it can be beneficial for security reasons to ensure that `m` is coprime to `n`, particularly when `m` contains sensitive information.


## Discrete Logarithm Assumptions

![[Discrete-Logarithm-Assumption.png]]

**Suitable Groups for DL, CDH, DDH**
![[Suitable-Groups-Discrete-Log.png]]


## Reductions Among Computational Problems

![[Reduction-Among-Computational-Problems.png]]

*GPT*
While these problems are related in the sense that they all involve operations in cyclic groups and are used in public-key cryptography, they are not completely dependent on each other. For example, even if a fast factoring algorithm were discovered (which would break RSA), the DL problem would still be considered hard unless a fast algorithm for computing discrete logarithms were also discovered. Conversely, a solution to the DL problem wouldn't necessarily provide a solution to the FACTORING or RSA problems.

**RSA $\propto$ FACTORING**

![[RSA<Factoring.png]]

**DDH $\propto$ CDH $\propto$ DL**

![[DDH<CDH<DL.png]]

---

links:  [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[themes/000 Index|Index]]