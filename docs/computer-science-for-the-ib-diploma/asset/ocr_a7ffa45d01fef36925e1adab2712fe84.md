Encryption key: a string of characters or numbers used by an encryption algorithm to encode or decode data. It is the values that are input into the mathematical functions responsible for scrambling or descrambling the data.

Symmetric encryption is where the same key is used for both encrypting and decrypting the data. This means the key must be shared between both the sender and receiver in a secure manner.

Symmetric encryption is generally faster and less computationally intensive than its asymmetric equivalent, so it makes sense to use it for encrypting large files.

When physical distance separates the sender and receiver, it can be difficult to share the encryption key in such a manner as to be protected against eavesdroppers. There are two common solutions to this problem:

+   - Use asymmetric encryption to establish secure communications. Use this asymmetric method to exchange and agree on a symmetric key, and then switch communications to the faster, more efficient symmetric approach.
+   - Use a mathematically secure method to exchange keys, such as Diffie Hellman (covered later in this section).

# ## Asymmetric encryption

![](bbox=[0.28, 0.35, 0.89, 0.52])

Asymmetric encryption is when the security key used to encrypt data is different from the key used to decrypt it. If it can work successfully, there are significant benefits to be gained, as it means two parties wanting to communicate in encrypted form do not have to meet privately to exchange an agreed-upon encryption key, as is required for symmetric encryption. Instead, the encryption key can be published publicly, and any person wishing to send a message can use it to encrypt the data, so that only the recipient and key-holder can decrypt it to read.

For example: If Alice wants to send a secure message to Bob, she encrypts it using Bob's public key. Only Bob can decrypt this message with his private key.

How does it work? How is it algorithmically possible to use one cipher key to encode the data and a different key to decode it? The answer is mathematics! The following walkthrough, inspired by an example by Henry J. Schmale, is simplified and loosely based on the RSA (Rivest-Shamir-Adleman) encryption algorithm.

# ### Key information

The mathematical walkthrough is provided to demonstrate how such algorithms are possible, as an exercise of intellectual interest. Understanding the mathematics is beyond the scope of the syllabus. You will not be examined on this procedure or asked to do these calculations in the exams.