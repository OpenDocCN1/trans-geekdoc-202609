
# Privilege Escalation

Once an attacker has access, they will attempt to refer to the process of an attacker elevating their privilege on a system from a low-level user to administrator or root. Privilege escalation occurs when code runs with higher privileges than those of the user who executed it. Privilege escalation techniques include the following:

## Vertical Privilege Escalation

A lower-privilege user or application accesses functions or content reserved for higher-privilege users or applications.

## Horizontal Privilege Escalation

A normal user accesses functions or content reserved for another normal user.

Applications and operating systems seek to prevent these types of attacks in various ways. One is by building in rings of protection. The *rings-of-protection model* provides the operating system with various levels at which to execute code or restrict access to it. It provides much greater granularity than a system that just operates in user and privileged modes. As you move toward the outer bounds of the model, you have less privilege. As you move to the inner bounds, you have more privilege.

# Persistence

Systems may be patched, vulnerabilities found, or the security breach may be noticed. This step is when the penetration test team seeks to maintain their access. This may be accomplished by creating accounts, planting backdoors, or creating an encrypted tunnel.

# Covering/Clearing Tracks

Once the objectives of the test are accomplished, the team will remove any items that have been placed on the network, restore systems, and remove any remaining code.

# Determining Recommendations

This is the point in the process when the team starts to do a final review of their findings. Through meetings and reviews, the team begins to determine its recommendations.

# Writing a Report and Presenting Findings

The final step is to create the report. The report lists the vulnerabilities and risks that have been discovered. The report also lists recommendations regarding administrative, technical, and physical controls that should be implemented to secure the organization's critical assets better.

# Assessment Types

There are several different approaches to penetration testing. Depending on the situation and what your employer or client is seeking, the assessment may proceed in one of several ways. These include the following:

## No Knowledge Testing

With this type of test, there is very little or no knowledge of the target network or its systems. This testing simulates an outsider attack, as outsiders usually don't know much about the network or systems that they are probing. The penetration test team must gather all types of information about the target before starting the test. The team typically verifies that the IP address range is correct before attempting to penetrate the network and beginning to profile its strengths and weaknesses. The company's personnel should not know that they are being tested. This provides the additional advantage of determining how effectively personnel are adhering to monitoring, detection, and response policies, as well as the policies’ effectiveness.

## Full Knowledge Testing

A test with full knowledge takes the opposite approach of a test with no knowledge testing. This assessment is one in which the penetration test team has full knowledge of the network, systems, and infrastructure. This information allows the penetration test to follow a more structured approach.

## Tabletop Exercise

The goal of a *tabletop exercise* is to raise situational awareness in the context of information security. It is also designed to foster discussion on incident response in brief, practical discussion periods. For management, tabletop exercises provide a great opportunity to demonstrate to the incident response group the scenarios that are most likely to occur.

## Internal and External Audits

An *internal audit* is one conducted to improve an entity's operations. Medium-sized and large-sized operations usually have an internal auditing department to monitor the operations of the organization regarding the improvement of effectiveness, control, governance processes, and risk management. The department accomplishes this by providing recommendations and suggestions on the basis of the assessment of data and business transactions. The main purpose of an internal audit is to provide an independent opinion and consultancy to senior management and those charged with governance (governing bodies). Internal audits are mostly performed by an employee of the organization; however, some organizations hire the services of an audit firm for an internal audit.

An *external audit* indicates an audit of the organization by an independent audit firm that is not controlled by the organization that it is auditing. An external audit is performed because of statutory requirements in order to express an opinion on whether the security controls, processes, and documentation are in accordance with acceptable standards and regulatory requirements in all material aspects. For an external audit, the auditor is required not to have any prior association with the organization; that is, an external auditor must be independent in their work.

# Vulnerability Assessment Areas

Not all security assessments are the same; for each individual assessment, different areas may be reviewed. Sometimes, a security assessment may not focus on the network, firewalls, insiders, or even outsiders. After all, code is the common component that allows applications and software to meet our needs. Even in a well-deployed and secured network, a weak application can expose a company's critical assets to an attacker. A security code review is an examination of an application that is designed to identify and assess threats to an organization. Common areas of assessment are discussed in the following sections.

## Denial-of-Service

DoS testing looks at a company's ability to withstand a potential DoS attack. Some organizations may also do this to examine how the network operates under a heavy load or high utilization. Goals for this category of test typically include assessing the impact of a DoS attack, determining the performance of the network, and measuring the impact of the devices that are being attacked.

A DoS attack is an attack on availability. It is intended to prevent access to legitimate users of a system, website, or network causing loss of revenue, impacting customer trust, and forcing an enterprise to spend time, effort, and money to remediate. Most DoS attacks are accomplished by flooding a target with ICMP traffic or sending traffic like an overflow type attack that makes it crash. A distributed denial of service (DDoS) has the same ill intent but is orchestrated from many sources. DDos can impact business for days to months as an organization attempts to recover.

## Telephony

Testing voice systems involves more than just traditional phone systems. Telephony testing includes an examination of voice over IP (VoIP), fax, PBX, and all voice lines. There are still computers hooked up to modems for items such as vendor access to specialized systems (for example, HVAC) as well as emergency backup remote access for networking staff. Each area can be critical to a company. For example, if a company's PBX is hacked, it can be subject to tool fraud, loss of revenue, and even loss of confidential information.

# Application and Security Code Testing
