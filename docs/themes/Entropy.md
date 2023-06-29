tags: #symmetric #entropy

# Entropy

links: [[103 AC1 TOC - Randomness|AC1 TOC - Randomness]] - [[themes/000 Index|Index]]

---

## Definition

Entropy is the measure of uncertainty, or disorder in a system.

In the context of information theory, entropy is a measure of uncertainty, randomness, or disorder in a set of data. It's used to quantify the amount of information in a message (measurement of information). A message with high entropy can't be compressed well.

Entropy itself isn't something you can physically capture or contain, it's a property or characteristic of a system or dataset that you can measure or calculate.

## Shannon Entropy

Formalised theory of information entropy.

$\sum_{i=1}^{n} p_i \cdot \log_{2}\left(\frac{1}{p_i}\right)$

or written differently

$-\sum_{i=1}^{n} p_i \cdot \log_{2}({p_i})$

## Entropy sources

See [[Randomness#Sources of Randomness|Sources of Randomness]]

We can combine multiple entropy sources with XOR. Doing this the entropy can only increase (or stay the same). Decrease is not possible. This also means that if we combine different entropy sources, our entropy is at least as strong as the strongest entropy source in the sources pool.

Entropy is better when the least amount of trust is required to get it e.g. when we are closest to the source.

## Entropy calculation

[[Anonymity - Exercises#Entropy Calculation Example|Link to an example]]

---
links: [[103 AC1 TOC - Randomness|AC1 TOC - Randomness]] - [[themes/000 Index|Index]]