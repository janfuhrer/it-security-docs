tags: #asymmetric 
links:  [[210 AC2 TOC - Anonymity]], [[themes/000 Index|Index]]

---
# TOR

## What is tor

P2P network of low-latency mixes which are used to provide anonymous communication between parties on the Internet. It works for any TCP-based protocol and traffic enters the network via SOCKS proxy. Commonly used for anonym web browsing.


## How does onion routing work?

- Client choses which mix servers he wants to use for comunication
- Set up symmetric key $K_{S_1}$ with first mix server
- Through first mix server set up symmetric key $K_{S_2}$ with second mix server
- Repeat until user has a key for every mix server
- Encrypt message with all symmetric keys $(K_{S_1}(K_{S_2}(m)))$ and send message to first mix server
- First mix server decrypts the message and sends the message to the next mix server until destination is reached.
![[tor_routing_1.png]]

Just like in [[Anonymity - Mixing#What is Mixminion?|mixminion]], there are directory servers which keep track of contact information, public keys and statistics. Clients use directory servers to chose servers based on bandwidth and update. Circuits / Routes are of length three. 
![[tor_routing_2.png]]

In the example above
- Tor Node 1 is the **Entry node / Guard**
	- Generally long lived "good" nodes
	- Client (User) has to trust this node since it directly communicates with it
- Tor Node 5 is the **Relay / Middle node**
- Tor Node 8 is the **Exit node**
	- Visible to outside destination
	- Most vulnerable node in circuit / route
	- Supports filtering of outgoing traffic


## What are hidden services and how do they work?

Services inside the tor network which are only available from inside the tor network. They allow tor servers to receive incoming connections anonymously.

Slides page 51

1. **Service Setup**: The hidden service picks some random relay nodes in the Tor network, sets them up as introduction points, and builds circuits to them. The service assembles a hidden service descriptor containing its public key and a summary of each introduction point, and signs this descriptor with its private key. It uploads that descriptor to a distributed hash table (DHT). The descriptor is found by clients by using the .onion address which is a hash of the service's public key.

2. **Client Request**: When a client wants to connect to a hidden service, it loads the .onion address into a Tor-enabled client (like the Tor browser). This address corresponds to the public key of the hidden service. The client uses this key to check the DHT and retrieve the descriptor, which contains the introduction points and the service's public key.

3. **Introduction Points Connection**: After obtaining the introduction points and the service's public key, the client randomly picks a relay in the network to act as a rendezvous point and communicates it to the hidden service via one of the introduction points.

4. **Rendezvous Point**: The client builds a circuit to the rendezvous point and sends a rendezvous message there. The rendezvous point holds this message until the hidden service connects.

5. **Circuit Building**: In the meantime, the hidden service builds a circuit to the rendezvous point and sends a rendezvous message, which makes the rendezvous point connect the two circuits.

6. **Hidden Service Connection**: Now, the client and the hidden service are connected through Tor circuits and can communicate privately. The rendezvous point simply relays (end-to-end encrypted) messages from client to service and vice versa. It does not know the client's IP or the hidden service's IP. It also can't read the content of the messages because they are end-to-end encrypted between the client and the service.


## What types of attacks on tor are possible?
**Listening to traffic on exit servers**
It might be possible to see http traffic if tls isn't used. The source of the request stays hidden though

**Website fingerprinting**
An adversary could potentially monitor the entry node and use the patterns of data entering the Tor network to infer which sites are being visited. Even though the data is encrypted, the size and timing of packets could provide clues, as different sites will tend to generate characteristic traffic patterns.

**Traffic analysis**
A global passive adversary observing multiple nodes could correlate the timing and volume of traffic entering and leaving the Tor network to de-anonymize users. This requires extensive resources and is difficult to execute, but could theoretically compromise anonymity.

**Intersection Attack**
Over time, an adversary could observe when a user is active on the Tor network and correlate this with activity on a certain website or service. This is more a long-term statistical attack and could potentially reveal patterns of usage or, given enough data and time, de-anonymize a user.

**DoS**
An attacker could flood the Tor network, or specific nodes within the network, with an overwhelming amount of traffic, making it unusable for legitimate users. This doesn't compromise anonymity directly, but it disrupts the operation of the network.

---
links:  [[210 AC2 TOC - Anonymity]], [[themes/000 Index|Index]]