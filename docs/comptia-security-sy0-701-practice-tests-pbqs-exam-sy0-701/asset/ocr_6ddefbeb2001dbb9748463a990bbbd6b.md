Question 92. A user wants to send a confidential email to their colleague and ensure that only the intended recipient can read it. The user also wants to provide assurance to the recipient that the email was indeed sent by them. Which encryption method should the user employ to accomplish this?

+   (A) Use symmetric encryption with a shared key

+   (B) Use asymmetric encryption and encrypt the email with the recipient's public key

+   (C) Use asymmetric encryption, encrypt the email with the user's private key

+   (D) Use asymmetric encryption, first sign the email with the user's private key, then encrypt it with the recipient's public key

Explanation 92. Correct Answer: D. Use asymmetric encryption, first sign the email with the user's private key, then encrypt it with the recipient's public key.

Option D offers both confidentiality and non-repudiation. The email is encrypted with the recipient's public key, ensuring only the recipient can decrypt it using their private key. Signing the email with the sender's private key allows the recipient to verify the sender using the sender's public key.

Option A is incorrect. While symmetric encryption provides confidentiality, it doesn’t offer non-repudiation or sender verification.

Option B is incorrect. Encrypting with the recipient's public key provides confidentiality but lacks sender verification.