
Application security testing is a key part of the SDLC. Applications can be tested using several methods, including static, dynamic, automated, and manual methods.

#### 8.2 QUESTIONS

**[1](#ch08.xhtml#ch8ques2-1).** Emmy is a new programmer at your company. She has been tasked with updating a critical line-of-business application on a tight schedule. The current version of the application is fairly stable and leverages many standardized code modules used throughout other applications in the organization. If Emmy uses these code modules, which of the following is she taking advantage of?

**A.** Code libraries

**B.** Integrated development environment

**C.** Runtime environment

**D.** Continuous integration and continuous delivery

**[2](#ch08.xhtml#ch8ques2-2).** Caleb is a cybersecurity analyst who must perform security testing on a new application. He specifically needs to test input validation for the new application. Which of the following is the best type of testing to perform to meet this requirement?

**A.** Vulnerability assessment

**B.** Code review

**C.** Fuzzing

**D.** Unit testing

#### 8.2 ANSWERS

**[1](#ch08.xhtml#r_ch8ques2-1).** A Reusing known stable code is taking advantage of the code libraries the organization maintains.

**[2](#ch08.xhtml#r_ch8ques2-2).** C Caleb must perform fuzzing on the application to test input validation, which involves inputting a variety of unexpected data into the application to see how the application handles those inputs.

### Assess the effectiveness of software security

This objective presents methods for assessing the effectiveness of the overall security program with regards to software development. The same assessment principles we have addressed in other objectives throughout the book also apply to software security, such as testing, auditing, and risk management, and we will discuss these principles as they relate to software security.

#### Software Security Effectiveness

How does one assess the effectiveness of software security? Is it a measure of how many vulnerabilities are found in the software? Is the security effective only if the software never gets hacked? Is it effective because we use secure development methodologies or secure coding? These questions can only be answered by each organization, but there are several methods to assess if the software development process is secure, as well as assess the overall security of the software itself.

In both Objectives 6.2 and 8.2 we discussed the value of assessment and testing and the various ways to test software, such as static and dynamic testing. These methods tell us how secure software is before it is implemented. However, software must continue to be assessed after implementation, using those same methods, but also using auditing and risk analysis. We’ll discuss those topics in the following sections.

##### Auditing and Logging Changes

Auditing and logging changes to software actually applies to two different contexts. First is the software development process. As mentioned in Objective 8.2, the official code base should be kept secure and should not be altered by unauthorized personnel. This is achieved by storing the code in a code repository and maintaining version control. There could be a version specifically approved for development, one for test, and, most importantly, one for production code. No one should have access to the code unless they are authorized, and even then, changes to any of those code bases should be approved and audited. Changes should be logged, particularly when changing production code, but also when changing development or test code. Version numbers should be incremented accordingly after changes are made, to maintain version control.

The other context for software auditing and logging involves the software itself, during operation and maintenance. Software should be developed with built-in logging and auditing mechanisms. For example, if someone attempts to change sensitive data in a software application, the application itself should log those attempts, or at least integrate with a larger logging system, such as the application log facility in Windows or a syslog server, to record the changes. Software also should log security events, such as authentication or authorization failures. Whether the software has its own built-in logging and auditing facilities or uses the facilities of the operating system or another logging application entirely, those logs should be protected from unauthorized personnel; only staff with administrative-level privileges should be allowed to access software application logs.

![Images](exam.jpg)

**EXAM TIP** Keep in mind the critical importance of logging all changes to a code base and auditing access to all versions of software code, to include development, test, and particularly production code.

##### Risk Analysis and Mitigation

General risk management principles were discussed at length in Objective 1.10. The same risk management principles apply to software, but in this objective, we will also present more specific details about how risk management can be used to analyze software security and mitigate security issues.

Applying risk management principles to the software development and security processes involves determining the threat actors, threats, and vulnerabilities associated with our software assets. For the purposes of this discussion, software assets include not only completed software applications, but all of the code bases in their specific versions: development, test, and production. Our software assets could also include the tools we use to develop and manage software, such as IDEs, code repositories, and various utilities. All these assets must also be secured against various threats and examined for vulnerabilities.

Vulnerabilities can be discovered in software using some of the techniques we discussed in Objective 8.2, such as SAST and DAST. However, another good place to start looking for vulnerabilities is to compare your software against industry vulnerability databases and lists, such as the Common Weakness Enumeration (CWE) Top 25 Most Dangerous Software Weaknesses, a community-developed list of hardware and software vulnerabilities hosted by MITRE, and the OWASP Top Ten, a list of the ten most critical vulnerabilities in web application software, published by the Open Web Application Security Project.

The OWASP Top Ten is periodically updated, so be sure to check for the latest version (`https://owasp.org/Top10/`). As an example, the OWASP Top Ten for 2021 is listed here:

• A01: Broken Access Control

• A02: Cryptographic Failures

• A03: Injection

• A04: Insecure Design

• A05: Security Misconfiguration

• A06: Vulnerable and Outdated Components

• A07: Identification and Authentication Failures

• A08: Software and Data Integrity Failures

• A09: Security Logging and Monitoring Failures

• A10: Server-Side Request Forgery (SSRF)

Once you have identified threats and vulnerabilities associated with your software assets, you can determine likelihood and impact, as you would with any other type of asset when assessing risk. The same types of qualitative and quantitative analyses introduced in Objective 1.10 apply to determine likelihood and impact with software assets.
