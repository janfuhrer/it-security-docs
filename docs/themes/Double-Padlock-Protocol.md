tags: #AC1 #symmetric

# Double-Padlock-Protocol

links: [[103 AC1 TOC - Randomness|AC1 TOC - Randomness]] - [[themes/000 Index|Index]]

---

The idealised Kish-Sethuraman (KS) cipher is theoretically known to offer perfect security through
a classical information channel. However, realisation of the protocol is hitherto an open problem,
as the required mathematical operators have not been identified in the previous literature.

**Security Assumptions**

* Users' private keys are kept secret
* Perfect security

Schematically the protocol would work like this: 

![[Double_Padlock.png]]

## Building it with a One Time Pad

Does not work sadly. We leak information because of the OTP reuse.

![[Double_Padlock_Broken.png]]

Maybe this could somehow be achieved through quantum physics^^

With the Kish‐Sethuraman (KS) cipher an attempt was made, by using special operators and communication, to reach absolutely secure classical communication. First the message is bounced back with additional encryption by the Receiver and then the original encryption is removed and the message is resent by the Sender. The mechanical analogy of this operation is using two padlocks; one by the Sender and one by the Receiver. Klappenecker has pointed out that finding an efficient software realisation of the operators is equivalent of proving the _P ≠ NP_ problem (see [[Complexity Classes]]).

---
links: [[103 AC1 TOC - Randomness|AC1 TOC - Randomness]] - [[themes/000 Index|Index]]