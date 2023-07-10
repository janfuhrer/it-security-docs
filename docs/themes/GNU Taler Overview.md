tags: #asymmetric 

# GNU Taler Overview

links: [[212 AC2 TOC - GNU Taler|AC2 TOC GNU Taler]] - [[themes/000 Index|Index]]

---

> Digital cash, made socially responsible.

## Definition

Taler is

- a Free/Libre software **payment system infrastructure** project
- ... with a surrounding software ecosystem
- ... and a company (Taler Systems S.A.) and community that wants to deploy it as widely as possible.
    
However, Taler is 

- **not a currency**  
- not a long-term store of value  
- not a network or instance of a system  
- not decentralized  
- not based on proof-of-work or proof-of-stake  
- not a speculative asset / “get-rich-quick scheme”

## Design goals

GNU Taler must ...

1. ... be implemented as free software.
2. ... protect the privacy of buyers.
3. ... must enable the state to tax income and crack down on illegal business activities.
4. ... prevent payment fraud.
5. ... only disclose the minimal amount of information necessary.
6. ... be usable.
7. ... be efficient.
8. ... avoid single points of failure.
9. ... foster competition.

## Vision

- Be paid to read advertising, starting with spam 
- Give welfare without intermediaries taking huge cuts 
- Forster regional trade via regional currencies  
- Eliminate corruption by making all income visible  
- Stop the mining by making crypto-currencies useless for anything but crime

## Regulatory Features for Central Banks

- Central bank issues digital coins **equivalent to issuing cash**
- Architecture with **consumer accounts at commercial banks**
- **Withdrawal limits** and denomination expiration
- **Income transparency** and possibility to set fees
- Revocation protocols and **loss limitations**
- **Privacy by cryptographic design** not organisational compliance

### CBDC (Central Bank Digital Currency)

- Taler replicates physical cash rather than bank deposits
- Taler has unique design principles and regulatory features that align with CBDC requirements
- ECB (Euro) survey has identified privacy as a primary requirement of end users

Online vs. Offline CBDC:

1. Online-first
2. Limited offline mode (counterparty risk)
3. Physical cash for emergencies

### Taxability

We say Taler is taxable because:  

- Merchant’s income is visible from deposits. 
- Hash of contract is part of deposit data.  
- State can trace income and enforce taxation.

## Architecture

Taler consists of different components:

- Exchange (Core)
- Merchant
- Wallet

![[Taler High Level.png]]

Integrated into our banking system:

![[Taler in Detail.png]]

---
links: [[212 AC2 TOC - GNU Taler|AC2 TOC GNU Taler]] - [[themes/000 Index|Index]]