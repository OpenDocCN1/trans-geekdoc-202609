Internet of Things (IoT) Security Using Blockchain

# 14.3 IOT SECURITY CONCERNS AND SOLUTIONS

# 14.3.1 SECURITY CONCERNS

+   1. **Confidentiality**: The user data must remain confidential while sharing data over a communication channel. However, In IoT communication, hackers can explore various vulnerabilities, such as accessing user data by analyzing the network traffic. It may launch various attacks to compromise the confidentiality of data, including tracing attacks, key attacks, brute force attacks, and Man-In-Middle attacks.
2. **Integrity**: As devices exchange vast amounts of data, if one device's security is compromised, it can lead to compromise, leading to integrity breaches down the line.
3. **Authentication**: Mutual authentication among IoT devices is a critical aspect. In an IoT communication scenario, if the authentication is not strong, the adversary may lay impersonation attacks, replay attacks, and masquerade attacks.

# 14.3.2 SOLUTIONS FOR SECURING I

Existing solutions for securing IoT communication are as follows:

+   1. **Authentication solutions**: To protect IoT communication from unauthorized access, existing researchers considered the following best practices:
   a. **Secure key management**: An asymmetric encryption scheme known as private key provides public and private key. If the data is encrypted using the private key, it can only be decrypted using the public key. Such key is distributed using classical communication channels and hence vulnerable to eavesdropping attacks.
   b. **Two-factor authentication**: This scheme requires multiple factors (e.g., password and OTP) to authenticate the communicating entities. Such schemes are often vulnerable to password-guessing, impersonation, and replay attacks.
   c. **Three-factor authentication**: Such schemes strengthen the security provided by adding extra features and overcomm the deficiencies of two-factor authentication schemes. They ensure that even if an attacker gains partial information about the user's smart card, biometric data, or password, they cannot compromise the entire system. Such schemes are often vulnerable to Man-In-Middle attacks, Phishing Attacks, and credential stuffing [14].
2. **Confidentiality Solutions**: To ensure that only legitimate users can decrypt the information, existing researchers have adopted the following schemes:
   . **Cryptographic primitives**: Many schemes based on symmetric and asymmetric cryptographic primitives such as RSA, ECC, and AES provide security to IoT data (stored or in transient) [3]. These schemes are susceptible to known-plaintext attacks (KPA), chosen-plaintext attacks