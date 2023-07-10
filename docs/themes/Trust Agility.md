tags: #AC2 #asymmetric 

# Trust Agility

links: [[208 AC2 TOC - Centralized public-key infrastructures|AC2 TOC - Centralized public-key infrastructures]] - [[Public Key Infrastructure]] - [[themes/000 Index|Index]]

---

Alles GPT (ma nüm):
1. **What is fundamentally wrong with the current CA model?**
    
    The Certificate Authority (CA) model suffers from several challenges:
    
    - **Trustworthiness**: In the current model, if a CA is compromised, the attacker can issue fraudulent certificates for any domain, which can be used to perform man-in-the-middle attacks or impersonate websites.
        
    - **Centralization**: The CA model is highly centralized, with a relatively small number of CAs trusted by default by browsers and operating systems. This centralization creates high-value targets for attackers.
        
    - **Weak link problem**: All CAs are equally trusted in the current model. This means that even if just one CA is compromised or acts maliciously, it can undermine the security of the entire system.
        
    - **Lack of transparency and accountability**: It can be difficult for website operators to know who is issuing certificates for their domains, and fraudulent or mistakenly-issued certificates can go undetected.
        
2. **What is the idea of "trust agility", and is it reasonable?**
    
    Trust agility refers to the idea that users or organizations should be able to choose who they trust, rather than being forced to trust a pre-set list of CAs. This allows users to adapt their trust based on their needs, preferences, or the changing security landscape. For example, if a CA is found to be compromised or acting maliciously, users could quickly stop trusting that CA.
    
    The concept of trust agility is reasonable and potentially beneficial for enhancing security. It could provide more flexibility and control to end users and reduce the impact of a single CA being compromised. However, it also presents challenges. For instance, average users may not have the knowledge or skills to make informed decisions about who to trust. Therefore, implementation of trust agility would need to be carefully designed to avoid introducing new security risks.
    
3. **Understand the notion of "perspectives". Evaluate strengths and weaknesses of the perspective model.**
    
    The Perspectives model is a system designed to enhance the security of certificate validation by using a network of "Notary" servers. When a client connects to a server, it can ask the Notaries what certificate they see for that server. If the client sees the same certificate as the Notaries, it can have higher confidence that the certificate is valid, even if the certificate is not signed by a trusted CA.
    
    Strengths of the Perspectives model:
    
    - It can help detect attacks where a fraudulent certificate is presented to specific users or from specific network locations, as the Notaries can provide a broader view of what certificate is being presented across different locations and times.
        
    - It allows for trust agility, as trust decisions can be based on the Notary observations rather than a fixed list of CAs.
        
    
    Weaknesses of the Perspectives model:
    
    - It requires maintaining a network of Notaries, which can be a logistical challenge.
        
    - It only works if the Notaries see the same certificate over a period of time. If an attacker can control or influence what certificate the Notaries see, the system can be fooled.
        
    - It does not provide a way to verify the identity of a server the first time a client connects to it. The Perspectives model is about consistency of observations over time, but if a client has no previous information about a server, the Notaries cannot provide a definitive validation of the server's certificate.

---
links: [[208 AC2 TOC - Centralized public-key infrastructures|AC2 TOC - Centralized public-key infrastructures]] - [[Public Key Infrastructure]] - [[themes/000 Index|Index]]