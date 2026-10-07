Option B is incorrect. Hashing the code provides a mechanism to check for alterations (integrity), but it does not provide non-repudiation or evidence of the specific team member’s approval.

Option C is incorrect. Encrypting with the team member’s public key doesn’t provide non-repudiation. Moreover, only the team member with the corresponding private key would be able to decrypt it, which might not be desirable for production releases.

Question 64. Your company has recently deployed an update to its CRM application. Post-update, users are experiencing connectivity issues. As a security administrator, which of the following steps should you take FIRST to address the connectivity problem without causing data loss?

+   (A) Restart the application immediately
(B) Disconnect all users and then restart the application
(C) Validate the update's integrity and then restart the application
(D) Reinstall the previous version of the CRM application

Explanation 64. Correct Answer: C. Validate the update’s integrity and then restart the application. Before making any changes, it’s essential to ensure the update’s integrity. This means confirming that the update was correctly applied and that there were no issues during its installation. Once the update’s integrity is confirmed, a restart can help apply any changes that may not have taken effect immediately.