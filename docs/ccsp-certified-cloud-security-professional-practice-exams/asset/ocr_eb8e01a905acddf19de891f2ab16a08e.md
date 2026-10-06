9. You have been tasked by management to run security tests against an application using the same toolssets and methodologies that a legitimate attacker would use, including actually attempting to leverage successful exploits. Which type of testing would this entail?

+   A. Dynamic application security testing

+   B. Penetration testing

+   C. Simulation testing

+   D. Static application security testing

+   B. Penetration (or pen) testing is done as “black-box” test but using the same tools and methodologies an attacker would use in order to evaluate the security of the application. It is designed to test vulnerabilities with various types of real-world scenarios and to actually execute exploits.

+   A is incorrect because dynamic application security testing (DAST) is run as “black-box” test where those running the test have no internal or particular knowledge of the system and may discover everything about it through the use of utilities. DAST does not attempt to fulfill malicious actions in the same manner as pen testing does.

+   C is incorrect because simulation testing is not a type of security testing that is part of the CCSP or a standard type in general. It is simply provided as an erroneous option.

+   D is incorrect because static application security testing (SAST) assesses both the source code and components of an application. It is done as a “white-box” test, and those running the tests have full access to the actual source code and configuration documentation of the application. Also, tests are done against an offline system.

10. Which of the following types of threats is focused on compromising the client rather than the server or application itself?

+   A. Cross-site scripting

+   B. Insecure direct object references

+   C. Injection

+   D. Cross-site request forgery

+   A. Cross-site scripting (XSS) is an attack where a malicious actor is able to send untrusted data to a user's browser without going through any validation or sanitization processes, or perhaps the code is not properly escaped from processing by the browser. The code is executed on the user's browser with their own access and permissions, allowing an attacker to redirect the user's web traffic, steal data from their session, or potentially access information on the user's own computer that their browser has the ability to access.

+   B is incorrect because insecure direct object references occur when a developer has in their code a reference to something on the application side, such as a database key, the directory structure of the application, configuration information about