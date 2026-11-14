
For references and more information about Governance and Strategy guidance, see the following:
learn.microsoft.com/en-us/security/benchmark/azure/mcsb-governance-strategy

Table 9.1 lists all high-level key best practices to apply in your organization.
For references and more information, see the following:
github.com/MicrosoftDocs/SecurityBenchmarks/blob/master/Azure%20Security%20Benchmark/3.0/azure-security-benchmark-v3.0.xlsx

## TABLE 9.1 Microsoft Azure Security Benchmark Key best practices across various workloads

### Security Controls

| Control |
| --- |
| DP-1: Discover, classify, and label sensitive data. |
| DP-2: Monitor anomalies and threats targeting sensitive data. |
| DP-3: Encrypt sensitive data in transit. |
| DP-4: Enable data at rest encryption by default. |
| DP-5: Use customer-managed key option in data at rest encryption when required. |
| DP-6: Use a secure key management process. |
| DP-7: Use a secure certificate management process. |
| DP-8: Ensure security of key and certificate repository. |
| AM-1: Track asset inventory and their risks. |
| AM-2: Use only approved services. |
| AM-3: Ensure security of asset life cycle management. |
| AM-4: Limit access to asset management. |
| AM-5: Use only approved applications in virtual machine. |
| PV-1: Define and establish secure configurations. |
| PV-2: Audit and enforce secure configurations. |
| PV-3: Define and establish secure configurations for compute resources. |
| PV-4: Audit and enforce secure configurations for compute resources. |
| PV-5: Perform vulnerability assessments. |
| PV-6: Rapidly and automatically remediate vulnerabilities. |
| PV-7: Conduct regular red team operations. |
| ES-1: Use endpoint detection and response (EDR). |
| ES-2: Use modern antimalware software. |
| ES-3: Ensure antimalware software and signatures are updated. |
| BR-1: Ensure regular automated backups. |
| BR-2: Protect backup and recovery data. |
| BR-3: Monitor backups. |
| BR-4: Regularly test backup. |
| DS-1: Conduct threat modeling. |
| DS-2: Ensure software supply chain security. |
| DS-3: Secure DevOps infrastructure. |
| DS-4: Integrate static application security testing into the DevOps pipeline. |
| DS-5: Integrate dynamic application security testing into the DevOps pipeline. |
| DS-6: Enforce security of workload throughout the DevOps life cycle. |
| DS-7: Enable logging and monitoring in DevOps. |
| GS-1: Align organization roles, responsibilities and accountabilities. |
| GS-2: Define and implement enterprise segmentation/separation of duties strategy. |
| GS-3: Define and implement data protection strategy. |
| GS-4: Define and implement network security strategy. |
| GS-5: Define and implement security posture management strategy. |
| GS-6: Define and implement identity and privileged access strategy. |
| GS-7: Define and implement logging, threat detection, and incident response strategy. |
| GS-8: Define and implement backup and recovery strategy. |
| GS-9: Define and implement endpoint security strategy. |
| GS-10: Define and implement DevOps security strategy. |

> There are numerous cybersecurity best practices that MCSBs contain, both technical and nontechnical capabilities, and controls such as processes. The MCSBs include a set of high-impact security recommendations in a single or multi-cloud environment. In addition to security controls, MCSB offers include service baselines. In contrast to a baseline, a control describes a feature or activity in a high-level way. It does not specify the technology or implementation of the activity, while a baseline describes how the control is implemented on the individual Azure services. In Azure, service baselines are available only for Azure currently. Each organization dictates benchmark recommendations.

## Recommend Best Practices for Protecting from Insider and External Attacks

Throughout the MCRA and MCSB, you can find best practices for both insider risk and external threats. The purpose of this section is to examine primarily insider risk and external attack security operations aspects of security controls. All security controls should reduce risk in one or both of these scenarios.

In an attack chain, an adversary or insider takes technical and nontechnical actions to damage an organization. It is important to note that there is no linear path for insider risk or external attacks. Each attack can take its own unique path, but all attacks have many common elements.

As shown in Figure 9.1, the MCRA includes an attack chain diagram that illustrates standard external and insider attack techniques.

In Figure 9.1, the top portion illustrates the steps common to many external attacks, as well as the Microsoft capabilities corresponding to each step. In the bottom part, you will find information about leading insider risk indicators and how Microsoft Purview Insider Risk Management helps you quickly identify, triage, and act on risky user activity.

Several common steps and patterns are involved in external attacks, which can be seen in Figure 9.1. The majority of external attack variation results from using different entry points. Furthermore, attacks may differ depending on the attackers’ objectives, including stealing data, encrypting data, or disrupting business operations.

An external attack that results in a significant incident typically involves some form of privilege escalation using credential theft, which can be mitigated by safeguarding privileged access.

An early adaptation of the military concept of kill chain to cybersecurity was created by Lockheed Martin. As a result of this concept of a cybersecurity attack chain, organizations have evolved their understanding of attacks and security controls by viewing attacks as a sequential sequence of events. For detailed control planning, such as threat detection coverage, many organizations today utilize the MITRE ATT&CK framework.

Figure 9.2 illustrates how these are related to a simple prepare-enter-traverse-execute (PETE) model developed by Microsoft to improve communication with nonsecurity professionals and business leaders.

Attackers can use different techniques to achieve their objectives of preparing, entering, traversing, and executing. They can also combine various techniques or use the same process repeatedly to accomplish their goals.

### FIGURE 9.1 Microsoft Cybersecurity Reference Architecture

![](img/5ab9852bf401dd309bf0f81797a91445_425_0.png)

### FIGURE 9.2 Prepare-enter-traverse-execute

![](img/5ab9852bf401dd309bf0f81797a91445_426_0.png)

The MCRA and MCSB security best practices are all intended to minimize the risk of attackers succeeding. The MCRA best practices primarily focus on detecting, responding, and recovering from external attacks. Key best practices include the following:

- **Continual improvement toward complete coverage:** Ensure that areas with no visibility and highly vulnerable areas without any preventative measures are continuously improved.
- **Balanced control investments:** Invest in security controls across the entire life cycle of identifying, protecting, detecting, responding, and recovering.
- **From SIEM for everything to XDR + SIEM:** SIEM has been the primary tool for detecting attacks and responding to them for many security operations. From SIEM for everything to XDR and SIEM, security information and event management (SIEM) has been the primary tool for detecting and responding to attacks. Because of their rapid reduction in false positives, extended detection and response (XDR) tools quickly became indispensable for the platforms they monitor (starting with endpoint detection and response [EDR] for endpoints). These tools protect a different breadth of sources than the SIEM for technologies covered by XDR, but they significantly simplify and enhance detection and response. The security best practices then evolved to reflect the strengths of SIEM (comprehensive visibility and correlation across all tools and technology) and XDR (simple, high-quality threat detection of covered assets), as well as the collective need for both types of tooling in security operations.
- **Modern analytics and SOAR Automation:** Integrate the use of security orchestration, automation, and response (SOAR), machine learning (ML), and user entity behavioral analytics (UEBA) technologies to reduce the amount of manual effort involved in security operations. By automating manual actions, SOAR technology reduces distractions and fatigue for human analysts during detection, investigation, and response procedures. Machine learning significantly improves detection by extending human expertise over large data sets and detecting anomalies that may indicate malicious activity. In contrast to attempting to find patterns in the full set of raw log data, UEBA improves detection and investigation by profiling the individual accounts and entities compromised by attackers.
