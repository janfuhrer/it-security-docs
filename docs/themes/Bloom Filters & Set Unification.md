tags: #AC1 

# Bloom Filters & Set Unification

links:  [[112 AC1 TOC - Key Revocation|AC1 TOC - Key Revocation]] - [[themes/000 Index|Index]]

---

## Explain efficient set union and how it can be achieved

The problem to solve is that two nodes each have a sets with small differences and they want to sync up their sets so they end up with the same combined sets.

The naive approach is that both nodes send their sets to the other nodes and they each compare the other nodes set and add whatever they are missing. This gives a communication cost of BigOh(|A| + |B|) which is not great. Instead of sending the actual set, hashes of the elements can be sent but that doesn't improve complexity. The ideal solution would complexity of BigOh(diff(A/B)).

**Bloom filters**
Take an array of 0's and the hash of the first element in the set. Flip the corresponding bits in the array. Repeat for the following elements in the set. If a bit is already flipped to 1 leave it on 1.

Send the array to the other node. The node can check its set elements by hashing them and checking if all the bits are set to 1. If they are then it is likely that all the elements are also present in the set of the sending node. If a bit of an element is not set to 1 then this element is definitely not part of the other nodes set. The probability can be adjusted through the size of the array. The larger the array the lower the chance for false positives.

![[bloom_filter_1.png]]
![[bloom_filter_2.png]]

**Counting bloom filter**
Bloom filters where buckets (array fields) hold positive integers instead of only 0 and 1. This means that elements can also be removed. This leads to the possibility of false negatives. This can happen when an element, which was not previously added, is removed from the CBF. 

The receiver of a CBF can subtract all the elements from its set and when the CBF ends up being negative, the CBF represents the elements that are missing in the other nodes set.

**Invertible Bloom Filters**
Extension of CBF. They allow negative counts are they store XOR-sums of the elements hashes in the buckets. This allows extraction of elements from the IBF and the construction of a symmetric difference.
https://www.youtube.com/watch?v=YNbcXlllOBQ

**Extraction**
1. Chose a pure bucket (bucket with count 1) and read pure hash
2. Based on hash you find out which other buckets are used
3. XOR the sum of hashes with the pure hash which removes / extract the hash from the sum. The result is the element itself information if the element is missing in my own set or in the other nodes set (don't know where this information is supposed to come from)
4. Hopefully more pure buckets will have formed to extract more elements
5. Repeat until all elements are successfully extracted (IBF should be all 0). If not, the extraction failed and the process has to be restarted with a larger IBF.

**Symmetric Difference**
The symmetric difference can be calculated out of two IBFs from two nodes. It's an XOR of the two IBFs and the result is an IBF of the elements which are missing in the other set. After having calculated the diff, extraction can be applied because it's more likely to find buckets with count 1. If there are no buckets with 1 or if other conflicts occur the size of the array can be increased.

![[ibf.png]]

The advantage of IBFs is that the size of the actual set does not matter. Only the size of the diff matters. The larger the diff the larger the IBF has to be.


## How is the size of the IBF chosen

Strata Estimator...

---
links:  [[112 AC1 TOC - Key Revocation|AC1 TOC - Key Revocation]] - [[themes/000 Index|Index]]
