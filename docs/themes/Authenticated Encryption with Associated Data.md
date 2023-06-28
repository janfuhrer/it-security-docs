tags: #symmetric

# Authenticated Encryption with Associated Data

links:  [[107 AC1 TOC - AEAD|AC1 TOC - AEAD]] - [[themes/000 Index|Index]] - [[themes/Authenticated Encryption|Authenticated Encryption]]

---

This chapter will only describe AEAD. For an overview of Authenticated Encryption, click [[themes/Authenticated Encryption|here]].

## Definition

AEAD provides:

- Confidentiality
- Integrety
- Authenticity

For every AEAD cypher 3 inputs are needed:

- Plaintext Data
- Secret Key
- Associated data

Here's how AEAD works:

1. **Encryption**: The plaintext data is encrypted using the secret key to produce ciphertext. This ensures confidentiality as only entities with the secret key can decrypt and access the data.
   
2. **Authentication**: The additional data, the ciphertext, and the secret key are used to generate a unique tag. This tag allows you to verify the integrity and authenticity of both the ciphertext and the additional data.


To decrypt and verify data using AEAD, the following inputs are required: the ciphertext, the additional data, the tag, and the secret key. The output is the plaintext data if the tag verifies correctly, and an error message otherwise.

**AEAD Protocols**

- AES-GCM with associated Data
- ChaCha20/Poly1305
- Ascon

## Example with AES-GCM

**Step 1: Key generation**

Alice and Bob agree on a secret key "secretkey123". This could be done in person or through a secure key exchange protocol such as Diffie-Hellman.

**Step 2: Alice encrypts the message**

Alice uses AES-GCM with the secret key "secretkey123" to encrypt her message "Meet me at the park". Let's assume this produces the ciphertext "abc123".

**Step 3: Alice authenticates the data**

Alice uses AES-GCM with the secret key "secretkey123", the ciphertext "abc123", and the associated data "2023-06-28" to produce a unique authentication tag. Let's say the generated tag is "xyz789".

**Step 4: Alice sends the data**

Alice then sends Bob the ciphertext "abc123", the associated data "2023-06-28", and the authentication tag "xyz789".

**Step 5: Bob verifies the data**

Bob uses AES-GCM with his copy of the secret key "secretkey123", the received ciphertext "abc123", and the associated data "2023-06-28" to generate a new authentication tag.

**Step 7: Bob compares the tags**

Bob then compares this new authentication tag with the received tag "xyz789". If they match, it verifies that the data hasn't been tampered with during transmission and is indeed from Alice.

--- 

links:  [[107 AC1 TOC - AEAD|AC1 TOC - AEAD]] - [[themes/000 Index|Index]] - [[themes/Authenticated Encryption|Authenticated Encryption]]