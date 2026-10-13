
I continue to highlight the importance of including tracking within a vulnerability management program as it is essential to maintain documentation of the configuration of network devices, security devices, and major systems pre- and post-vulnerability mitigation. Furthermore, it is important to maintain documentation of changes, when they occur, and why they occur. Archives in secure backup locations must be kept of all prior working configurations that can be used in an emergency prior to deploying any type of mitigation process. Well-established organizations have policies governing the rate of the changes that occur and who can perform changes.

Regardless of the tool that the vulnerability management service uses to track changes, the following list covers the process for requesting, evaluating, and implementing changes. I find that mature vulnerability management services include these steps as part of the change process associated with mitigating a vulnerability.

1.  Request the change, with all required documentation. The request may originate from end users, helpdesk staff, or IT management.
2.  Record the change request into the tracking system. This action formally enters the request into the change control process.
3.  Evaluate the proposed change for its effect on the impacted information system, organizational security, and any related systems. This may involve testing in a development environment, if possible.
4.  Approve or deny the change. This step is usually performed by the vulnerability engineer or equivalent authority. Regardless of the decision, it should be recorded along with the rationale for the decision.
5.  Implement the change, if approved. Test and verify that the change had the desired effect and had no unintended effects on other systems or on its own security, known as residual risk.
6.  Update the ticketing system and configuration backup solutions to reflect changes made. This is the most critical step, as a ticketing system that contains outdated information is arguably worse than not having one at all.

[Chapter 9](#ch09.xhtml#ch09) covers all of these topics, ranging from vulnerability management to recovering from mitigation of vulnerabilities. Hopefully, this introduction to this topic demonstrates that a SOC vulnerability management program is much more elaborate than just acquiring a vulnerability scanner!

### Penetration Testing

Penetration testing is a more focused, in-depth, and specialized subset of a vulnerability management program. Vulnerability scanning gives you a list of potential vulnerabilities but does not actually attempt to exploit those vulnerabilities. A penetration test performs the same exploit an attacker could use against a vulnerability to validate that the vulnerability is real. Because exploitation is being used, penetration testing has a much higher risk of damaging systems than does vulnerability scanning. It is essential to be authorized by the asset owner before performing any form of penetration test, known in the industry as a "get out of jail free card" because if something goes wrong, you are not liable based on what was agreed upon prior to performing the penetration test.

#### NIST 800-115

According to `NIST 800-115`, *Technical Guide to Information Security Testing and Assessment*, a penetration test is made up of four phases, as shown in [Figure 3-10](#ch03.xhtml#ch03fig10).

![FIGURE 3-10 NIST 800-115 Penetration Testing Phases](Images/03fig10.jpg)

**FIGURE 3-10** NIST 800-115 Penetration Testing Phases

The first phase of the `NIST 800-115` penetration testing playbook is to plan how the penetration test will be delivered. This phase can include determining what is considered within or not within scope of the test, identifying what is considered the success criteria, obtaining authorization, and conducting other activities prior to the actual penetration testing steps. If you are using an outside party, these planning steps would be part of your statement of work, which defines how the outside party will be instructed to perform the penetration test. If you are using internal resources, this would be your penetration test plan.

The following is a list of planning or statement of work penetration questions that you need to answer:

*   **Target systems:** Which systems are within scope?
*   **Timeframe:** How long will the test last?
*   **Evaluation methods:** What tactics are within scope (rules of engagement)?
*   **Tools and software:** What tools will be used?
*   **Notified parties:** Will parties be notified about the testing or kept in the dark?
*   **Initial access level:** Where does the penetration start? (You can be outside the network or assume the attacker has gained access to one part of the network.)
*   **Authorization:** What authorization rights are given to the attacker?
*   **Risks/critical operation areas:** What are the risks of testing, and which areas of operation must be out of scope to avoid negatively impacting the business?
*   **Target space:** Which network space is part of the scope? Is it a specific subnet?
*   **Define flag:** When does the attack stop, meaning when can the penetration tester consider they have won? Essentially, what is considered success criteria?
*   **Deliverable:** What output do you want from the penetration test?
*   **Expected remediation:** Do you want any remediation to occur if something breaks or if vulnerabilities are found?
*   **Assumptions:** What can be assumed prior to the test? The answer to this means how much information is provided about the target prior to testing, also known as either white, black or gray box testing.

Discovery is the second phase of the NIST penetration testing playbook. This phase focuses on reconnaissance, which includes learning about the targeted environment and associated targets. The discovery phase tends to require the most time and effort, as the more data you know about a target, the more likely you will identify the best point of attack. I recommend to not have your penetration testers start with zero knowledge about the target, commonly referred to as a *black-box test*. The reason I recommend this is that certain aspects of your network and hosts are already publicly available. You can either pay a large amount of money to have somebody tell you what you know (assuming you are paying for a penetration testing service) or just give that information to the penetration tester and reduce the time spent on external reconnaissance research. This approach to penetration testing is commonly called *gray-box testing*, meaning you provide some information about the environment to the penetration tester, but only what you assume the attacker would easily find through open sources. This reduces the time spent on reconnaissance.

Phase three of the NIST penetration testing playbook is to attack, to perform the actual penetration test. Better-quality data that is obtained from the discovery phase will lead to much more effective attack results. If a critical vulnerability is identified during the discovery phase, the attack phase could occur within seconds, leading to a quick capture of the flag. It is common, however, for an effective attack to lead to a breach of the perimeter defenses, which means the penetration tester must step back to the discovery phase of the internal network before another attack can be launched. This is represented in [Figure 3-10](#ch03.xhtml#ch03fig10) as additional discovery, which can occur multiple times as the penetration tester navigates the target environment.
