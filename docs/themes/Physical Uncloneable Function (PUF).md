tags: #symmetric 

# Physical Uncloneable Function

links:  [[103 AC1 TOC - Randomness|AC1 TOC - Randomness]] - [[themes/000 Index|Index]]

---

## Defintion

A Physical Uncloneable Function (PUF) is a physical entity that is embodied in a physical structure and is easy to evaluate but hard to predict. It is a type of hardware that provides a unique identifier for devices and relies on the inherent uniqueness in physical microstructures to provide a set of unique and unpredictable responses to challenges. Because of their physical nature, PUFs are extremely difficult to clone, even with physical access to the device.

## Usage (Challenge Response)

PUFs are commonly used in authentication and key generation schemes. The primary way PUFs are used is through a challenge-response mechanism.

In a typical scenario, a verifier sends a challenge (a random number or signal) to the PUF device. The PUF device then responds with a unique response that is determined by both the challenge and the unique physical characteristics of the PUF. Because the physical characteristics of the PUF can't be precisely duplicated, the responses from two different PUFs to the same challenge will also be different.

## In the context of Security

1. Authentication: PUFs can be used to authenticate devices in a network by using the unique challenge-response pairs.
2. Key Generation: PUFs can also generate unique cryptographic keys, providing secure key storage.
3. Anti-Tampering: Because PUFs rely on physical characteristics that can't be exactly duplicated or predicted, they provide a level of security against physical tampering and cloning.

## Unique properties

### Compared to symmetric key cryptography

In symmetric key cryptography, both the sender and receiver share a secret key. This key needs to be stored somewhere, and if an attacker can get ahold of it, they can decrypt any messages encrypted with that key.

On the other hand, with PUFs, there's no need to store a secret key. Instead, the unique physical properties of the PUF itself are used to generate the keys. This makes it much harder for an attacker to gain access to the keys, even if they have physical access to the device.

### Security assumptions

The main security assumption behind PUFs is the difficulty of physically cloning the PUF. Even minor variations in the manufacturing process result in different physical properties, leading to different responses to the same challenge. As a result, PUFs are considered secure as long as this physical unclonability holds.

## Pros & Cons

* - Wear and Tear 
* + Denial of Service is not possible. No network needed.
* + Cloning is not possible if the security assumption holds.

## Example Protocol

A simple security protocol using a PUF might look like this:

1. The verifier sends a challenge to the device with the PUF.
2. The device uses the PUF to generate a response to the challenge.
3. The device sends the response back to the verifier.
4. The verifier checks the response against a database of known challenge-response pairs for that PUF.
5. If the response matches the known response for that challenge, the device is authenticated. If not, the authentication fails.

Note that the verifier must have a way to securely store and retrieve the known challenge-response pairs. This could be done, for example, by storing them in a secure database during an initial enrollment phase.

---
links:  [[103 AC1 TOC - Randomness|AC1 TOC - Randomness]] - [[themes/000 Index|Index]]