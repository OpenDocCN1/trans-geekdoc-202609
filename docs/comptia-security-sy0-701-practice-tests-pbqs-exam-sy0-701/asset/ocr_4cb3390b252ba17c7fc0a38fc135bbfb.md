Option A is incorrect. Making all cloud storage buckets or containers publicly accessible can expose sensitive data and is a common misconfiguration that leads to data breaches.

Option C is incorrect. Using the same SSH key pairs across all instances can be risky. If an attacker obtains the SSH key, they can gain unauthorized access to all instances that use that key.

Option D is incorrect. While it’s important to limit access based on the principle of least privilege, IAM roles should be appropriately assigned to staff based on their responsibilities and not just their seniority. This ensures that users have the necessary permissions to do their jobs without unnecessary access to sensitive resources.

Question 90. RedFlare Solutions, a financial firm, is storing sensitive client data in a database. The Chief Information Security Officer (CISO) insists that the data should be unreachable even if it’s intercepted during transmission or if the storage is compromised. Which encryption standard would best serve this requirement?

+   (A) Symmetric encryption using a shared key
(B) Hashing the data with a one-way function
(C) Encrypting the entire database using transparent encryption
(D) Storing the data in a proprietary format

Explanation 90. Correct Answer: C. Encrypting the entire database using transparent data encryption. Transparent data encryption (TDE) encrypts the entire database, ensuring that data remains encrypted both at rest and during transmission. It