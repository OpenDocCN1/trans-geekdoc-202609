+   (B) Amy's public key

+   (C) Bob's private key

+   (D) Bob's public key

**Explanation 335. Correct Answer: D. Bob’s public key.** In asymmetric encryption, if a message is encrypted with an individual’s public key, only the corresponding private key can decrypt it. Therefore, to ensure Bob is the only person who can decrypt the document, Amy should encrypt it using Bob’s public key.

**Option A is incorrect.** Encrypting with Amy’s private key would allow anyone with Amy’s public key to decrypt it, and it would also serve as a digital signature rather than ensuring confidentiality.

**Option B is incorrect.** Using Amy’s public key would not make sense because then only Amy’s private key could decrypt it.

**Option C is incorrect.** The private key should never be shared or used for encryption. Its main use is for decryption and signing.

**Question 336.** A tech startup is developing a mobile application that offers exclusive content only to users within a specific country due to licensing agreements. Which method should the startup use to ensure that only users within that country can access the content?

+   (A) Integrate a time-based one-time password (TOTP) system