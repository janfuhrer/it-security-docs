tags: #AC2

# Diffie-Hellman

links: [[201 AC2 TOC - Intro Public Key Encryption|AC2 TOC - Intro Public Key Encryption]] - [[themes/000 Index|Index]]

---

The Diffie-Hellman key exchange, invented in 1976 by W. Diffie and M. Hellman (and R. Merkle), was the first practical solution to the key exchange problem.

## One-Way Function

The Diffie-Hellman key exchange is based on the following one-way function, where $p$ (large prime, usually 2048 or 4096 bit) and $g$ (primitive root modulo $p$, see [[202 AC2 TOC - Modular Arithmetic and Group Theory|Modular Arithmetic and Group Theory]]) are public parameter.

- Exponentiation (easy):

$$y:= f(x) = g^x \mod p$$

- Discrete logarithm (hard): 

$$x := f^{-1}(y) = \log_g y \mod p $$
### Example

![[Diffie-Hellman Key Exchange.png]]

A simple numeric Example:

-  Let $p = 13$ and $g=2$ 
- Alice...
	- picks random a $\leftarrow$ 4  
	- computes $A:=2^4 \mod 13 = 3$ 
	- sends $A=3$ to Bob
- Bob...
	- picks random b $\leftarrow$ 2  
	- computes $B := 2^2 \mod 13 = 4$
	- sends $B=4$ to Alice
- Alice computes $k := 4^4 \mod 13 = 9$
- Bob computes $k := 3^2 \mod 13 = 9$

## Passive Attack

For an eavesdropper to break a Diffie-Hellman key exchange, one of two (supposedly hard) problems must be solved:

- Discrete Logarithm (DL): compute $a$ from $A=g^a \mod p$
- Computational Diffie-Hellman (CDH): compute $k = g^{ab} \mod p$ from $A = g^a \mod p$ and $B = g^b \mod p$

It is an open question whether DL is harder than or equal to CDH. However, it is strongly believed that no algorithm can solve DL (and hence CDH) in polynomial time, but there is no proof.

The CDH assumption is stronger than the DL assumption.

- $a := DL-Solver(A)$
- $b := DL-Solver(B)$
- $k := CDH-Solver(A,B) \rightarrow$ get solution directly without solving the discrete algorithm

## Active Attack

![[Diffie-Hellman active attack.png]]

## Application Modes

There are 3 application modes for DH:

- Ephemeral-ephemeral mode
	- Both Alice and Bob generate new values for each communication so every time they communicate a new session key $k$ is genereted
- Ephemeral-static mode
	- Only one of the two generates new values for each communication.
	- There will bi also a new session key $k$ for every communication
- Static-static mode
	- Both retain their values over multiple communications
	- They always use the same key $k$ 

## In Practice

Standardised in:

- [[PKCS|PKCS#3]]
- RFC2631 ([[003 Organisations|IETF]])
- [[003 Organisations|NIST]] Special Publication 800-56A (Revision 2)

Applications in crypto protocols:

- SSH (Secure shell)
- TLS (Transport Layer Security), formerly known as SSL (Secure Sockets Layer)
- IPSec (Internet Protocol Security)

---
links: [[201 AC2 TOC - Intro Public Key Encryption|AC2 TOC - Intro Public Key Encryption]] - [[themes/000 Index|Index]]