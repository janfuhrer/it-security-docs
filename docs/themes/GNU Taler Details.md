tags: #asymmetric 

# GNU Taler Details

links: [[212 AC2 TOC - GNU Taler|AC2 TOC GNU Taler]] - [[themes/000 Index|Index]]

---

## Withdrawing coins

![[Taler Withdraw Coins.png]]

## Payment

![[Taler Payment.png]]

## Double Spending Problem

A lot of logic is needed to ensure double spending does not happen. (Multiple keys, key rotation etc.)

Also, the exchange needs a database to detect double spending.

## Giving change

It would be inefficient to pay EUR 100 with 1 cent coins! 

* Denomination key represents value of a coin.  
* Exchange may offer various denominations for coins. 
* Wallet may not have exact change!
* Usability requires ability to pay given sufficient total funds. 

Key goals:

* maintain unlinkability
* maintain taxability of transactions    

Method:

* Contract can specify to only pay partial value of a coin.
* Exchange allows wallet to obtain unlinkable change for remaining coin value.

### Refresh protocol

[[Cut-and-choose zero-knowledge proof]] is needed here.

* Customer asks exchange to convert old coin to new coin
* Protocol ensures new coins can be recovered from old coin
	* New coins are owned by the same entity!

Thus, the refresh protocol allows:  

* To give unlinkable change.  
* To give refunds to an anonymous customer.  
* To expire old keys and migrate coins to new ones. 
* To handle protocol aborts.

---
links: [[212 AC2 TOC - GNU Taler|AC2 TOC GNU Taler]] - [[themes/000 Index|Index]]