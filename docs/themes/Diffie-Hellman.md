tags: #AC2

# Diffie-Hellman

links:  [[201 AC2 TOC - Intro Public Key Encryption|TOC - Intro Public Key Encryption]] - [[themes/000 Index|Index]]

---

The Diffie-Hellman key exchange, invented in 1976 by W. Diffie and M. Hellman (and R. Merkle), was the first practical solution to the key exchange problem.

## One-Way Function

The Diffie-Hellman key exchange is based on the following one-way function, where $p$ (large prime) and $g$ (primitive root modulo $p$, see [[themes/Topic 2 - Maths|Modular Arithmetic and Group Theory]]) are public parameter.

- Exponentiation (easy):

$$y:= f(x) = g^x \mod p$$

- Discrete logarithm (hard): 

$$x := f^{-1}(y) = \log_g y \mod p $$
### Example

![[Diffie-Hellman Key Exchange.png]]

A simple numeric Example:

-  Let $p = 13$ and $g=2$ 
- Alice...
	- picks random a ← 4  
	- computes $A:=24 \mod13=3$ 
	- sends $A=3$ to Bob
- Bob...
	- picks random b ← 2  
	- computes $B:=22 \mod 13 = 4$
	- sends $B=4$ to Alice
- Alice computes $k:=44 \mod 13 = 9$
- Bob computes $k:=32 \mod 13 = 9$

## Passive Attack

For an eavesdropper to break a Diffie-Hellman key exchange, one of two (supposedly hard) problems must be solved

- Discrete Logarithm (DL): compute $a$ from $A=g^a \mod p$
- Computational Diffie-Hellman (CDH): compute $k = g^{ab} \mod p$ from $A = g^a \mod p$ and $B = g^b \mod p$

It is an open question whether DL is harder than or equal to CDH. However, it is strongly believed that no algorithm can solve DL (and hence CDH) in polynomial time, but there is no proof.

The CDH assumption is stronger than the DL assumption.

## Active Attack

![[Diffie-Hellman active attack.png]]

## Application Modes

There are 3 application modes

- Ephemeral-ephemeral mode
	- Both Alice and Bob generate new values for each communication so every time they communicate a new session key $k$ is genereted
- Ephemeral-static mode
	- Only one of the two generates new values for each communication.
	- There will bi also a new session key $k$ for every communication
- Static-static mode
	- Both retain their values over multiple communications
	- They always use the same key $k$ 

## In Practice

Standardised:

- PKCS#3
- RFC2631
- NIST Special Publication 800-56A (Revision 2)

Applications in crypto protocols:

- SSH (Secure shell)
- TLS (Transport Layer Security), formerly known as SSL (Secure Sockets Layer)
- IPSec (Internet Protocol Security)

---

links:  [[201 AC2 TOC - Intro Public Key Encryption|TOC - Intro Public Key Encryption]] - [[themes/000 Index|Index]]