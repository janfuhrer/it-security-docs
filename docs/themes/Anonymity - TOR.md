tags: #asymmetric

# TOR

links: [[210 AC2 TOC - Anonymity|AC2 TOC - Anonymity]] - [[themes/000 Index|Index]]

---

Tor is a P2P network of **low-latency** mixes which are used to provide anonymous communication between parties on the Internet. It works for any TCP-based protocol and traffic enters the network via SOCKS proxy. Commonly used for anonym web browsing.

## Onion Routing

- Multiple mix servers
- Path of mx servers chosen by initiator
- Chosen mix servers create "circuit" (see following example)

**Example**

- Client choses which mix servers he wants to use for communication
- Set up symmetric key $K_{S_1}$ with first mix server
- Through first mix server set up symmetric key $K_{S_2}$ with second mix server
- Repeat until user has a key for every mix server
- Encrypt message with all symmetric keys $(K_{S_1}(K_{S_2}(m)))$ and send message to first mix server
- First mix server decrypts the message and sends the message to the next mix server until destination is reached.

![[tor_routing_1.png]]

Just like in [[Anonymity - Mixing#Mixminion|Mixminion]], there are directory servers which keep track of contact information, public keys and statistics. Clients use directory servers to chose servers randomly with bias towards bandwidth/ uptime. Circuits are **bi-directional** and of **length three**.

![[tor_routing_2.png]]

In the example above:

- Tor Node 1 is the **Entry node / Guard**
	- Generally long lived "good" nodes
	- Client (User) has to trust this node since it directly communicates with it
- Tor Node 5 is the **Relay / Middle node**
- Tor Node 8 is the **Exit node**
	- Visible to outside destination
	- Most vulnerable node in circuit / route
	- Supports filtering of outgoing traffic

## Hidden Services in Tor

> Services inside the tor network which are **only** available from inside the tor network. They allow tor servers to receive incoming connections **anonymously**.

1. **Service Setup**: The hidden service picks some introduction points and builds circuits to them. Then the service advertises his service (as a `.onion` address) at the DB ([[DHT]])
2. **Client Request**: When a client wants to connect to a hidden service, it loads the `.onion` address into a Tor-enabled client (like the Tor browser). This address corresponds to the public key of the hidden service. The client uses this key to check the [[DHT]] and retrieve the descriptor, which contains the introduction points and the service's public key.
3. **Introduction Points Connection**: After obtaining the introduction points and the service's public key, the client randomly picks a relay in the network to act as a rendezvous point and communicates it to the hidden service via one of the introduction points.
4. **Rendezvous Point**: The client builds a circuit to the rendezvous point and sends a rendezvous message there. The rendezvous point holds this message until the hidden service connects.
5. **Circuit Building**: In the meantime, the hidden service builds a circuit to the rendezvous point and sends a rendezvous message, which makes the rendezvous point connect the two circuits.
6. **Hidden Service Connection**: Now, the client and the hidden service are connected through Tor circuits and can communicate privately. The rendezvous point simply relays (end-to-end encrypted) messages from client to service and vice versa. It does not know the client's IP or the hidden service's IP. It also can't read the content of the messages because they are end-to-end encrypted between the client and the service.

![[hidden-service-tor.png]]

## Attacks on Tor

- Exit Relay Snooping (not encrypted traffic, e.g. http)
- Website fingerprinting (monitor entry node to analyse which sites are being visited, only metadata through encryption)
- Traffic Analysis (stuttering while packet send to identify exit point)
- Intersection Attack (e.g. disable internet, see if attack stops)
- DoS (circle in path, e.g. 10'000 hops)

---
links: [[210 AC2 TOC - Anonymity|AC2 TOC - Anonymity]] - [[themes/000 Index|Index]]