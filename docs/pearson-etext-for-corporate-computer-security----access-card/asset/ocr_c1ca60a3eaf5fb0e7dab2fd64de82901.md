# Test Your Understanding

+   15. a. Distinguish between cryptography and cryptographic systems.
+      b. Distinguish between cryptographic systems and cryptographic system standards.
+      c. Why is the first handshaking stage the negotiation of security methods and options?
+      d. What is an impostor?
+      e. What is authentication?
+      f. What is mutual authentication?
+      g. Why is a secure keying phase necessary?
+   16. a. What three protections do cryptographic systems provide on a message-by-message basis?
+      b. What is an electronic signature?
+      c. What two protections do electronic signatures usually provide?
+      d. Distinguish between the handshaking stages and ongoing communication.

# 3.4 The Negotiation Stage

# 3.4 Explain the negotiation stage.

We have gone fairly quickly through the four stages involved in cryptographic systems. Now, we will go through each of these stages in more detail, beginning with the negotiation stage.

# Cipher Suite Options

As discussed earlier in this chapter, a cipher suite is a specific set of security methods and options for a particular cryptographic system standard (e.g., SSL/TLS). A cipher suite includes a specific set of methods and options for initial authentication, key exchange, and ongoing message confidentiality, authentication, and integrity.

| Cipher Suite | Key Negotiation | Digital Signature Method | Symmetric Key Encryption Method | Hashing Method for HMAC | Strength |
|---|---|---|---|---|---|
| NULL_WITH_NULL_NULL | None | None | None | None | None |
| RSA_EXPORT_WITH_RC4_40_MD5 | RSA export strength (40 bits) | RSA export strength (40 bits) | RC4 (40-bit key) | MD5 | Weak |
| RSA_WITH_DES_CBC_SHA | RSA | RSA | DES_CBC | SHA-1 | Stronger but not very strong |
| DH_DSS_WITH_3DES_EDE_CBC_SHA | Diffie-Hellman | Digital signature standard | 3DES_EDE_CBC | SHA-1 | Strong |
| RSA_WITH_AES_256_CBC_SHA256 | RSA | RSA | AES 256 bits | SHA-256 | Very strong |

Figure 3-9 Selected SSL/TLS Cipher Suites