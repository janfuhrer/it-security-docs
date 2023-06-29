tags: #AC2 #asymmetric #math 

# Complexity Classes

links:  [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[themes/000 Index|Index]]

---

The following classes can be applied to **time** based complexity as well as **space** based complexity. In practical computing polynomial complexity $\mathcal{O}(n^k)$ is the limit of what we can calculate. Everything more complex than this is a hard problem.

## Polynomial (P)

P is the class that represents the set of all decision problems that can be solved in polynomial time. Meaning a complexity below or equal to $\mathcal{O}(n^k)$.

## Nondeterministic Polynomial (NP)

NP is the class of problems for which a solution can be verified in polynomial time - that is, efficiently - even though the solution may be hard to find.

**Examples**

- Factoring Problem (assumed)
	- One reason: NP-complete problems can have one solution, but can also have more than one solution, or no solution at all. In contrast, factoring always has exactly one solution.

## NP-Complete

The hardest problems in the class NP are called NP-complete; we don't know how to solve these problems in polynomial time. NP's hardest problems are all equally hard. If you can solve any NP-complete problem efficiently, you can solve all of them, as well as all problems in NP.

Not all _instances_ of NP-complete problems are actually hard to solve. (Because they are small or have a specific structure). Being NP-complete doesn't mean that all instances of a given problem are hard, but that as the problem size grows, many of them are. 

**Examples**

- Traveling Salesman Problem (decision version)
	- Given a length L, the task is to decide whether the graph has a tour of at most L
- Knapsack Problem (decision version)
	- Can a value of at least V be achieved without exceeding the weight W?
- Graph Colouring Problem
	- Can the graph be coloured using X or fewer colours?
- Clique Problem
- Boolean Satisfiability Problem (SAT)

## NP-Hard

We say that a problem is NP-hard when it's at least as hard as NP-complete problems.  Problems that are NP-hard do not have to be elements of NP; indeed, they may not even be decidable.

The primary difference between NP-complete and NP-hard is that NP-complete problems are in NP (i.e., a solution can be verified quickly), while NP-hard problems are not necessarily in NP. All NP-complete problems are NP-hard, but the converse is not necessarily true.

**Examples (not part of NP-complete)**

* Traveling Salesman Problem (Optimisation version)
* Knapsack Problem (Optimisation version)
* Graph Colouring Problem (Optimisation version)

## Overview

![[Complexity.png]]

## P vs. NP

This one is the most famous problem in computer science, and one of the most important outstanding questions in the mathematical sciences.

It's clear that P is a subset of NP. The open question is whether or not NP problems have deterministic polynomial time solutions. It is largely believed that they do not. So we assume: $P \neq NP$.

---
links:  [[203 AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions|AC2 TOC - Number-Theoretic Algorithms and Hardness Assumptions]] - [[themes/000 Index|Index]]