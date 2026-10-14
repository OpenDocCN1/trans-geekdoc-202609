
## 39. B
Web application firewalls (WAFs) sit in front of web applications and watch for potentially malicious web attacks, including cross-site scripting. They then block that traffic from reaching the web application. An intrusion detection system (IDS) may detect the attack but is unable to take action to prevent it. DLP and VPN solutions are unable to detect web application attacks.

## 40. C
Input validation verifies that user-supplied input does not violate security conditions and is the most effective defense against cross-site scripting attacks. Bounds checking is a form of input validation, but it is used to ensure that numeric input falls within an acceptable range and is not applicable against cross-site scripting attacks. Peer review and OS patching are both good security practices but are unlikely to be effective against a cross-site scripting attack.

## 41. C
Durability requires that once a transaction is committed to the database it must be preserved. Atomicity ensures that if any part of a database transaction fails, the entire transaction must be rolled back as if it never occurred. Consistency ensures that all transactions are consistent with the logical rules of the database, such as having a primary key. Isolation requires that transactions operate separately from each other.

## 42. A
Pass-around reviews are often done via email or using a central code review system, allowing developers to review code asynchronously. Pair programming requires two programmers to work together, with one writing code and the other reviewing and tracking progress. Team reviews are typically done in a group, and Fagan inspection is a formal review process that would involve both the developer and a team to review the code using a formal process.

## 43. B
Multipartite viruses use multiple propagation mechanisms to defeat system security controls but do not necessarily include techniques designed to hide the malware from antivirus software. Stealth viruses tamper with the operating system to hide their existence. Polymorphic viruses alter their code on each system they infect to defeat signature detection. Encrypted viruses use a similar technique, employing encryption to alter their appearance and avoid signature detection mechanisms.

## 44. C
User acceptance testing (UAT) is typically the last phase of the testing process. It verifies that the solution developed meets user requirements and validates it against use cases. Unit testing, integration testing, and system testing are all conducted earlier in the process leading up to UAT.

## 45. D
Functional requirements specify the inputs, behavior, and outputs of software. Derived requirements are requirements developed from other requirement definitions. Structural and behavioral requirements focus on the overall structure of a system and the behaviors it displays.

## 46. C
The Open Web Application Security Project (OWASP) is widely considered as the most authoritative source on web application security issues. They publish the OWASP Top Ten list that publicizes the most critical web application security issues.

## 47. B
Chris is in an Agile sprint phase and is likely developing code based on user stories. Planning includes stakeholder stories, as well as design and test case preparation. Deployment includes the actual deployment of the application, as well as additional verification and testing.

## 48. D
This question is asking you to identify the blocking rule that should NOT be set on the firewall. Packets with public IP addresses will routinely be allowed to enter the network, so you should not create a rule to block them, making this the correct answer. Packets with internal source addresses should never originate from outside the network, so they should be blocked from entering the network. Packets with external source addresses should never be found on the internal network, so they should be blocked from leaving the network. Finally, private IP addresses should never be used on the Internet, so packets containing private IP addresses should be blocked from leaving the network.

## 49. B
This is an example of a specific type of buffer overflow known as an off-by-one error. The first line of the code defines an array of 10 elements, which would be numbered 0 through 9. The second line of code tries to place a value in the 11th element of the array (remember, array counting begins at 0!), which would cause an overflow.

## 50. C
Lost updates occur when one transaction writes a value to the database that overwrites a value needed by transactions that have earlier precedence, causing those transactions to read an incorrect value. Dirty reads occur when one transaction reads a value from a database that was written by another transaction that did not commit. Incorrect summaries occur when one transaction is using an aggregate function to summarize data stored in a database while a second transaction is making modifications to the database, causing the summary to include incorrect information. SQL injection is a web application security flaw, not a database concurrency problem.

## 51. A
Transport Layer Security (TLS) provides the most effective defense against session hijacking because it encrypts all traffic between the client and server, preventing the attacker from stealing session credentials. Secure Sockets Layer (SSL) also encrypts traffic, but it is vulnerable to attacks against its encryption technology. Complex and expiring cookies are a good idea, but they are not sufficient protection against session hijacking.

## 52. C
When a system uses shadowed passwords, the hashed password value is stored in `/etc/shadow` instead of `/etc/passwd`. The `/etc/passwd` file would not contain the password in plaintext or hashed form. Instead, it would contain an `x` to indicate that the password hash is in the shadow file. The `*` character is normally used to disable interactive logins to an account.

## 53. B
Time of check to time of use (TOCTOU) attacks target situations where there is a race condition, meaning that a dependence on the timing of actions allows impermissible actions to take place.

## 54. C
The single quotation mark in the input field is a telltale sign that this is a SQL injection attack. The quotation mark is used to escape outside the SQL code's input field, and the text following is used to directly manipulate the SQL command sent from the web application to the database.

## 55. B
Client-side input validation is not an effective control against any type of attack because the attacker can easily bypass the validation by altering the code on the client. Escaping restricted characters prevents them from being passed to the database, as does parameterization. Limiting database permissions prevents dangerous code from executing.

## 56. B
PERT charts use nodes to represent milestones or deliverables and then show the estimated time to move between milestones. Gantt charts use a different format with a row for each task and lines showing the expected duration of the task. Work breakdown structures are an earlier deliverable that divides project work into achievable tasks. Wireframe diagrams are used in web design.

## 57. D
Regression testing is performed after developers make changes to an application. It reruns a number of test cases and compares the results to baseline results. Orthogonal array testing is a method for generating test cases based on statistical analysis. Pattern testing uses records of past software bugs to inform the analysis. Matrix testing develops a matrix of all possible inputs and outputs to inform the test plan.

## 58. B
Cross-site scripting (XSS) attacks may take advantage of the use of reflected input in a web application where input provided by one user is displayed to another user. Input validation is a control used to prevent XSS attacks. XSS does not require an unpatched server or any firewall rules beyond those permitting access to the web application.
