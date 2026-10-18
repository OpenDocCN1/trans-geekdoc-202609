
In addition to monitoring traffic for the host, the HIDS/HIPS may be integrated with other security software functions and may perform traffic filtering for the host, anti-malware functions, and even advanced endpoint monitoring and protection. Although not required, most modern HIDSs/HIPSs in large enterprises are agent-based, centrally managed systems. They use software endpoint agents installed on the host so security information can be reported back to a centralized collection point and analyzed individually or in aggregate by a SIEM, as discussed in Objective 7.2.

Objective 7.2 also discussed the methods by which an IDS/IPS detects anomalous network traffic and potential attacks. To recap, there are three primary methods that can be used alone or in combination to detect potential issues in the network:

• `Signature- or pattern-based (rule-based) detection` (also called `knowledge-based detection`) uses preconfigured attack signatures that may be included as part of a subscription service from the IDS/IPS vendor.

• `Anomaly- or behavior-based analysis` involves allowing the IDS/IPS to “learn” the normal network traffic patterns in the infrastructure; when the IDS/IPS detects a deviance from these normal patterns, the system alerts an administrator.

• `Heuristic analysis` takes behavior analysis one step further; in addition to catching changes in normal behavior patterns, a heuristic analysis engine looks at those abnormal behaviors to determine what types of malicious activities they could lead to on the network.

![Images](exam.jpg)

**EXAM TIP** You should understand the methods by which IDS/IPSs detect anomalies and potential intrusions, as well as how they are classified as either network-based or host-based systems.

Note that IDS/IPSs can look at a multitude of traffic characteristics to detect anomalies and potentially malicious activities, including port, protocol, service, source and destination addresses, domains, and so on. These characteristics could also include particular patterns like abnormally high bandwidth usage or network usage during a particular time of day or night when traffic usually is light. Advanced systems can also do in-depth content inspection of specific protocols, such as HTTP, and even intercept and break secure connections using protocols such as TLS, so that the systems can detect potentially malicious traffic that is encrypted within secure protocols.

**Cross-Reference**

Intrusion detection and prevention were also discussed in Objective 7.2.

##### Third-Party Provided Security Services

Organizations, particularly smaller ones, may not always be staffed sufficiently to take care of their own security services and infrastructure. With the mounting security challenges that organizations now face, there is an increasing trend in the use of `managed security services (MSSs)`, also known as `Security as a Service`, third-party providers to which organizations can outsource some or all of their security functions. An MSS can manage various aspects of an organization’s security, such as security device configuration, maintenance, and monitoring, security operations center (SOC) services, and even user and resource management or control.

Contracting services out to a reputable third-party service provider has the following advantages, among others:

• `Cost savings` The organization does not have to hire and train its own security personnel, nor maintain a security infrastructure.

• `Risk sharing` Since the organization does not maintain its own security infrastructure, some of the risk involved with this endeavor is shared with another party.

However, there are also distinct disadvantages to contracting with a third-party service provider:

• `Less control over the infrastructure` The organization does not always have the ability to immediately control how the infrastructure is configured or react to both customer needs and events. It relies on the third party to be dependable in its responsiveness, as well as have a sense of urgency.

• `Legal liability` In the event of a breach, the organization still retains ultimate responsibility and accountability for sensitive information (although the third-party service provider may also have some degree of liability).

• `Lack of visibility into the service provider’s infrastructure` The organization may not even be able to look at its own audit logs or security device performance. The organization may also not have the ability to audit the third-party security provider’s processes, legal or regulatory compliance, or infrastructure.

Regardless of the security functions an organization chooses to outsource, the key to a successful relationship with a third-party security service provider is the service level agreement (SLA). An MSS usually offers a standard SLA, which the organization should carefully review and, if necessary, seek modification of before entering into the contract with the provider. The SLA should clearly define both distinct and shared responsibilities the organization and the third-party provider have in securing systems and information. The SLA should also address critical topics such as availability, resiliency, data information ownership, and legal liability in the event that an incident such as a breach occurs.

**Cross-Reference**

Third-party providers and some of the services they offer, as well as service level agreements, are discussed in detail throughout Objectives 1.12, 4.3, 5.3, and 8.4.

##### Honeypots and Honeynets

In their ongoing effort to prevent attackers from getting to sensitive hosts, administrators often deploy a honeypot on the network as part of their defense-in-depth strategy. A `honeypot` is an intentionally vulnerable host, segregated from the live network, that appears to attackers as a prime target to exploit. The honeypot distracts the attacker from sensitive hosts, and at the same time gives the administrator an opportunity to record and review the attack methods used by the attacker.

Honeypots are often deployed as virtual machines and are segmented from sensitive hosts by both physical and virtual means. They may be on their own physical subnet off of a router, as well as use VLANs that are tightly controlled. They may have dedicated IDS/IPSs monitoring them, as well as other security devices. Administrators often have the option of dynamically changing the honeypot’s configuration or disabling it altogether if needed in response to an attacker’s actions.

A sophisticated attacker may recognize a lone honeypot, so a more advanced technique network defenders may deploy is a honeynet. A `honeynet` is a network of honeypots that can simulate an entire network, including infrastructure devices, servers, end-user workstations, and even security devices. The attacker may be so busy trying to navigate around and attack the honeynet that they do not have time to attack actual sensitive hosts before a security administrator detects and halts the attack.

Note that an organization should carefully consider the use of honeypots and honeynets before deciding to deploy them. If implemented improperly, a honeypot/honeynet can cause legal issues for an organization, since attackers have been known to use a honeypot to further attack a different network outside the organization’s control. This could subject the organization to potential legal liability. Additionally, it can be a legal gray area if an organization tries to press charges against an attacker, as the attacker might be able to claim they were entrapped, particularly if the honeypot was set up by a law enforcement or government agency. The organization should definitely consult with its legal department before deploying honeypot technologies.

##### Anti-malware
