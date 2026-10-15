# Managing Data on Non-Critical Systems.

Due diligence must also be exercised to ensure that sensitive data are not residing in non-critical systems. Thoroughly checking and cleaning up such systems and associated devices is key to preventing leakage of critical data.

# Data Integrity Checks.

Organizations must also consider deploying tools to check and report unauthorized changes to hardware, software, and information. Parity checks, cyclical redundancy checks, and cryptographic hashes are examples of integrity mechanisms that should be part of an organization's arsenal to detect malicious attacks.⁴⁹

# Separating of Production, Development, and Testing Environments.

Production, development, and testing environments must be kept separate to mitigate the risk of sensitive data (in production servers) falling in the wrong hands. Another reason for keeping the environments separate is to avoid contamination of production data with test data. Since development and testing involve a lot of debugging, one incorrect program or code could cause the server performance to be compromised and also erroneously modify production data.⁵⁰

# Data Disposal Management.

Proper disposing of data is also an integral element of data security. There are multiple methods of destroying data, from overwriting to degaussing (i.e., erasing the magnetic field) and disk shredding. It is important that organizations have a well-thought-out and clearly documented data disposition plan and follow it. With growing and extensive use of third-party managed cloud-based services, organizations need to be all the more cautious that the vendor is following through with the agreed-upon data destruction plan.⁵¹ Following is a list of questions to guide management in adopting a multipronged approach to securing sensitive data.

# Data Security: Guiding Questions

+   1. Are appropriate encryption tools in use to secure data-at-rest and data-in-transit?
+   2. Is the performance of the encryption tools regularly reviewed and are changes made as deemed necessary?
+   3. Is data-in-transit protected?