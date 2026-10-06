
29. What type of common vulnerability is exploited by sending commands through input fields in an application in an attempt to bypass application security?

-   A. Cross-site scripting
-   B. Cross-site request forgery
-   C. Insecure direct object references
-   D. Injection

- D. An injection attack is where a malicious actor sends commands or other arbitrary data through input and data fields with the intent of having the application or system execute the code as part of its normal processing and queries.

A, B, and C are incorrect. Cross-site scripting is an attack where a malicious actor is able to send untrusted data to a user's browser without going through any validation or sanitization process, or where the code is not properly escaped from processing by the browser. Insecure direct object references occur when a developer has in their code reference to something on the application side, such as a database key, the directory structure of the application, configuration information about the hosting system, or any other information that pertains to the workings of the application that should not be exposed to users or the network. A cross-site request forgery forces a client that has to authenticate to an application to send forged requests under the user's own credentials to execute commands and requests that the application thinks are coming from a trusted client and user.

30. What type of security testing testers who have knowledge of the systems, and in most cases access to the source code as well, and is performed offline systems?

-   A. DAST
-   B. SAST
-   C. Pen
-   D. RASP

- B. Static application security testing (SAST) is a method used to test and analyze the components of an application. It is considered "white-box" testing in that the people running the tests have knowledge of and access to the source code and systems involved.

A, C, and D are incorrect. Dynamic application security testing (DAST) is considered "black box" testing of an application and is run against live systems. The people running the test do not have any special knowledge of the system. Penetration testing is typically a "black-box" test and is run in the same manner and with the same toolsets that an attacker would attempt to use against an application. Runtime application self-protection (RASP) is typically run against systems that have the ability to tune and focus their security measures based on actual environment variables and the particular attack methods being used against them.

31. What type of software is often considered secured and validated via community knowledge?

-   A. Proprietary
-   B. Object-oriented
-   C. Open source
-   D. Scripting

- C. The most popular and widely used open source software packages have undergone extensive code review, testing, collaborative development, and scrutiny, which is not possible with proprietary software packages that are closed source and protected. With this level of scrutiny and the ability for any organization to evaluate and analyze the code from these packages, many consider them to be among the most secure and stable packages available in the industry.

A, B, and D are incorrect. Proprietary software is closed source and not available for review or validation outside of the company that has created it, and as much would not be considered secure via community knowledge. Both object-oriented and scripting are types of coding and software development and do not depend on community knowledge for security.

32. During which stage of the SDLC process should security be consulted and begin its initial involvement?

-   A. Testing
-   B. Design
-   C. Development
-   D. Requirement gathering

- D. Requirements gathering and feasibility is the first stage, and it is appropriate for security to be included as part of this stage. Security should be included at the project's inception or at least from the very earliest stages to ensure proper controls and technologies are being used, as well as to ensure security is always considered with each decision made.

A, B, and C are incorrect. The testing, design, and development phases of the SDLC all come after the initial requirements gathering phase, and as such they would be too late to involve security to ensure project success and objectives are met.

33. What security concept does the letter R represent in the DREAD threat risk model?

-   A. Reversibility
-   B. Reproducibility
-   C. Redundancy
-   D. Resiliency

- B. The R of the DREAD threat risk model refers to reproducibility, which in this case means a quantitative measure as to the ease and sophistication required to reproduce an exploit.

A, C, and D are incorrect. Reversibility refers to the ability for a cloud customer to completely remove all data and services from a cloud environment, with assurance that the data has been securely and completely removed. Resiliency and redundancy both pertain to an application or service adjusting to problems or load issues to maintain an acceptable level of performance, but they are not related to the DREAD threat risk model.

34. For security purposes, a university keeps its student and faculty data separated from each other within a system. What security concept does this strategy illustrate?

-   A. Sandboxing
-   B. Isolation
-   C. Segregation
-   D. Compartmentalization

- A. Sandboxing involves the segregation and isolation of information or processes from other information and processes within the same system or application, typically for security concerns. This is generally used for data isolation, as keeping different communities and populations of users isolated from others with similar data.

B, C, and D are incorrect. Segregation, isolation, and compartmentalization are all similar concepts, but none is the correct term in this case.

35. Which of the following would be appropriate to use in conjunction with an RSA token for a multifactor authentication system?

-   A. Thumb drive
-   B. Access card
-   C. Password
-   D. Mobile device code generator

- C. A password would be appropriate to use in conjunction with an RSA token for a multifactor authentication system because a password is something a user knows, whereas the RSA token represents something the user has. As such, they are factors of different categories.

A, B, and D are incorrect. An access card, thumb drive, or mobile device with a code generator would not be appropriate to use in conjunction with an RSA token for a multifactor authentication system because each one is something a user possesses. Therefore, they are all the same type of factor.

36. What is the recommended relative humidity level for a data center, per recommendations from ASHRAE?

-   A. 40–60 percent
-   B. 20–30 percent
-   C. 50–70 percent
-   D. 24–36 percent

- A. The recommended relative humidity rate for a data center, the American Society of Heating, Refrigeration, and Air Conditioning Engineers (ASHRAE), is 40–60 percent.

B, C, and D are incorrect. None of the other options available is the recommended humidity per ASHRAE.

37. Which protocol allows for the use of storage commands over a TCP network rather than a physical connection?

-   A. IPSec
-   B. SCSI
-   C. VPN
-   D. iSCSI

D. The most prevalent communications protocol for network-based storage is iSCSI, which is a protocol that allows for the transmission and use of SCSI commands over a TCP-based network.

A, B, and C are incorrect. SCSI is used for storage commands and functions over a physical connection, not a network. IPSec is used for secure communications and encryption between two devices, and a virtual private network (VPN) is used to allow for secure connections and tunneling from public networks into a trusted zone.

38. DRS is used for managing all aspects of clustered systems. Which of the following represents what DRS stands for?

-   A. Dynamic resource state
-   B. Distributed resource scheduling
-   C. Distributed resource selection
-   D. Dynamic resource scheduling

B. Distributed resource scheduling (DRS) is used within all clustering systems as the method for clusters to provide high availability, scaling, management, and workload distribution and balancing of jobs and processes.

A, C, and D are incorrect. None of the other options presented is what the acronym DRS stands for.

39. Which strategy involves a fake production system to lure attackers in order to learn about their tactics?

-   A. IDS
-   B. Honeypot
-   C. IPS
-   D. Firewall
