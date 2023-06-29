tags: #symmetric #private-key

# Key escrow and recovery

links:  [[109 AC1 TOC - Secret sharing|AC1 TOC - Secret sharing]] - [[themes/000 Index|Index]]

---

This chapter documents key escrow and recovery using the GNU project Anastasis as an example.

**Key escrow**: The key is shared among multiple parties. Each party receives a portion of the key.

**Key recovery**: The key is reassembled using the pieces from the escrow parties.

## Anastasis

The upload and restore process, along with related images, can be found on the Anastasis Project [website](https://anastasis.lu/en/). Below is a brief description of the process in words.

### Upload Process

1. Split recovery information
2. Identify the user by his attributes. Argon2 is used to derive an identifier from the user's attributes.
3. Use the HMAC Key Derivation Function (HKDF) to derive key material from the user ID. This results in 2 keys, K1 and K2.
4. Encrypt the recovery information splits with K1
5. Add some kind of truth about the user to the splits. E.g. an answer to a security question, phone number, email address
6. Encrypt the truth with K2
7. Store the data with different providers

### Recovery Process

1. Identify the user by his attributes. Argon2 is used to derive an identifier from the user's attributes.
2. Use the HMAC Key Derivation Function (HKDF) to derive key material from the user ID. This results in 2 keys, K1 and K2.
3. Send K2 to the providers, who can then decrypt the "truth" information.
4. Provider uses the truth information to authenticate the user.
5. The user receives the recovery information pieces from the providers.
6. User decrypts the parts using K1
7. User successfully recovered his information

### Simplifications
The processes from above and the images on the website have made some simplifications and left some information:

- More flexible splitting than 4/4
- There is a recovery document that stores used policies and providers.
- There is a distinction between the core secret and the master secret.
- Payment processing is omitted
- Provider salts the received information
- Anti-DoS prevention in the protocol
- There is versioning
- There are limitations of liability


---
links:  [[109 AC1 TOC - Secret sharing|AC1 TOC - Secret sharing]] - [[themes/000 Index|Index]]