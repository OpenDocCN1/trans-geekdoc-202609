
# Monitoring as Change Management

You can think of monitoring as a type of change management. Anytime a change is made to systems or the operating environment, a reassessment should be performed to see how the change affects a potential risk.

**Continuous monitoring** allows organizations to evaluate the operating effectiveness of controls on or near a real-time basis. Because continuous monitoring occurs immediately or closely after events in which the key controls are used, it enables the enterprise to detect control failures quickly and find ways to make improvements quickly. NIST SP 800-37 (`csrc.nist.gov/publications/detail/sp/800-37/rev-2/final`) describes continuous monitoring as an effective, organization-wide program that should include the following:

*   Configuration management
*   Control processes
*   Security impact analyses
*   Assessment of selected security
*   Security status reporting
*   Active involvement of asset owners

SP 800-37 also states that the continuous monitoring should address these functions:

*   Reporting progress
*   Addressing vulnerabilities
*   Describing how the information system owner intends to address those vulnerabilities

During the lifetime of an asset, changes will occur. People come and go, equipment changes are made, configurations change, and processes are revised. These changes will affect the organization's security posture. The result has to be assessed to determine whether these changes have altered the desired security state in a negative way.

As new assets are identified or change value and as risks are reassessed and monitored, the **risk management life cycle** is revealed. Risks are continuously reviewed, reassessed, and responded to throughout the life cycle. How exactly each life-cycle step is labeled or structured depends on the risk management framework adopted by the organization.

Throughout the risk management life cycle, the organization is entering and updating data into its **risk register**. The risk register is involved at nearly every step of the risk management process. The risk register should contain each risk as it is identified, assessed, owned by someone, responded to, and ultimately reassessed and monitored.

# Enterprise Security Architecture Frameworks and Governance

**Enterprise Security Architecture (ESA) frameworks** describe the processes used to plan, allocate, and control information security resources. ESA frameworks are used for IT governance and include people, processes, and technologies. Here are two examples of ESA frameworks:

*   **Enterprise Architecture (EA)** Used by the federal government to ensure that business strategy and IT investments are aligned
*   **Sherwood Applied Business Security Architecture (SABSA)** Another perspective on strategy based on an architectural viewpoint

Regardless of the architecture used, the goal is to measure performance and ensure that companies are receiving the best return on their security investment. ESA frameworks typically include strategy, action plans, and provisions for monitoring as well as defined metrics such as these:

*   Strategic alignment
*   Effective risk management
*   Value delivery
*   Resource management
*   Performance measurement
*   Process assurance integration

The chosen ESA framework must balance technical and procedural solutions to support the long-term needs of the business and deliver substantial long-term efficiency and effectiveness. Some of the most popular risk management frameworks (RMFs) include the FISMA risk management framework, COSO Enterprise Risk Management Framework, and ISO 31000 for Risk Management.

# Training and Awareness for Users

The role of training cannot be emphasized enough. Most employees want to do the right thing and genuinely want to see the organization thrive. However, it is the responsibility of the company to provide training. It is also important to remember that employees don't know proper policies and procedures unless they are informed as to what they are.

Just consider something as basic as emergency response. Without proper training, some employees may be tempted to simply stop what they are doing and run for the door; this may even be OK, but what's the approved response? Does each employee know what to do? Do employees know how to respond in the face of a cyberattack, disaster, weather emergency, or any other situation? Training helps assure that employees know how to respond to potential security risks and incidents.

Training does offer a good return as it increases effectiveness and efficiency. When new security processes or technologies are introduced, employees should be trained in them. Training increases morale and helps employees strive to do a better job.

# Best Practices for Risk Assessments

If you are tasked with taking part in a risk assessment, a key concern will be to define its goals and objectives. One good place to start is the mission statement. The **mission statement** typically defines a company's primary goal.

There are many techniques to consider when conducting a risk and vulnerability assessment. These best practices or approaches vary depending on the scope of the assessment and what the team is trying to protect. To secure and protect assets properly, significant amounts of time, money, and resources are required. Only then can the proper level of security be designed and implemented properly. When preparing and conducting a risk assessment, consider the following best practices or approaches:

*   Create a risk assessment policy.
*   Inventory and maintain a database of IT infrastructure components and IT assets.
*   Define risk assessment goals and objectives in line with the organizational business drivers.
*   Identify a consistent risk assessment methodology and approach for your organization.
*   Conduct an asset valuation or asset criticality valuation as per a standard definition for the organization.
*   Limit the scope of the risk assessment by identifying and categorizing IT infrastructure components and assets as critical, major, and minor.
*   Understand and evaluate the risks, threats, and vulnerabilities to those categorized IT infrastructure components and assets.
*   Define a consistent standard or yardstick of measurement for securing the organization's critical, major, and minor IT infrastructure.
*   Create a business continuity plan to help ensure that critical processes and activities can continue in case of a disaster or emergency.
*   Perform the risk and vulnerability assessment as per the defined standard.

Implementing these risk assessment best practices is not easy. It requires careful analysis and decision-making unique to the organization's business drivers and priorities as an organization. [Table 1.4](#c01.xhtml#c01-tbl-0004) shows an example summary of annualized loss expectancies. The proposed “cost,” or single loss expectancy, is fairly low when considering that most services can be replaced nearly free of charge by cloud providers.

**TABLE 1.4** Annualized loss expectancy (ALE) of DMZ assets

| Asset | Threat | SLE | ARO | ALE | Countermeasure |
| --- | --- | --- | --- | --- | --- |
| Web server | DoS | $300 | 1 | $300 | Redundant web servers |
| Email server | Open relay | $0 | .01 | $0 | Closing relay |
| DNS server | Cache poisoning | $100 | .25 | $25 | DNSSEC |
| Firewall | Enumeration | $500 | .2 | $100 | Hardening |
| Database | SQL injection | $10,000 | 2 | $20,000 | Web application firewall and input validation |
