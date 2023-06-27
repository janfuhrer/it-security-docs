tags: #symmetric #private-key

# Shamir Secret Sharing

links:  [[110 AC1 TOC - Secret sharing|AC1 TOC - Secret sharing]] - [[themes/000 Index|Index]]

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

> If you want k out of n entities to coordinate to recover a secret, there are $$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$ combinations to consider

=> Use Polynominals!

**Polynominals**

A polynominal of degree k is fully determined by k + 1 data points $$(x_0,y_0), ...,(x_j,y_j),...,(x_k,y_k),$$where no two $x_j$ may be identical.

**Lagrange Interpolation**
The interpolation polynominal in the Lagrange form is:
$$L(x)= \sum_{j=0}^k y_j l_j(x)$$ where$$L_j(x)= \prod_{0\le m \le k} \frac{x-x_m}{x_j-x_m}=\frac{x-x_0}{x_j-x_0} \cdots \frac{x-x_{j-1}}{x_j-x_{j-1}} \frac{x-x_{j+1}}{x_j-x_{j+1}} \cdots \frac{x-x_{k}}{x_j-x_{k}}$$  for 0 **$\le$ j $\le$ k

**Practical Considerations**

> Our secrets will typically be Integers. Calculations with floating points could get messy

=> Use finite field arithmetic, not $\mathbb{R}$

**Real world scalability**

![[shamir_scalability_table.png]]

Other values:

- $\binom{10}{5} = 252$
- $\binom{20}{10} = 184756$
- $\binom{30}{15} = 155117520$
- $\binom{10}{5}\approx 10^{29}$

> How many people do you have to share your secrets with?

> How many people realistically participate in recovery?

---
links:  [[110 AC1 TOC - Secret sharing|AC1 TOC - Secret sharing]] - [[themes/000 Index|Index]]