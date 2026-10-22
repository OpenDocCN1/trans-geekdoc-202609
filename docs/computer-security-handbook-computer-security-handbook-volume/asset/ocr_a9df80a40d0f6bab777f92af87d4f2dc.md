to quantify and easily overlooked. In this example, resources are available to both implement and support the technology.

Effectiveness in increasing control is an integral part of the benefit and risk-management decisions. Each component needs to be considered in order to determine cross-benefits where controls overlap and supplement other controls. In this case, the control increase is understood and supported by management.

Data classification is the foundation for requirements. It will help drive the cost-benefit discussions because it captures the value of the information to the underlying business. In this example, the data are considered significant enough to warrant additional security measures to safeguard the data against misuse, theft, and loss.

There are many technology decisions required to secure the example environment. Management can use this approach to plot the security levels required by the system. For example, for system audit services, in order of minimal service to maximum:

+   - The minimal level of security is to have systems with a limited number of system events logged. For example, the default level of logging from the manufacturer is used but does not contain all of the required information. The logs are not reviewed but are available for forensics in the event of a security incident.
+   - A higher level of security is afforded with a log that records more activities based on requirements and not, for example, the manufacturer's default level. As in the minimal level of security, the activities are logged and available to support forensics but are not reviewed. In this case, more types of information are recorded in the system log, but it still may not contain all that is required.
+   - A sufficient log is kept on each server and is manually monitored for anomalies and potential security events.
+   - The log is automatically reviewed by software on each server.
+   - System logs are consolidated onto a centralized security server. Data from the system logs are transmitted to the centralized security server, and software is then used to scan the logs for specific events that require attention. Events such as attempts to gain escalated privileges to root or administrative access can be flagged for manual review.
+   - The maximum service level is a host-based intrusion detection system (IDS) used to scan the system logs for anomalies and possible security events. Once detected, action needs to be taken to resolve the intrusion. The procedure should include processes such as notification, escalation, and automated defensive response.

# 30.2.5.2 Business-to-Business Security Services.

The second case study uses the security services framework in a B2B example. Following is a theoretical discussion of how the framework can be applied to B2B e-commerce security. These assumptions may be made in this B2B system example:

+   - Internet-facing.
+   - Supports major transactions.
+   - Descriptions will be external and customer based (excluding support, administration, and operations security services).
+   - Trusted communication is required.