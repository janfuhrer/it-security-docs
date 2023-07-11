tags: #asymmetric #exercise

# Anonymity - Exercises

links: [[210 AC2 TOC - Anonymity|AC2 TOC - Anonymity]] - [[themes/000 Index|Index]]

---

## Entropy Calculation Example

Suppose we have 101 suspects including Bob. Furthermore, suppose for Bob the attacker has a probability of 0.9 and for all the 100 other suspects the probability is 0.001. What is the entropy of this?

$\sum_{i=1}^{n} p_i \cdot \log_{2}\left(\frac{1}{p_i}\right)$

$100 * \frac{1}{1000} * \log_{2}(1000) + \frac{9}{10} * log_{2}(\frac{10}{9}) = 1.133$


100 suspects with probability $\frac{1}{1000}$ and 1 suspect with probability $\frac{9}{10}$.

## Explain the Dining Cryptographers Problem

You want to make sure that an entity inside a group is responsible for some action but you want, that it remains a secret who has done it. The dining cryptographers approach can make a statement, whether some entity inside the group is responsible for an action or someone outside (Mallory) did it.

Every two cryptographers establish a shared one-bit secret. Everyone then makes an XOR out of the two shared one-bit secrets and reveals the result.

- If they payed they invert the XOR
- If they didn't pay they just reveal the XOR of the shared one-bit secrets

Finally the revealed results are XORed aswell

- If the result is 1 then someone payed but this person stays anonymous (someone of the group payed / did the action)
- If the result is 0 then the NSA payed (someone who is not part of the group payed / did the action)

---
links: [[210 AC2 TOC - Anonymity|AC2 TOC - Anonymity]] - [[themes/000 Index|Index]]