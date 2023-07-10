tags: #AC2 #asymmetric #math #computability-complexity

# Complexity Notation

links: [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[themes/000 Index|Index]]

---

## Different algorithmic complexities

From fast to slow

* $\mathcal{O}(1)$ - Constant time
* $\mathcal{O}(\log n)$ - Logarithmic time
* $\mathcal{O}(\sqrt{n})$ - Square root time
* $\mathcal{O}(n)$ - Linear time
* $\mathcal{O}(n \log n)$ - Linear logarithmic time
* $\mathcal{O}(n^2)$ - Quadratic time
* $\mathcal{O}(n^3)$ - Cubic time
* $\mathcal{O}(n^k)$ - Polynomial time
* $\mathcal{O}(2^n)$ - Exponential time
* $\mathcal{O}(n!)$ - Factorial time
* $\mathcal{O}(n^n)$ - "Crazy" exponential time

From the slides:
![[Complexity_Notation.png]]

## Notation

For some function $f(n)$

* Big O notation: $\mathcal{O}(f(n))$ - Upper bound. Worst case scenario. (Less or equal)
* Little o notation: $\mathcal{o}(f(n))$ - Upper bound. Worst case scenario. (Strictly less)
* Big Omega notation: $\Omega(f(n))$ - Lower bound. Best case scenario. (Greater or equal)
* Little omega notation: $\omega(f(n))$ - Lower bound. Best case scenario. (Strictly greater)
* Big Theta notation: $\Theta(f(n))$ - Equal. Average case scenario.

## Master Theorem

To analyse recursive function we need the Master Theorem.

**Decrease (R1-2)** the problem size by $k$:

$$
T(n) = 
\begin{cases} 
	c & \text{if } n = d \\ 
	q \times T(n-k) + f(n) & \text{if } n \gt d \\ 
\end{cases}
$$

**Divide (D1-4)** the problem size by $r$:

$$
T(n) = 
\begin{cases} 
	c & \text{if } n = d \\ 
	q \times T(n/r) + f(n) & \text{if } n \gt d \\ 
\end{cases}
$$


![[Master_Theorem.png]]

---
links: [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[themes/000 Index|Index]]