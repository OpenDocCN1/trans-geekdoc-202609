

# Table of Contents

1. [Computer Systems Security: Planning for Success](#index.xhtml)
    1. [Legal](#index.xhtml#_legal)
    2. [Acknowledgements](#index.xhtml#_acknowledgements)
    3. [Instructional Notes](#index.xhtml#_instructional_notes)
    4. [1. Introduction](#index.xhtml#_introduction)
    5. [2. Cryptography](#index.xhtml#_cryptography)
    6. [3. Malware](#index.xhtml#_malware)
    7. [4. Protocols](#index.xhtml#_protocols)
    8. [5. Attacks](#index.xhtml#_attacks)
    9. [6. Security Solutions](#index.xhtml#_security_solutions)
    10. [7. Access Controls](#index.xhtml#_access_controls)
    11. [8. Vulnerability Management and Compliance](#index.xhtml#_vulnerability_management_and_compliance)
    12. [9. Incident Response and Continuity](#index.xhtml#_incident_response_and_continuity)
    13. [10. Virtualization](#index.xhtml#_virtualization)

![](images/avatars/default.jpg)`Ryan Tolboom`

# Computer Systems Security Planning for Success

# Legal

[Computer Systems Security: Planning for Success](https://web.njit.edu/~rxt1077/security/) by [Ryan Tolboom](mailto:ryan.tolboom@njit.edu) is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-nc-sa/4.0/), except where otherwise noted.

![Creative Commons License](images/cc.png)

All product names, logos, and brands are property of their respective owners. All company, product and service names used in this text are for identification purposes only. Use of these names, logos, and brands does not imply endorsement.

Images used in this text are created by the author and licensed under CC-BY-NC-SA except where otherwise noted.

# Acknowledgements

This material was funded by the Fund for the Improvement of Postsecondary Education (FIPSE) of the U.S. Department of Education for the Open Textbooks Pilot grant awarded to Middlesex College for the Open Textbook Collaborative.

The author would like to thank New Jersey Institute of Technology (NJIT) Open Access Textbooks (OAT) project and the [Open Textbook Collaborative Project (OTC)](https://middlesexcc.libguides.com/OTCProject) for making this text possible.

The author would also like to acknowledge the contributions and hard work of:

* `Karl Giannoglou`, Adjunct Professor NJIT
* `Jacob Jones`, NJIT 2023
* `Raymond Vasquez`
* `Justine Krawiec`, Instructional Designer NJIT
* `Alison Cole`, Computing & Information Technology Librarian Felician University
* `Ricky Hernandez`, NJIT 2024
* `Jake Caceres`, NJIT 2024

# Instructional Notes

The text, labs, and review questions in this book are designed as an introduction to the applied topic of computer security. With these resources students will learn ways of preventing, identifying, understanding, and recovering from attacks against computer systems. This text also presents the evolution of computer security, the main threats, attacks and mechanisms, applied computer operation and security protocols, main data transmission and storage protection methods, cryptography, network systems availability, recovery, and business continuation procedures.

## Learning Outcomes

The chapters, labs, and review questions in this text are designed to align with the objectives [CompTIA Security+ SY0-601](https://www.comptia.jp/pdf/CompTIA%20Security+%20SY0-601%20Exam%20Objectives%20\(3.0\).pdf) exam. The objectives are reproduced here for reference:

* `1.1` Compare and contrast different types of social engineering techniques.
* `1.2` Given a scenario, analyze potential indicators to determine the type of attack.
* `1.3` Given a scenario, analyze potential indicators associated with application attacks.
* `1.4` Given a scenario, analyze potential indicators associated with network attacks.
* `1.5` Explain different threat actors, vectors, and intelligence sources.
* `1.6` Explain the security concerns associated with various types of vulnerabilities.
* `1.7` Summarize the techniques used in security assessments.
* `1.8` Explain the techniques used in penetration testing.
* `2.1` Explain the importance of security concepts in an enterprise environment.
* `2.2` Summarize virtualization and cloud computing concepts.
* `2.3` Summarize secure application development, deployment, and automation concepts.
* `2.4` Summarize authentication and authorization design concepts.
* `2.5` Given a scenario, implement cybersecurity resilience.
* `2.6` Explain the security implications of embedded and specialized systems.
* `2.7` Explain the importance of physical security controls.
* `2.8` Summarize the basics of cryptographic concepts.
* `3.1` Given a scenario, implement secure protocols.
* `3.2` Given a scenario, implement secure network architecture concepts.
* `3.3` Given a scenario, implement secure network designs.
* `3.4` Given a scenario, install and configure wireless security settings.
* `3.5` Given a scenario, implement secure mobile solutions.
* `3.6` Given a scenario, apply cybersecurity solutions to the cloud.
* `3.7` Given a scenario, implement identity and account management controls.
* `3.8` Given a scenario, implement authentication and authorization solutions.
* `3.9` Given a scenario, implement public key infrastructure.
* `4.1` Given a scenario, use the appropriate tool to assess organizational security.
* `4.2` Summarize the importance of policies, processes, and procedures for incident response.
* `4.3` Given an incident, utilize appropriate data sources to support an investigation.
* `4.4` Given an incident, apply mitigation techniques or controls to secure an environment.
* `4.5` Explain the key aspects of digital forensics.
* `5.1` Compare and contrast various types of controls.
* `5.2` Explain the importance of applicable regulations, standards, or frameworks that impact organizational security posture.
* `5.3` Explain the importance of policies to organizational security.
* `5.4` Summarize risk management processes and concepts.
* `5.5` Explain privacy and sensitive data concepts in relation to security.

## Example Schedule

A sample schedule utilizing these resources in a 15 week semester is shown below:

| Week | Chapters | Assignments | Learning Outcomes |
| --- | --- | --- | --- |
| 1 | [Introduction](#index.xhtml#_introduction) | [Lab: Think Like a Hacker](#index.xhtml#_lab_think_like_a_hacker)<br>[Introduction Review Questions](#index.xhtml#intro_review) | `1.1`, `1.2`, `1.6`, `2.7` |
| 2 | [Cryptography](#index.xhtml#_cryptography) | [Lab: Hash it Out](#index.xhtml#_lab_hash_it_out)<br>[Cryptography Review Questions](#index.xhtml#crypto_review) | `1.2`, `1.3`, `1.6`, `2.1`, `2.4`, `2.5`, `2.8`, `3.9` |
| 3 | [Malware](#index.xhtml#_malware) | [Lab: Malware Analysis](#index.xhtml#_lab_malware_analysis)<br>[Malware Review Questions](#index.xhtml#malware_review) | `1.2`, `1.3`, `1.4`, `2.5`, `4.1`, `4.3`, `4.5` |
| 4 | [Protocols](#index.xhtml#_protocols) | [Lab: Scanning with nmap](#index.xhtml#_lab_scanning_with_nmap)<br>[Protocols Review Questions](#index.xhtml#protocols_review) | `1.3`, `1.6`, `1.7`, `3.1`, `3.2`, `4.1` |
| 5 | [Attacks](#index.xhtml#_attacks) | Quiz 1<br>[Attacks Review Questions](#index.xhtml#attacks_review) | `1.2`, `1.3`, `1.4`, `1.8`, `3.3`, `3.4`, `4.1`, `4.2` |
| 6 | [Introduction](#index.xhtml#_introduction)<br>[Cryptography](#index.xhtml#_cryptography)<br>[Malware](#index.xhtml#_malware)<br>[Protocols](#index.xhtml#_protocols)<br>[Attacks](#index.xhtml#_attacks) | Midterm Review<br>[Lab: MitM with Scapy](#index.xhtml#_lab_mitm_with_scapy) | `1.1`, `1.2`, `1.3`, `1.4`, `1.5`, `1.6`, `1.7`, `1.8`, `2.1`, `2.4`, `2.5`, `2.7`, `2.8`, `3.1`, `3.2`, `3.3`, `3.4`, `3.8`, `3.9`, `4.1`, `4.2`, `4.3`, `4.5` |
| 7 | [Introduction](#index.xhtml#_introduction)<br>[Cryptography](#index.xhtml#_cryptography)<br>[Malware](#index.xhtml#_malware)<br>[Protocols](#index.xhtml#_protocols)<br>[Attacks](#index.xhtml#_attacks) | | |

