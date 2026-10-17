
# Use Case Testing and Misuse Case Testing

Use case testing is employed to assess all the different possible scenarios under which software may be correctly used from a functional perspective. Misuse case testing involves assessing the different scenarios where software may be misused or abused. A misuse case is a type of use case that tests how software code can be interacted with in an unauthorized, malicious, or destructive way. Misuse cases are used to determine all the various ways that a malicious entity, such as a hacker, could exploit weaknesses in a software application or system.

## Test Coverage Analysis

When performing an assessment, you should determine which parts of a system, application, or process will be covered by the assessment, how much you’re going to test, and to what depth or level of detail. This is referred to as test coverage analysis and is performed to derive a percentage measurement of how much of a system is going to be examined by a test or overall assessment. This limit is something that IT professionals, security professionals, and management want to know before approving and conducting an assessment.

Test coverage analysis considers many factors, such as the cost of the assessment, personnel availability, and system criticality. Obviously, highly critical systems require more test coverage than noncritical systems, to ensure that all possible scenarios and exceptions are analyzed. Test coverage analysis can be one of those measurements that can be extended over time; for example, an organization could conduct in-depth vulnerability testing on 25 percent of its assets each week so that after a month, all assets have been covered, and then the process repeats. This approach ensures that no one piece of the infrastructure is left untested.

## Interface Testing

Interfaces are connections and entry/exit points between hardware and software. Examples of interfaces include a graphical user interface (GUI) that helps a human user communicate with a system and a network interface that connects systems to networks to facilitate the exchange of data. Interfaces can also include security mechanisms, application programming interfaces (APIs), database tables, and a multitude of other examples. In any event, interfaces represent critical junction points for communications and data exchange and should be tested for security.

Security issues with interfaces include data movement from a more secure environment to a less secure one, introduction of malware into a system, and unauthorized access by a user or process. Interfaces are often responsible for not only exchanging data between systems or networks, but also data transformation, which can affect data integrity. Interface testing should address all of these issues and ensure that data exchanged between entities is of the right format and transferred with the correct access controls.

## Breach Attack Simulations

Breach attack simulations are a form of automated penetration test that the organization may conduct on itself, targeting various systems, network segments, or even applications. A breach attack simulation is normally done on a regular schedule and lies somewhere along the spectrum between vulnerability testing and penetration testing, since it attempts to find vulnerabilities that are in fact exploitable. Normally, a breach attack simulation will not actually exploit a vulnerability, unless it is purposely configured to do so; it may run automated tests and synthetic transactions to show that the vulnerability was, in fact, exploitable, without actually executing the attack. An advantage of a breach attack simulation is that since it’s performed on a regular basis, it’s not simply a point-in-time assessment, as are penetration tests. Breach attack simulations often come as part of a software package, sometimes as part of a subscription- or cloud-based security suite.

## Compliance Checks

Compliance checks are tests or assessments designed to determine if a control or security process complies with governance requirements. While compliance checks are conducted in pretty much the same way as the other types of assessments discussed so far, the real difference is that the results are checked against sometimes detailed requirements passed down through laws, regulations, or mandatory standards that the control must meet. For example, it may not be enough to confirm that the control ensures that data is encrypted during transmission; the governance requirement may mandate that the encryption strength be at a certain level or use a specific algorithm, so the control must be checked to determine if it meets that requirement.

![Images](note.jpg)

**NOTE** While definitely interconnected, the terms secure and compliant are not synonymous. A control could be secure, but not necessarily compliant due to a lack of documentation or a consistent process. The opposite is also true.

Most assessments examine not only the security of a control and how well it protects an asset, but also if it complies with prescribed governance. An individual test, such as a vulnerability assessment performed by a network scanner, may only determine if the control is secure. It’s up to the security analyst performing the overall assessment to determine its compliance with governance requirements.

## REVIEW

**Objective 6.2: Conduct security control testing** In this objective we looked a bit more in depth at security control testing. We discussed overall assessments, such as vulnerability assessments and penetration testing. Vulnerability assessments look for weaknesses in systems but do not attempt to exploit them. Penetration testing, on the other hand, not only finds vulnerabilities but assesses their severity by attempting to exploit them. Penetration testing can come in different flavors and can be performed by different types of testers, such as ethical hackers or internal and external testers. Penetration testing can be categorized in different ways, such as full-knowledge, zero-knowledge, and partial-knowledge tests.

Different tools and methods can be used for assessments but should include various methods to verify and validate security controls. Verification means that the control is tested to determine if it is working as designed; validation means that the control’s actual effectiveness in performing that function is determined. Security control testing includes:

- Log reviews to determine if the results of the tests are consistent with what we expect.
- Synthetic transactions, which are scripted sets of events that can be used to test different aspects of functionality or security with a system.
- Code review and testing, which are critical to ensuring that software code is error-free and employs strong security mechanisms.
- Misuse case testing, which looks at how users might abuse systems, resulting in unauthorized access to information or system compromise.
- Test coverage analysis, which examines data based on a percentage of measurement of how much of a system or application is tested.
- Interface testing, which examines the different connections and data exchange mechanisms between systems, networks, applications, and other components.
- Breach attack simulation, which is an automated periodic process that not only finds vulnerabilities but more closely examines whether or not they can be exploited, without actually doing so.
- Compliance checks, which ensure that controls are not only secure but also meet governance requirements.

### 6.2 QUESTIONS

**[1](#ch06.xhtml#ch6ques2-1).** You are a cybersecurity analyst who has been tasked with determining what weaknesses are on the network. Your supervisor has specifically said that regardless of the weaknesses you find, you must not disrupt operations by determining if they can be exploited. Which of the following is the best type of assessment you could perform that meets these requirements?

**A.** Penetration test
