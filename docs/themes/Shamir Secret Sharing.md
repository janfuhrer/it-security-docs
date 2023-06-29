tags: #symmetric #private-key

# Shamir Secret Sharing

links: [[109 AC1 TOC - Secret sharing|AC1 TOC - Secret sharing]] - [[themes/000 Index|Index]]

---

Shamir's Secret Sharing (SSS) is an efficient secret sharing algorithm for distributing private information (the "secret") among a group such that the secret cannot be revealed unless a quorum of the group acts together to pool its knowledge.

## Problems

There are 3 main problems that SSS wants to address. 
Below are the 3 problems with a suggested solution:

### Availability

> If you give one person a secret key, it may get lost

=> So give it to more than one Person

### Confidentiality

> If you give many entities a secret, it may get disclosed

=> So give them only a key share!

### Scalability

> If you want k out of n entities to coordinate to recover a secret, there are 
> 
> $$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$
> 
> combinations to consider

=> Use Polynominals!

**Polynominals**

A polynominal of degree $k$ is fully determined by $k + 1$ data points 

$$(x_0,y_0), ...,(x_j,y_j),...,(x_k,y_k)$$

when given that $x_i \neq x_j$ for $i \neq j \land i,j \in 0,..,k$. (Each $x$ must be unique)

**Lagrange Interpolation**

The interpolation polynominal in the Lagrange form is:

$$L(x)= \sum_{j=0}^k y_j l_j(x)$$

Another representation (which I understand better):
$$P(x) = \sum_{j = 0}^{n} f_j(x_j) \cdot l_j(x)$$

where $l_j$ is defined as follows (called Lagranges Interpolation formula):

$$l_j(x)= \prod_{0\le m \le k,\ m \neq j} \frac{x-x_m}{x_j-x_m}=\frac{x-x_0}{x_j-x_0} \cdots \frac{x-x_{j-1}}{x_j-x_{j-1}} \frac{x-x_{j+1}}{x_j-x_{j+1}} \cdots \frac{x-x_{k}}{x_j-x_{k}}, 0 \le j \le k$$

With lagranges interpolation we can find one polynomial which conquers every point defined by a set of tuples $S := \{i \in 0,..,n: (x_i, f_i)\}$ (where $f_i$ is some polynomial itself). It's only possible if every $x \in S$ is unique within the set.

**Case Study**

Say we have following polynomials:
$$ f_0(x) = 0, f_1(x) = x^2, f_2(x) = x^3$$ 
Say we are given following set based on the polynomials above:
$$S := { (1, f_0(1) = 1), (2, f_1(2) = 4), (3, f_2(3) = 9) } $$

We now can create one resulting polynomial by applying the Lagranges Interpolation formula ($n = \vert S \vert = 3$):
$$P(x) = 1 \cdot l_1(x) + 4 \cdot l_2(x) + 9 \cdot l_3(x)$$

We could also substitute $l_1, l_2, l_3$ with the respective terms of the Lagrange Interpolation formula and we would see that we have a deterministic polynomial. If the resulting polynomial is our key we could share the different polynomial among people and if we needed to recover the key we would just apply the formula of Lagrange and our key could be recovered.

Source: [de: Wikipedia](https://de.wikipedia.org/wiki/Polynominterpolation)

**Practical Considerations**

> Our secrets will typically be Integers. Calculations with floating points could get messy

=> Use finite field arithmetic, not $\mathbb{R}$

**Real world scalability**

![[shamir_scalability_table.png]]

Other values:

- $\binom{10}{5} = 252$
- $\binom{20}{10} = 184756$
- $\binom{30}{15} = 155117520$
- $\binom{100}{50}\approx 10^{29}$

> How many people do you have to share your secrets with?

> How many people realistically participate in recovery?

---
links:[[109 AC1 TOC - Secret sharing|AC1 TOC - Secret sharing]] - [[themes/000 Index|Index]]