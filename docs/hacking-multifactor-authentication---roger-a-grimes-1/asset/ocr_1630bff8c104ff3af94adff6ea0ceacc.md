# Chapter 21 Test: Can You Spot the Vulnerabilities? 433

+   - Credential theft
- Spoofing
- Tampering
- Escalation of privilege
- Human error
- Misconfiguration
- Insider attack
- Physical attacks

Attackthreats are the steps from initial root exploit to the end that an attacker or malware program do gain an asset or component. They often get represented as nodes and subnodes, linked together in the order that they occur in different attack scenarios.

These ones, from many popular frameworks from which the MITRE ATT&CK may pull individual nodes to build attack trees. Figure 21.1 shows a snippet of the larger matrix. It contains 12 adversarial stages of attacks with over 185 individual elements, known as components and subordinates. Many other standards-setting organizations tried to accomplish a global, agreed-on set of attack components in the past, but for some reason, none of the previous attempts ATT&CK matrix seems to be the one attack people can agree on. With that said, it's a work in progress. MITRE is still asking for contributions and recommendations. I wrote an article here: www.linkedin.com/pulse/you-can-help-improve-mitres-attackck-matrix-roger-grimes.

| Execution | Persistence | Privilege Escalation | Defense Evasion | Credential Access | Discovery |
| --- | --- | --- | --- | --- | --- |
| AppScript | .bash_profile and .bashrc | Access Token Manipulation | Access Token Manipulation | Account Manipulation | Account Discovery |
| CMPST | Accessibility Features | Access Features | Binary Padding | Bash History | Application Window Discovery |
| Command-Line Interface | Account Manipulation | AppCert DLLs | BITS Jobs | Brute Force | Bookmark Discovery |
| Compiled HTML File | AppCert DLLs | AppCert DLLs | Bypass User Account Control | Domain Trust |
| Component Object Model and Distributed COM | AppInit DLLs | Application Shimming | Clear Hidden Artifact | Credentials from Web Browsers | File and Directory Discovery |
| Control Panel Items | | Bypass User Account Control | CMTSP | Credentials in Files | Network Service Discovery |
| Dynamic Exchange | Authentication Package | DLL Search Order Hijacking | Code Signing | Credentials in Registry | Network Share Discovery |
| Execution through API | BITS Jobs | Dyb Hijacking | Compile After Delivery | Exploitation for Credential Access | Network Splitting |
| Execution through Module Load | Bootkit | Elevated Privilege with Control | Compiled HTML File | Forced Authentication | Password Policy Discovery |
| Exploitation for Client Extension | Browser Extensions | Exploitation for Privilege Escalation | Component Framework | Hooking | Peripheral Device Discovery |
| Graphical User Interface | Change Default File Association | Component Object Model Hijacking | Input Capture | Permission Groups Discovery |

Figure 21.1: Partial snippet of a large MITRE ATT&CK matrix