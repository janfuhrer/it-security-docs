tags: #AC2 #asymmetric #math 

# Computational Hardness Assumption

links: [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[RSA]] - [[themes/000 Index|Index]]

---

## One-Way Functions

![[One-Way-Functions.png]]

## Hardness Assumption

![[Hardness-Assumption.png]]

## The FACTORING and RSA Assumptions

![[Factoring-RSA-Assumptions.png]]

see [[RSA|RSA]]

## Discrete Logarithm Assumptions (DL)

![[Discrete-Logarithm-Assumption.png]]

- **CDH**: computational $\rightarrow$ calculate key
- **DDH**: decisional $\rightarrow$ returns true/false

**Suitable Groups for DL, CDH, DDH**

![[Suitable-Groups-Discrete-Log.png]]

- DL can be solved easily in an *additive group* using the [[Algorithm of Euclid]].

## Reductions Among Computational Problems

![[Reduction-Among-Computational-Problems.png]]

While these problems are related in the sense that they all involve operations in cyclic groups and are used in public-key cryptography, they are not completely dependent on each other. For example, even if a fast factoring algorithm were discovered (which would break RSA), the DL problem would still be considered hard unless a fast algorithm for computing discrete logarithms were also discovered. Conversely, a solution to the DL problem wouldn't necessarily provide a solution to the FACTORING or RSA problems.

**RSA $\propto$ FACTORING**

![[RSA_FACTORING.png]]

- [[RSA]] is the stronger assumption (as the simpler problem)

**DDH $\propto$ CDH $\propto$ DL**

![[DDH_CDH_DL.png]]

- Solving DL allows to solve CDH
- Solving CDH allows to solve DDH

---
links: [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[RSA]] - [[themes/000 Index|Index]]