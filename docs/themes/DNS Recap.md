tags: #recap #DNS #networking #name-system #for-dummies

# DNS Recap

links: [[211 AC2 TOC - DPKI|AC2 TOC DPKI]] - [[themes/000 Index|Index]]

---

## What?
The DNS (Domain Name System) translates human readable domain names like `www.bfh.ch` to IP addresses like `127.0.0.1`. The IP addresses can then be routed by routing protocols and finally be resolved to physical MAC address using ARP.

## How?
The DNS has a strong hierarchy starting at the root domain `'.'` , followed by so called TLD (Top Level Domains, like `'ch'` or `'com'`). The hierarchy is a tree and each node forms its one **namespace**. All `'ch'` domains can be found within the `'.ch'` namespace. For example the domain of the BFH is located at `'.ch.bfh'` and forms the namespace for all subdomains of `'bfh.ch'`. Any node is addressed using his FQDN (Fully Qualified Domain Name). The namespace of the BFH can therefore be resolved by the FQDN `'bfh.ch.'`. Each namespace forms also a **zone**. The zones are the domain of the namespace and all its sub-domains. This means that for example the subdomains `'ti.bfh.ch'` or `ahb.bfh.ch` are part of the zone `'bfh.ch'`. 

![[dns_fqdn.png]]

## Resource Records (RR)
DNS entries follow a specific form specified in the [RFC-1035](https://www.rfc-editor.org/rfc/rfc1035.txt) (which is part of Internet Standard [STD 13](https://www.rfc-editor.org/std/std13.txt)). They are called resource records and specify following fields per entry

- NAME: The human readable domain `www.bfh.ch`
- TYPE: The type of the RR (RR can be of various types like `A` for IPV4-addresses, `MX` for mail exchanges, `SOA` for zone of authority, `AAAA` for IPV6-addresses and many more -> see section 3.2.2 of [RFC-1035](https://www.rfc-editor.org/rfc/rfc1035.txt))
- CLASS: Network class of the RR (mostly IN for Internet)
- TTL: How long shall the RR live in caches.
- RDLENGTH: Length of the RDATA
- RDATA: detailed information defining the RR

## Reverse lookup
DNS also supports reverse lookups. This means, that for a given address a human readable domain can be looked up. For this purpose also RR must be created in the DNS config which map addresses to domains. Then you can do a normal lookup.