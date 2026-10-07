# Security, Privacy, and Blockchain in Financial Technology

# 4.4.2.1 Protection of Stored Biometric Data

While the case of Apple Pay [51], biometric data is kept in an enclave, a Trusted Execution Environment (TEE) of the user's mobile [52], this is not the case for all systems where data may be less secure. If kept, on the user's mobile, malware can steal this data; it can be read if the user is close to an attacker and if Bluetooth is activated [28]. The risk of leakage of this data is also real when on the server; the service provider must then be reliable and have robust mechanisms for protecting this data. Thus, one of the major issues with biometric authentication is is protection of stored biometric data to prevent their fraudulent use.

# 4.4.2.2 Protection during Exchanges with the Remote Server

Another issue to consider biometric authentication is the protection of data sent to the server. This issue is present as soon as there is an exchange of identification or payment data. Cryptography (in particular encryption) is a well-known solution for this problem [53]. However, this requires the use of adequate protocols, since we saw in section 2.1.1 that of the most used protocols (SSL/TLS) contained flaws that have been revealed.

# 4.4.2.3 Biometric Data Protection Solutions

Protecting biometric data is of the utmost importance. Not only can this data be used by the attacker to authenticate the authentic client (impersonation), but also a biometric characteristic cannot be modified in the way as a password. Many solutions are known for the protection of stored biometric data. In the following, we give a brief review of two main categories of solutions as presented by Ilkaran Nataganathan et al. in the article “Protection of Privacy in Biometric Data” [50].

The first category is one that could be called “Biometric Encryption” and consists in encrypting the biometric data using a cryptographic technique. There are two operating modes in this category: Key Binding and key generation techniques from biometric data. In the first mode, a random secret key is homogeneously mixed with the biometric features using cryptographic tricks. The second mode is rather a set of techniques to build a cryptographic key from the biometric data and saved on a server. The second category is the technique known as “Cancelable biometric” or CB which consists in intentionally adding to distort the user’s privacy [54].

# 4.4.2.4 Balance between Accuracy and Privacy

Moreover, to have more robust and accurate biometric authentication systems, more biometric features need to be extracted from the raw biological data and stored [55]. Feature extraction is sometimes using machine learning methods on a large dataset. This clearly increases the risk of exposing private data. It has been shown that in some cases, a user’s face can be reconstructed with the stored features to establish the match. This is then a violation of the intended irreversibility feature in biometric authentication systems.