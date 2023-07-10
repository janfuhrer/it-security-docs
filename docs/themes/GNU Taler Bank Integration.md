tags: #asymmetric 

# GNU Taler Bank Integration

links: [[212 AC2 TOC - GNU Taler|AC2 TOC GNU Taler]] - [[themes/000 Index|Index]]

---

...as a bank

1. Create an escrow bank account for the exchange with EBICS access    
2. Provision offline signing machine (or account during testing)
3. Provision two PostgreSQL databases (for LibEuFin Nexus and exchange)
4. Provision user-facing exchange service and secmod processes
5. Provision LibEuFin Nexus (connected to escrow account and providing an internal API to the exchange)
6. Test using the “taler-wallet-cli“


* LibEuFin Nexus: Free software tooling for European FinTech
* EBICS: Electronic Banking Internet Communication Standard


The Taler exchange needs to communicate with the core banking system ...

* to query for transactions into the exchange’s escrow account
* to initiate payments of aggregated Taler deposits to merchants

---
links: [[212 AC2 TOC - GNU Taler|AC2 TOC GNU Taler]] - [[themes/000 Index|Index]]