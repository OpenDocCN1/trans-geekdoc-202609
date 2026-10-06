
- 32. What type of device is often leveraged to assist legacy applications that may not have the programmatic capability to process assertions from modern web services?
A. Web application firewall
B. XML accelerator
C. Relying party
D. XML firewall

- 33. At which phase of the SDLC process should security begin participating?
A. Requirements gathering
B. Requirements analysis
C. Design
D. Testing

- 34. Which of the following is NOT part of the OWASP Top Ten list of critical web application security risks?
A. Injection
B. Sensitive data exposure
C. Insecure direct object references
D. User ID and password authentication schemes

- 35. What type of identity system allows trust and verifications between the authentication systems of multiple organizations?
A. Federated
B. Collaborative
C. Integrated
D. Bidirectional

- 36. It is vital during the initial requirements gathering for a new project or application to include all the pertinent stakeholders who will drive the requirements and determine whether the critical success factors have been achieved. Which of the following would NOT be a key stakeholder to include during these initial stages?
A. Developers
B. Management
C. Security
D. Users

- 37. The Simple Object Access Protocol (SOAP) allows programs from different environments or platforms to communicate seamlessly with each other over HTTP. If you are using SOAP, which data format are you using for information exchange?
A. SAML
B. XML
C. JSON
D. HTML

- 38. Single sign-on systems work by authenticating users from a centralized location or using a centralized method, and then allowing applications that trust the system to grant those users access. What would be passed between the authentication system and the applications to grant a user access?
A. Ticket
B. Certificate
C. Credential
D. Token

# QUICK ANSWER KEY

1. A
2. A
3. C
4. B
5. A
6. D
7. A
8. C
9. B
10. A
11. A
12. C
13. D
14. A
15. C
16. A
17. C
18. A
19. A
20. C
21. B
22. C
23. D
24. C
25. D
26. A
27. B
28. A
29. C
30. A
31. D
32. B
33. A
34. D
35. A
36. A
37. B
38. D

# Comprehensive Answers and Explanations

- 1. You have a new application that is about to be put into production and used by customers. Management would like to undertake an exhaustive test of the system by assessing the known controls and configurations as well as reviewing the source code and components. Which type of testing would this represent?
A. SAST
B. DAST
C. Pen
D. RASP

A. Static application security testing (SAST) assesses both the source code and components of an application. It is done as a "white-box" test, as those performing the tests have full access to the actual source code and configuration documentation of the application. Tests are done against an offline system.

B is incorrect because dynamic application security testing (DAST) is run as a "black-box" test, where those performing the test have no internal or particular knowledge of a system and must discover everything they know about through the use of utilities.

C is incorrect because pen testing is also done as a "black-box" test, but using the same tools and methodologies that an attacker would use in order to evaluate the security of the application. Pen testing is designed to assess vulnerabilities in various types of real-world scenarios.

D is incorrect because runtime application self-protection (RASP) is used to test against systems that have the ability to detect attacks and threats, and then to automatically adjust their security settings or other configurations to compensate for and mitigate these attacks and threats. RASP is designed to be done in real time on live systems.

- 2. An employee of your company submitted a security ticket claiming that he was able to access areas of an application by going through certain functions that he should not be able to. What type of vulnerability does this best illustrate?
A. Missing function-level access control
B. Security misconfiguration
C. Sensitive data exposure
D. Unvalidated redirects and forwards

A. Many applications will do authorization checks and assign access rights when a user accesses the application and accesses different functions, if the application does not verify authorization for each function, it is possible for the user to be able to elevate access, either intentionally or accidentally. The application should verify authorization as a user accesses each new function or piece of data.

B is incorrect because security misconfiguration refers to a system baselines were not correctly applied, unauthorized changes were made, or security patches and updates from the vendor were not applied.

C is incorrect because sensitive data exposure occurs when protected data, such as PII or credit card information, is not properly encrypted or masked, and is thus susceptible to attackers. This exposure refers to specific data within the application and is not directly related to specific functions of the application.

D is incorrect because unvalidated redirects and forwards occurs when an application allows links or redirects but does not properly validate or secure them. This enables an attacker to potentially redirect or secure them.

- 3. Where would be the most appropriate location for authentication checks?
A. Between presentation and data layers
B. Between layers
C. Between firewalls
D. Between application

C. Authentication systems, as a security check, enforce limited time for authentication tokens and any checks. If it takes longer than the allowed time, the request will be considered stale and invalid, and it will likely loop back to try the process again. If a large geographic distance exists and network latency occurs, it is possible on systems, if they have short validity periods, for authentications to fail and for system access to be denied.

A is incorrect because regulations are always a concern, especially over a large geographic distance, where some variances are almost guaranteed. However, this is not the best answer because it is not specific to authentication systems and their operational usage.

B is incorrect because redundancy is not something that will be impacted by geographic distance between data centers. Systems can have redundancy implemented in a variety of ways, regardless of where they are actually hosted or the distance between them.

D is incorrect because interoperability will be a global issue across the entire enterprise, not one specifically impacting authentication systems. With most modern authentication systems, interoperability is also not a primary concern because these systems are specifically designed to be multiplatform and flexible.

- 4. When you are changing to a different data center for a disaster recovery scenario, which of the following could pose a challenge to authentication systems over geographic distance?
A. Regulations
B. Latency
C. Redundancy
D. Interoperability

B. Authentication systems, as a security check, enforce limited time requirements for authentication tokens. If it takes longer than the allowed time, the request will be considered stale and invalid.

- 5. Which type of testing involves entirely attacking the security of a system without actually attempting to alter systems or fully execute malicious actions?
A. DAST
B. SAST
C. Pen
D. RASP

A. Dynamic application security testing (DAST) is run as a "black-box" test where those running the test have no internal or particular knowledge of a system and must discover everything they know about it through the use of utilities. DAST does not attempt to fully execute malicious actions in the same manner as pen testing does.
