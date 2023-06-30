tags: #AC2 #asymmetric #math #computability-complexity 

# Complexity Reduction

links: [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[themes/000 Index|Index]]

---

The expression "P1 $\leftarrow$ P2" refers to a reduction proof. This is a concept used to determine the difficulty of problems in relation to each other.

The statement "P1 $\leftarrow$ P2" means that problem P1 can be reduced to problem P2 in polynomial time. In other words, if we have a solution for P2, we can use that solution to solve P1 in polynomial time.

Reductions are a central concept in the theory of [[Complexity Classes#NP-Complete|NP-completeness]]. If a problem P is known to be NP-complete and every other problem Q can be reduced to P in polynomial time (i.e., Q  $\leftarrow$ P), then Q is also NP-complete.

So, we need some problem to which we can reduce to in order to prove NP-completeness. That's where the Cook-Levin theorem comes into play.

## Cook–Levin theorem

The theorem states the following:

> The Boolean satisfiability problem (also known as SAT) is NP-complete.

This was the first problem that was shown to be NP-complete. The proof does not need a reduction so we can use it as a basis for other problems.

**Boolean satisfiability problem (SAT):** This is the problem of determining if there exists an assignment of true/false values to variables that makes a given Boolean expression true.

In a bit more detail: It asks to determine if a propositional formula (syntactic formula which is well formed and has a truth value) can be made true by an appropriate assignment ("solution") of truth values to its variables. While it is easy to verify whether a given assignment renders the formula true, no essentially faster method to find a satisfying assignment is known than to try all assignments in succession. Cook and Levin proved that each easy-to-verify problem can be solved as fast as SAT, which is hence NP-complete.

### How does the proof work?

**Step 1: SAT is in NP**

First, we have to show that SAT is in NP. This is fairly straightforward: given a Boolean formula and a truth assignment for its variables, we can check in polynomial time whether the assignment makes the formula true or false. Therefore, SAT is in NP.

**Step 2: SAT is NP-Hard**

Next, we have to show that SAT is NP-hard. This is the more complex part of the proof. Essentially, it means we must demonstrate that any problem in NP can be transformed (or "reduced") into a SAT problem in polynomial time.

Stephen Cook approached this by considering a nondeterministic Turing machine. He then demonstrated how one can construct a Boolean formula that simulates a computation of this machine. This formula is satisfiable if and only if the machine accepts the given input. This transformation can be done in polynomial time, so this part of the proof shows that SAT is as hard as the hardest problems in NP, meaning it's NP-hard.

Since SAT is both in NP and NP-hard, it is NP-complete.

### Visualisation

Visualisation of reductions to prove different NP-complete problems:

![[Complexity_Reduction.png]]

---
links: [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[themes/000 Index|Index]]