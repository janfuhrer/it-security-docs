tags: #asymmetric 

# Elliptic Curves

links: [[206 AC2 TOC - Elliptic Curves|AC2 TOC - Elliptic Curves]] - [[themes/000 Index|Index]]

---

* An elliptic curve is a set of points $(x, y)$ satisfying the equation $y^2 = x^3 + ax + b$
* The variables $x$ and $y$ and the curve parameters $a$ and $b$ take values from a field $\mathcal{F} = (F,+,−,0,×,^{−1} ,1)$
* The special element $\mathcal{O} \in E_{a,b}(F)$ is called **point of infinity**

## Curve Point Operations

Elliptic curves have the property that a line intersecting the curve in two points has always a third intersecting point with the curve. Two special cases exist:

* $P + P$: Just draw a tangent trough point P
* $P + (-P)$: Results in a vertical line which is $\mathcal{O}$

Through those rules we get an additive group $\mathcal{G} = (E_{a,b}(F),+,-,\mathcal{O})$

Inverse of a point:

$-P \overset{\text{def}}{=} \begin{cases} \mathcal{O}, & \text{if } P = \mathcal{O}, \\ (x,-y), & \text{if } P = (x,y) \end{cases}$

## Addition of Curve Points

![[EC Add.png]]

All cases:

$P + Q \overset{\text{def}}{=} \begin{cases} \mathcal{O}, & \text{if } P = -Q, \\ P, & \text{if } Q = \mathcal{O} \\ Q, & \text{if } P = \mathcal{O} \\ -R, & \text{if } P \neq -Q \text{ and } P,Q \neq \mathcal{O}\end{cases}$

Note that a single addition of two points $P \neq Q$ requires computing 3 multiplications and 1 multiplicative inverse in $F$

## Elliptic Curves over $\mathbb{Z}_p$

If $p$ is prime, then $(\mathbb{Z}_p,+,−,0,×,−1 ,1)$ is a field.

As we are in $\mathbb{Z}_p$ now (modulo) we are always dealing with positive discrete numbers.

Hasse’s theorem provides an estimate of the number of points on an elliptic curve over a finite field:

$|E_{a,b}(\mathbb{Z}_p)| = p + 1 + ε$, for $|ε| < 2\sqrt{p}$, hence $q = |E_{a,b}(\mathbb{Z}_p)| ≈ p$

The number of points is around $p$

## Calculation

$P = (x_1,y_1), Q = (x_2,y_2)$

$m = \begin{cases} \frac{y_2-y_1}{x_2-x_1}, & \text{if } P \neq Q, \\ \frac{3x^2_1 + a}{2y_1}, & \text{if } P = Q \end{cases}$

$P + Q=(x,y)=(m^2 − x_1 − x_2, m \cdot (x_1 − x)− y_1)$

---
links: [[206 AC2 TOC - Elliptic Curves|AC2 TOC - Elliptic Curves]] - [[themes/000 Index|Index]]