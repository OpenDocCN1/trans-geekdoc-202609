# Figure 3-22 Key-Hashed Message Authentication Code (HMAC)

![](bbox=[0.3, 0.1, 0.89, 0.58])

and key (2). This hash is the **key-hashed method authentication code (HMAC)**. The sender adds the HMAC to the message (3) and then encrypts this combined bit stream with symmetric key encryption (4).

The receiver decrypts the transmitted bit string for confidentiality. Then it tests the HMAC. It does this by adding the key (which it also knows) to the message and then hashing the combined message and key with the same hashing algorithm the sender used (5). This computed HMAC should match the transmitted HMAC (6). If it does, the sender is authenticated (7). Like digital signatures, HMACs also provide message integrity.

Hashing is much faster and therefore less expensive than public key encryption. This is very important given the large number of messages exchanged in a session.

# Test Your Understanding

+   33. a. What two cryptographic protections does an HMAC provide?
+      b. Do HMACs use symmetric key encryption, public key encryption, or hashing?
+      c. What is the benefit of HMACs over digital signatures?