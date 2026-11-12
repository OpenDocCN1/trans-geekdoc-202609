# Chapter 1: Domain 1.0: General Security Concepts

+   1. B. File encryption meets all of the needs described. Full-disk encryption is easier to deploy and manage but does not protect individual files in motion and does not effectively support multiuser scenarios. Partition-level encryption has the same challenges, albeit at a partition rather than full-disk level. Record-level encryption is typically used in databases to protect individual records or entries.
+   
+   2. D. Wildcard certificates are used to handle multiple subdomains with a single certificate. A self-signed certificate will not be recognized by browsers and other services, creating confusion for customers. Root of trust certificates and CRL certificates are not types of certificates.
+   
+   3. A. Gap analysis considers control objectives and the controls that are intended to meet the objectives.
+   
+   4. D. In most production environments downtime is the primary concern when considering an application restart. Many application architectures are designed to allow restarts of individual systems or services without creating an outage or downtime. Configuration changes should not be created by a restart, patches generally apply properly, and security controls should be in place throughout the process.
+   
+   5. C. Organizations frequently use tools like git to build repositories that support their need for version control. Backout plans might note that you need to return to the prior version but will need to include how to do so. Stakeholder analysis and SOPs are not specifically supported by or improved by using git.
+   
+   6. B. Key stretching makes potentially weak keys more resistant to brute-forcing and often involves using a hash or block cipher repeatedly to make the original value harder to crack. Key rotation is the process of changing keys on a periodic basis to limit the impact of potential exposure. Master keying and passphrase armoring are not commonly used concepts for information security, although master keys are used for physical locks.
+   
+   7. C. Operational controls like log monitoring, change management processes, and vulnerability management are all put in place to support managing and using technology in a secure manner.
+   
+   8. D. Retaining the actual password is not a best practice, and thus encrypting password plain text is not a common technique to make passwords harder to crack. Since the application would need the cryptographic key to read the passwords, anybody who had access to that key could decrypt the passwords. Using a salt, a pepper, and a cryptographic hashing algorithm designed for passwords are all common best practices to prevent offline brute-force attacks.
+   
+   9. C. Both Diffie–Hellman and RSA are key exchange algorithms designed to securely allow key exchange between users or systems that have not previously communicated.
+   
+   10. B. Backout plans document what to do to return to a state prior to the change being made and are designed to be implemented if the change fails. They may involve undoing changes,