tags: #AC2 #math #exercise 

# AC2 - Math - Exercise 3

links: [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[Algorithm of Euclid]] - [[Multiplicative Inverse]] - [[themes/000 Index|Index]]

---

![[exercises03.pdf]]

2. 
**Euclic(48, 174)**
174 mod 48 = 30
48 mod 30 = 18
30 mod 18 = 12
18 mod 12 = 6
12 mod ==6== = 0

**ExtEuclid(48, 174)**

| | 6 = 18 - 1(12) |
| ---------------- | --------------------------------------- |
| 12 = 30 - 1(18)  | 6 = 18 - 1(30 - 1(18)) = 2(18) - 1(30)   |
| 18 = 48 - 1(30)  | 6 = 2(48 - 1(30)) -1(30) = 2(48) - 3(30) |
| 30 = 174 - 3(48) | 6 = 2(48) - 3(174 - 3(48)) = ==-3(174) + 11(48)== |

**MultInv(48, 127)**

127 mod 48 = 31
48 mod 31 = 17
31 mod 17 = 14
17 mod 14 = 3
14 mod 3 = 2
3 mod 2 = 1
2 mod ==1== = 0

|                  | 1 = 3 -1(2)                                      |
| ---------------- | ------------------------------------------------ |
| 2 = 14 - 4(3)    | 1 = 3 - 1(14 - 4(3)) = -1(14) + 5(3)             |
| 3 = 17 - 1(14)   | 1 = -1(14) + 5(17 - 1(14)) = 5(17) - 6(14)       |
| 14 = 31 - 1(17)  | 1 = 5(17) - 6(31 - 1(17)) = -6(31) + 11(17)      |
| 17 = 48 - 1(31)  | 1 = -6(31) + 11(48 - 1(31)) = 11(48) - 17(31)    |
| 31 = 127 - 2(48) | 1 = 11(48) - 17(127 - 2(48)) = ==-17(127) + 45(48)== |

==45== * 48 mod 127 = 1

---

links: [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[Algorithm of Euclid]] - [[Multiplicative Inverse]] - [[themes/000 Index|Index]]