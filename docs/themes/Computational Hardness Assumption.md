tags: #AC2 #asymmetric #math 

# Computational Hardness Assumption

links:  [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[RSA]]- [[themes/000 Index|Index]]

---

## One-Way Functions

![[One-Way-Functions.png]]

## Hardness Assumption

![[Hardness-Assumption.png]]

## The FACTORING and RSA Assumptions

![[Factoring-RSA-Assumptions.png]]
[[RSA|RSA Explanation]]


## Discrete Logarithm Assumptions (DL)

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

links:  [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[RSA]]- [[themes/000 Index|Index]]