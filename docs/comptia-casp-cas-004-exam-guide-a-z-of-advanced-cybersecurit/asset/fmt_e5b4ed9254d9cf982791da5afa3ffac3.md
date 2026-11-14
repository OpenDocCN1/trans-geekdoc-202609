
# White box

A team begins the white-box testing procedure with a thorough grasp of the application or system. The team uses this information to create test cases that simulate each path, input field, and processing method. The team would have access to all network information in the case of a network, which they could use and leverage in the test.

# Gray box

The team is given more information in gray-box testing than in black-box testing, but not as much as in white-box testing. Gray-box testing offers the benefit of being non-intrusive while keeping the developer-tester separation. On the other side, it could disclose some of the issues that white-box testing might miss. *[Figure 12.10](#c12.xhtml#fig12_10)* compares the three testing methods:

![](images/Image27665.jpg)

**Figure 12.10:** Testing methods

Consider the security implications of each while deciding between black-, white-, and gray-box testing. Because white-box testing exposes the code to the testers, it should only be done by extremely trusted individuals, such as internal testers. Untrusted entities, such as third-party testers, might benefit from black-box testing. Black-box testing should be performed by a third party with sufficient resources to run as many test cases as necessary and examine all code paths. You should also think about the sort of malevolent activity you’re attempting to predict.

For example, if you want to see if an attack from outside the network is likely, you should perform a black-box test, because anyone trying it is unlikely to have any internal knowledge of the application. On the other hand, if you’re more interested in the sort of assaults that may come from your own employees, gray-box testing, in which the attacker has some knowledge of the system, might be a good fit.

Finally, you should think about how the testing approach will affect the network. White-box testing has a minimal chance of affecting system stability, but black-box testing has a larger risk of causing system instability.

# Vulnerability assessment

Irrespective of the elements under investigation (network, application, database, etc.), the aim of any vulnerability assessment is to identify problems before they are exploited to compromise the component, either intentionally or accidentally. The evaluation process’s design has a significant influence on its performance. Before an assessment process is developed, the following goals of the assessment need to be identified:

*   The relative worth of the information that may be obtained by compromising the components under consideration, aids in determining the quantity and kind of resources that should be allocated to the problem.
*   Threats specific to the component; for example, due to the differences in their operation and locations on the network, a web application might not be vulnerable to the similar issues and threats as compared to the network traffic on a firewall.
*   Mitigation methods that may be used to address concerns that are discovered, such as identifying common tactics, may reveal difficulties that were not initially expected. When doing a vulnerability test on your standard network operating system image, for example, you should anticipate vulnerabilities and determine how you will resolve them.

A security analyst undertaking a vulnerability assessment must be familiar with the network’s systems and devices, as well as the duties they perform. The analyst will be able to analyze the vulnerabilities of the systems and devices based on the known and possible threats to the systems and devices with this knowledge. Security analysts should look at the controls that are already in place and see if there are any dangers to them. After that, the security analyst will utilize all of the data acquired to decide which automated tools to employ to look for vulnerabilities. When the vulnerability analysis is completed, the security analyst should double-check the results to make sure they’re correct, then present the findings to management with recommendations on how to fix the problem. Threat modeling should be carried out using this information to determine the dangers that might negatively affect systems and devices, as well as the attack techniques that could be deployed.

A vulnerability management system may be necessary in specific cases. A vulnerability management system is software that centralizes and automates the process of continuously monitoring and testing the network for vulnerabilities to some extent. Without human assistance, such a system can scan the network for vulnerabilities, report them, and, in many circumstances, fix the problem. While a vulnerability management system is a useful tool to have, no system can replace vulnerability and penetration testing done by skilled specialists, no matter how advanced it is. Keep in mind that the results of a vulnerability assessment are only a snapshot. Even if no vulnerabilities are discovered, the simplest way to summarize the situation is that there are currently no known vulnerabilities. It is hard to predict whether or not a flaw will be identified in the future.

# Self-assessment

While many businesses opt to have third-party vulnerability and penetration testing conducted, organizations should conduct self-assessments in between these examinations. Conducting tabletop exercises is one of the most frequent approaches for this procedure.

# Tabletop exercises

Before going on to higher-level testing, a tabletop exercise is the most cost-effective and efficient approach to uncovering areas of risk. A tabletop exercise is a casual brainstorming session in which corporate executives and other important personnel are encouraged to participate. In a tabletop exercise, participants agree on a specific assault scenario on which they will concentrate.

# Internal and external audits

Internal and external audits should be conducted as part of any security evaluation and testing plan. All security mechanisms that are currently in place should be tested during an audit. The following are some suggestions to consider as part of a solid security audit plan:

*   At a minimum, perform annual audits to establish a security baseline.
*   Determine your organization’s objectives for the audit and share them with the auditors.
*   Set the ground rules for the audit before the audit starts, including the audit dates/times.
*   Choose auditors who have security experience.
*   Involve business unit managers early in the process.
*   Ensure that auditors rely on experience, not just checklists.
*   Ensure that an auditor’s report reflects risks that your organization has identified.
*   Ensure that the audit is conducted properly.
*   Ensure that the audit covers all systems and all policies and procedures.
*   Examine the report when the audit is complete.

Audits are now required by several rules. Previously, organizations relied on `Statement on Auditing Standards` (`SAS`) 70, which provided auditors with information and verification concerning data center controls and processes linked to data center users and financial reporting. An `SAS` 70 audit was utilized to ensure that the data center’s rules and processes were really followed. The `Statements on Standards for Attestation Engagement` (`SSAE`) Number 16 is a new standard that verifies controls and processes while also requiring a written claim about the controls’ design and operational performance. A `Service Organization Control` (`SOC`) 1 report is the result of an `SSAE` 16 audit. Internal controls over financial reporting are the topic of this study. There are two types of `SOC` 1 reports, which are as follows:
