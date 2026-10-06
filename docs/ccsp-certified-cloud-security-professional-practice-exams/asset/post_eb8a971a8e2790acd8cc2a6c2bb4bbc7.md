
+   ☑ C. Shibboleth is an open source, federated identity system that is widely used by universities, nonprofits, government agencies, and other resource- or technology-related organizations.

+   ☑ A is incorrect because puppet is an open source software package that is used to maintain configurations on different types of systems and operates via an agent installed on each system.

+   ☑ B is incorrect because Chef is a software package for deploying and configuring servers in a manner where configuration is treated like code and deployed to servers for execution.

+   ☑ D is incorrect because GitHub is a widely used software platform that provides a code repository for collaborative development, including branching and versioning capabilities.

13. During an incident investigation from a suspected breach, it was discovered that some application code contained the names of underlying databases and systems that were able to be read by the attacker. What type of vulnerability does this best represent?

+   A. Injection

+   B. Sensitive data exposure

+   C. Security misconfigurations

+   D. Insecure direct object references

+   ☑ Insecure direct object references occur when a developer has in their code a reference to something on the application side such as a database key, the directory structure of the application, configuration information about the hosting system, or any other information that pertains to the workings of the application that should not be exposed to users or the network.

+   ☑ A is incorrect because an injection attack is where a malicious actor sends commands or arbitrary data through input and data fields with the intent of having the application or system execute the code as part of its normal processing and queries. This can trick an application into exposing data that is not intended or authorized to be exposed, or potentially allow an attacker to gain insight into configurations or security controls.

+   ☑ B is incorrect because sensitive data exposure relates to web applications regularly utilizing user data, such as credit cards, authentication credentials, personally identifiable information (PII), and financial information. If this information is not properly protected through encryption and secure transport mechanisms, it can quickly become an easy target for attackers. Web applications must enforce strong encryption and security controls on the application side, but also require secure methods of communication with browsers and other clients that are used for accessing the information.

C is incorrect because security misconfigurations occur when applications and systems are not properly configured or maintained in a secure manner. This can be due to a shortcoming in security baselines or configurations, unauthorized system configurations, or a failure to patch and upgrade systems as security patches are released by the vendor. Security misconfigurations also include not changing the default configurations or credentials that come with an application prior to its use and deployment.

14. What standard is used between different entities within a federated system to exchange information about authentication and user attributes?

+   A. SAML
B. XML
C. HTML
D. TLS

A. The Security Assertion Markup Language (SAML) is an open standard for exchanging information for authentication and authorization between an identity provider and a relying party. SAML provides information to ensure that authentication has been completed successfully. It also provides the identification for the identity provider and organization as well as a set of attributes about the user to be given to the relying party.

B is incorrect because XML is similar to SAML in structure and format, but is not used for exchanging information with a federated system. XML is a standard format for encoding and exchanging information, but it is not used specifically for authentication and authorization.

C is incorrect because HTML is used for encoding web pages to be consumed by clients such as web browsers. It is not a protocol or specification for exchanging information in the same manner as XML or SAML.

D is incorrect because TLS is for facilitating secure communication between two parties, including negotiating the connection and then actually encrypting and protecting packets as are transmitted between the two parties. It is heavily used within federated systems, but it is not the protocol used for actually passing information between the two parties. It secures the information.

15. Which concept is often used to isolate and separate information or processes within an environment for either security concerns or regulatory requirements?

+   A. Virtualization
B. Segregation
C. Sandboxing
D. Honeypots

+   C. Sandboxing involves the segregation and isolation of information or processes from others within the same system or application, typically for security concerns. Sandboxing typically is used for data isolation, such as keeping different communities and populations of users with similar data isolated from each other. The need for sandboxing can be due to internal reasons, such as policies, or it can come from external sources, such as regulatory or legal requirements.

+   A incorrect virtualization hosting multiple different systems under the same physical hardware. The hosts are run under the supervision and control of a hypervisor instead of direct access to the underlying hardware. Virtualization is not specifically used for separation of systems or information for security or regulatory requirements.

+   B incorrect because segregation is a general concept that relates to the topic of the question but is not an official term or concept used within computing. It is provided as an erroneous answer.

+   D incorrect because honeypots are special systems designed to appear in configuration and data as production systems, but they are kept isolated and use fake data for the purposes of enticing attackers to them. This allows an organization to learn about the types of attacks being employed against their systems and to determine additional different security approaches for their actual systems.

# 16. Which type of threat is often used in conjunction with phishing attempts and is often viewed as greatly increasing the likelihood of success?

A. Unvalidated redirects

B. Cross-site request forgery

C. Cross-site scripting

D. Insecure direct object references

+   A. Unvalidated redirects and forwards occur when an application allows external links or redirects but not properly validate or secure them. This allows an attacker to potentially redirect users through a legitimate and secure application to an for phishing attempts or other malware attacks. The site will appear to be safe and

+   B incorrect because cross-site request forgery forces an authenticated client to send forged requests coming from a trusted client.

+   C incorrect because cross-site scripting is an attack where a malicious actor sends unwanted data to the browser without any validation or sanitization of processing.

+   D incorrect because insecure direct object references occur when a developer has in their code a reference to something on the application side such as a database key, the directory structure of the application, configuration information about the hosting system, or any other information that pertains to the workings of the application that should not be exposed to users or the network.

# 17. What is the primary security mechanism to protect SOAP and REST APIs?

+   A. Firewalls
B. XML firewalls
C. Encryption
D. WAFs

C. The SOAP and REST APIs do not have built-in security mechanisms and must rely on external mechanisms. The primary means to protect both APIs is through the use of encryption, typically through the use of TLS to secure the transmission of data across the networks between the clients and services.

A is incorrect because firewalls may be used with some APIs to limit and control access to, it does not provide thorough security as encryption, nor does it secure the data transmissions from the APIs at all.

B is incorrect because XML firewalls are used to validate and control XML flowing into a system. They may be used with APIs for additional security and XML validation offloading, but they will not secure the data transmissions across the network from the APIs.

D is incorrect because a web application firewall (WAF) will enable extensive filtering and security checks on the content of data packets between API services, but they will not secure the actual data

# 18. What type of testing needs to produce the best and most comprehensive results for discovering system vulnerabilities?

+   A. Static
B. Dynamic
C. Pen
D. Vulnerability

A. Static application security testing (SAST) tests both the source code and components of an application. It is done as a "white-box" test, as those running the tests have full access to the actual source code and configuration documentation of the application. Also, tests are done against an offline system. SAST is considered the most comprehensive type of testing due to the knowledge of the systems and access to source code by the testers.

B is incorrect because dynamic application security testing (DAST) is run as a "black-box" test where those running the test have no internal or particular

Chapter 4: Cloud Application Security Domain
135
