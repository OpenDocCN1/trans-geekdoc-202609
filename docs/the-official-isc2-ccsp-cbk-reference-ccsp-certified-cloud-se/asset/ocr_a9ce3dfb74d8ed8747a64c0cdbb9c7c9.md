# UNDERSTAND SECURITY CONCEPTS RELEVANT
TO CLOUD COMPUTING

Security concepts for cloud computing mirror the same concepts in on-premises security, with some differences. Most of these differences are related to the customer not having access to the physical hardware and storage media. These concepts and concerns will be discussed in the following sections.

# Cryptography and Key Management

Cryptography is essential in the cloud to support security and privacy. With multitenancy and the inability to securely wipe the physical drive used in a CSP’s data center, information security and data privacy are more challenging, and the primary solution is cryptography.

Data at rest and data in motion must be securely encrypted. A customer will need to be able to determine whether a VM or container has been unaltered after deployment, requiring cryptographic tools. Secure communications are essential when moving data and processes between CSPs as well as to and from on-premise users. Again, cryptography is the solution.

One of the challenges with cryptography has always been key management. With many organizations using a multicloud strategy, key management becomes even more challenging. The questions to answer are

+   - Where are the keys stored?
+   - Who manages the keys (customer or CSP)?
+   - Should a key management service be used?

In a multicloud environment, there are additional concerns:

+   - How is key management automated?
+   - How is key management audited and monitored?
+   - How is key management policy enforced?

The power of a key management service (KMS) is that many of these questions are answered.

The KMS stores keys separately from the data. One benefit of encrypting data at rest is that many data breach laws provide an exemption if the data is encrypted securely. This benefit disappears if the encryption/decryption keys are stored with the data. So, if keys