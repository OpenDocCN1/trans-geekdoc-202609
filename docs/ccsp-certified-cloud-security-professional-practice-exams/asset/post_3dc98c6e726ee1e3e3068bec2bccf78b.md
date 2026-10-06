
C is incorrect because pen testing is also done as a "black-box" test but using tools and methodologies that an attacker would use in order to evaluate the security of the application. It is designed to test vulnerabilities in various types of real-world scenarios and to actually execute exploits.

D is incorrect because runtime application self-protection (RASP) involves testing against systems that have the ability to detect attacks and threats as well as to automatically adjust their security settings or configurations to compensate for and mitigate them. RASP is designed to be done in real time on live systems.

6. A common strategy to mitigate costs when using a cloud solution for disaster recovery is to leave images offline at the DR provider and only turn them on when needed. Which of the following would be the least significant concern with this approach?

+   A. Integrity
+   B. Patching
+   C. Confidentiality
+   D. Reversibility

D. With images at a disaster recovery (DR) site, reversibility is still a concern, but in almost all cases it would be trivial to quickly delete them and remove them from the system, if needed. Although still a concern in any cloud deployment, of the possible choices, reversibility would be the least concern for a DR focus.

A is incorrect because the integrity of images is always a primary concern within a cloud environment. Unlike with physical servers, images when offline can still be accessed via a compromised system and potentially altered or compromised.

B is incorrect because patching would be a great concern when images are kept offline. The patching process would need to be augmented to guarantee that images were brought online and patched to the same level as current production systems to maintain consistency.

C is incorrect because confidentiality is a primary concern with images that are offline. In an offline state, the images still remain as files within the storage of the cloud provider, and as such, a compromised management plane or hypervisor, as well the storage system itself, could expose these files to access and copying.

7. Which stage of the BCDR process takes into account the RPO and RTO requirements set forth by management and stakeholders?

+   A. Gathering requirements
+   B. Define scope
+   C. Analyze
+   D. Implement

+   A. When you are gathering initial requirements for a business continuity and disaster recovery (BCDR) process, the recovery point objective (RPO) and recovery time objective (RTO) will be the two primary factors that drive all decisions and planning. There are many ways to accomplish continuity and disaster recovery, but the requirements for the point and time are the ultimate drivers that determine which solutions will meet management objectives.

+   B is incorrect because the scope-defining stage taking the requirements and determining the extent of the project or application. By this point, the RPO and RTO would already need to be defined and used as a guide to establish the requirements overall.

+   C is incorrect because the analyze stages taking the project requirements and translating them into an actionable project plan, complete with timelines and specific ordering and objectives. This would occur well after the RPO and RTO have been documented and integrated.

+   D is incorrect because the implementation stage involves the actual execution of the project. This is after all planning has been completed and documented.

Which of the following threats from the OWASP Top Ten is the most difficult for an organization to protect against?

+   A. Advanced persistent threats
+   B. Account hijacking
+   C. Malicious insiders
+   D. Denial of service

+   C. Malicious insiders are individuals with trusted and valid access to a system or application who then misuse that access for malicious ends. This can include stealing data, using it for their purposes, selling it, or granting others unauthorized access to it.

+   A is incorrect because advanced persistent threats involve users establishing a presence within an application or system and then using that over a period of access to data or processes to steal information. The attacker needs to first establish the system, either through phishing and other social engineering tactics or through traditional system compromises and vulnerabilities. In those cases, security personnel and administrators utilize countermeasures to minimize the chances of compromise.

+   B is incorrect because account hijacking involves either a shared account abused or someone gaining access to another's account. Account hijacking can be minimized by policies that prevent or forbid account sharing, as well as through technological measures such as multifactor authentication.

+   D is incorrect because denial of service (DoS) does not actually involve the compromise of a system or application, but is rather focused on availability. Many different approaches are available for preventing or minimizing the impact of DoS attacks against a system.

9. You have been tasked by management to run security tests against an application using the same toolsets and methodologies that a legitimate attacker would use, including actually attempting to leverage successful exploits. Which type of testing would this entail?

+   A. Dynamic application security testing
+   B. Penetration testing
+   C. Simulation testing
+   D. Static application security testing

+   B. Penetration (or pen) testing is done as “black-box” test but using the same tools and methodologies an attacker would use in order to evaluate the security of the application. It is designed to test vulnerabilities with various types of real-world scenarios and to actually execute exploits.

+   A is incorrect because dynamic application security testing (DAST) is run as “black-box” test where those running the test have no internal or particular knowledge of the system and may discover everything about it through the use of utilities. DAST does not attempt to fulfill malicious actions in the same manner as pen testing does.

+   C is incorrect because simulation testing is not a type of security testing that is part of the CCSP or a standard type in general. It is simply provided as an erroneous option.

+   D is incorrect because static application security testing (SAST) assesses both the source code and components of the application.

10. Which of the following types of threats is focused on the client rather than the server?

+   A. Cross-site scripting
+   B. Insecure object references
+   C. Injection
+   D. Cross-site request forgery

+   A. Cross-site scripting (XSS) is an attack where a malicious actor is able to send untrusted data to a user's browser without going through any validation or sanitization, allowing code to execute on the browser.

+   B is incorrect because insecure direct object references occur when a developer has in their code a reference to something on the application side, such as a database key, information that is not intended to be exposed.

+   C is incorrect because an injection attack is where a malicious actor sends commands or other arbitrary data through input fields with the intent of having the application execute the code. This could potentially allow an attacker to gain insight into configurations or security controls.

+   D is incorrect because cross-site request forgery forces an authenticated client who has user open to send forged requests under the user's credentials that the application thinks are coming from a trusted client.

11. Which concept refers to the ability to validate and prove that a specific entity did not perform operations on a system?

+   A. Repudiation
+   B. Validation
+   C. Integrity
+   D. Authentication

+   A. Repudiation relates to the ability to prove that a specific user or entity did not perform specific functions or access specific data within a system. With comprehensive logging, any transaction on a system is open to dispute or challenge by a user, who can claim they never performed the type of transaction the system says they did.

+   B is incorrect because validation refers to ensuring that data inputs are in the correct format and within acceptable parameters. It does not pertain to verifying the specific source or maintaining documentation that can later be used to prove it.

+   C is incorrect because integrity relates to the assurance that data has not been altered, created, or deleted by unauthorized parties or processes. It is not related to proving that a specific entity performed an operation.

+   D is incorrect because authentication involves the ability to prove an identity to a system or service to satisfy the particular requirements to meet that burden of proof. It is not related to proving that a specific entity conducted an operation on a service.

12. Which of the following software applications is not a utility for managing code or system configurations?

+   A. Puppet
+   B. Chef
+   C. Shibboleth
+   D. GitHub

Chapter 4: Cloud Application Security Domain
131
