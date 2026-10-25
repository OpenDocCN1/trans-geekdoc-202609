+   3. Does it validate all parameters in form fields, view state, cookie data, and HTTP headers?
+   4. Are parameters directly used in database queries?
+   5. Are parameters directly reflected back to the browser?

# Exception Management

Gracefully handling error conditions and exceptions is critical to software applications. Often, developers miss such conditions or handle them incorrectly. Side effects from improper error handling/exception management range from denial of service or information leakage. Sample questions to probe this aspect are as follows:

+   1. How does the application handle error conditions?
+   2. Is there a default catch for exceptions?
+   3. Are exceptions ever allowed to propagate back to the client?
+   4. Are generic error messages used that do not contain exploitable information?
+   5. Do exceptions log any sensitive information to logs?
+   6. Are built-in capabilities from programming languages used for this purpose, or do developers rely on in-house modules?

# Auditing and Logging

Audit and logging are critical for security, operations, debugging, compliance, and legal reasons. Operations and debugging are often the drivers for audit/logging though security requirements are considered integral today. Below are sample questions that can be asked to understand audit and logging.

+   1. Does your application audit activity across all tiers on all servers?
+   2. How are log files secured?
+   3. Does the application log any sensitive information (e.g., credentials, data elements, session tokens)?
+   4. Are log files transported securely (e.g., TCP/TLS)?
+   5. Is the retention period clearly defined for log files? Does it align with regulatory and legal requirements?
+   6. How often are logs rotated?
+   7. Are trigger levels defined for certain types of events?

Now that you have a visual representation of the threat and have answered questions as above, the next step is to identify the threats that may affect your software application. This is also where you bring together elements of the software security group and the development team for a whiteboard meeting to brainstorm cost-effective and practical solutions to the vulnerabilities that have been identified in threat modeling. The goals of the attacker are addressed in relation to the threats and questions during the STRIDE assessment. This is done from a somewhat higher architectural and multifunctional perspective given the makeup of the brainstorming team. It is also common practice to use any available categorized threat list and apply it to any of the vulnerabilities identified earlier.