
- 7. During the boot process for the service/application, how do system components authenticate to each other?
- 8. Are keys used for authentication instead of passwords?

## Authorization

Many times, we would like to restrict users/systems/API/components from accessing certain functionality in a software system. Authorization enables us to do just that—that is, prevent certain operations to certain agents. Questions typically related to authorization are as follows:

- 1. What gatekeepers are used at the entry points of the application?
- 2. How is authorization enforced at the database?
- 3. Is a defense-in-depth strategy used?
- 4. Do you fail securely and only allow access upon successful confirmation of credentials?

## Configuration Management

Configuration management enables us to harden software, systems, services, and devices and lock them down, thus reducing risk to the environment. Components of configuration management include hardening standards and guidelines, reviewing application dependencies on services, looking at user and administrator interfaces, security change management, and so on. Questions are along the following lines:

- 1. What administration interfaces does the application support?
- 2. How are they secured?
- 3. How is remote administration secured?
- 4. What configuration stores are used and how are they secured?
- 5. Have hardening standards been developed for the software stack (OS, DB, application)?
- 6. Does the software system provide a way to detect variances from approved security configuration changes?
- 7. Do all groups (IT, QA, Engineering, Operations) only use approved (golden master or hardened) software images for different components such as OS, DB, web, and application servers?
- 8. Are approved images used across the entire life cycle, from development to deployment?

## Sensitive Data

This aspect deals with awareness around the type of data handled by the application and systems. In many cases, we have found that developers and operations teams are not aware or educated enough on the types of data their application will handle (either by design or mistake) and if the protection is enough for the data elements.

- 1. What sensitive data is handled by the application?
- 2. What regulatory/compliance requirements are applicable to data/data elements?
- 3. How is it secured over the network and in persistent stores? Is this good enough, given legal/regulatory requirements?
- 4. What type of encryption is used and how are encryption keys secured?
- 5. Are sensitive data elements present in logs, source code, or configuration (e.g., XML) files?

## Session Management

Securely establishing and maintaining the integrity of session is one of the key components of today’s applications—specifically, web applications. Once the user is authenticated, a session is established. This can result in multiple scenarios wherein a session can be abused. Session management focuses on preventing such abuses. Questions asked for this aspect are typically along the following lines:

- 1. How are session cookies generated?
- 2. How are they secured to prevent session hijacking?
- 3. How is persistent session state secured?
- 4. Where is session information stored? On the server or the client side?
- 5. How is session state secured as it crosses the network?
- 6. How does the application authenticate with the session store?
- 7. Are credentials passed over the wire, and are they maintained by the application? If so, how are they secured?
- 8. How are multiple sessions from a user/component handled?

## Cryptography

Everyone uses cryptography. Cryptography tends to provide a sense of security for most developers and users. However, proper use of cryptography is not that common in our experience. Using cryptography to solve the wrong problem can often cause frustration and even exposure. When dealing with cryptography, it is best to stick with well-tested, publicly available algorithms and libraries. Questions on cryptography can include the following:

- 1. What is the problem cryptography is going to solve (confidentiality, integrity, or both)?
- 2. What algorithms and cryptographic techniques are used?
- 3. Are there any proprietary or in-house algorithms used?
- 4. How long are encryption keys and how are they secured?
- 5. Does the application put its own encryption into action?
- 6. How often are keys recycled? Are certificates checked for their validity? Are certificates checked against revocation lists?

## Parameter Manipulation

Application often passes parameters to communicate with the other side. Parameters range from (not so important) iterators, variable names, and values to session tokens. Man-in-the-middle (MITM) attacks and deliberate parameter tampering makes it important for us to devise a mechanism to detect if parameters received are indeed safe and can be used as designed. Imperative here is on the receiver side—like input validation, do not blindly trust parameters.

- 1. Does the application detect tampered parameters?
- 2. Does the application rely on only client-side validation, or is there server-side validation as well?
- 3. Does it validate all parameters in form fields, view state, cookie data, and HTTP headers?
- 4. Are parameters directly used in database queries?
- 5. Are parameters directly reflected back to the browser?

## Exception Management

Gracefully handling error conditions and exceptions is critical to software applications. Often, developers miss such conditions or handle them incorrectly. Side effects from improper error handling/exception management range from denial of service or information leakage. Sample questions to probe this aspect are as follows:

- 1. How does the application handle error conditions?
- 2. Is there a default catch for exceptions?
- 3. Are exceptions ever allowed to propagate back to the client?
- 4. Are generic error messages used that do not contain exploitable information?
- 5. Do exceptions log any sensitive information to logs?
- 6. Are built-in capabilities from programming languages used for this purpose, or do developers rely on in-house modules?

## Auditing and Logging

Audit and logging are critical for security, operations, debugging, compliance, and legal reasons. Operations and debugging are often the drivers for audit/logging though security requirements are considered integral today. Below are sample questions that can be asked to understand audit and logging.

- 1. Does your application audit activity across all tiers on all servers?
- 2. How are log files secured?
- 3. Does the application log any sensitive information (e.g., credentials, data elements, session tokens)?
- 4. Are log files transported securely (e.g., TCP/TLS)?
- 5. Is the retention period clearly defined for log files? Does it align with regulatory and legal requirements?
- 6. How often are logs rotated?
- 7. Are trigger levels defined for certain types of events?

Now that you have a visual representation of the threat and have answered questions as above, the next step is to identify the threats that may affect your software application. This is also where you bring together elements of the software security group and the development team for a whiteboard meeting to brainstorm cost-effective and practical solutions to the vulnerabilities that have been identified in threat modeling. The goals of the attacker are addressed in relation to the threats and questions during the STRIDE assessment. This is done from a somewhat higher architectural and multifunctional perspective given the makeup of the brainstorming team. It is also common practice to use any available categorized threat list and apply it to any of the vulnerabilities identified earlier.

![](img/a54ed04827050a271316d34985425127_103_0.png)

Figure 4.7 Risk assessment process.

The use of attack trees and attack patterns is a traditional approach to threat assessment that can help you identify additional potential threats. Although attack patterns represent commonly known attacks, their combination with attack trees can be used for a greater depth of analysis highlighting areas you may have missed in your initial analysis or through the use of categorized lists of known threats. Since attack trees are in a hierarchical, structured, and flow diagram style, they give a great visual representation of attacks and help focus efforts on potential additional approaches to avoiding or mitigating such attacks. They are also useful for the creation of test plans and the assessment of security costs. Since the primary focus of attack patterns, attacker techniques, and STRIDE is on the goals of the attacker, using them in combination with attack trees helps bring a holistic approach to this process, especially when used in face-to-face brainstorming sessions.

Before you move on to the next stage of the threat modeling and architectural risk assessment process and start assigning values to the risk, it is important to be sure you have addressed risk with regard to the ease of exploitation, possibility, and impact. A visual representation of what knowledge you must have before moving on to the next step is given in Figure 4.7. If you don't have the information required to address an area of risk, you will need to go back through the process and fill in the gaps in your knowledge and understanding.

### 4.3.3.3 Ranking the Threats

During the final stage of the threat modeling and architecture security analysis, the threats are ranked from a risk perspective. Given that it may not be economically feasible to mitigate
