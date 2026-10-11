
*   ° Significant operational actions [[3]](#Ch007_337-359_B978044318734600009X.xhtml#bb0020)

The intelligence gained from proactive audit log management and monitoring can be very beneficial: the collected antivirus logs of thousands of systems can give a very accurate picture of the current state of malware. Antivirus alerts combined with a spike in failed authentication alerts from authentication servers or a spike in outbound firewall denials may indicate that a password-guessing worm is attempting to spread on a network.

According to “Five mistakes of Log Analysis” by Anton Chuvakin (see [https://www.computerworld.com/article/2567666/five-mistakes-of-log-analysis.xhtml](https://www.computerworld.com/article/2567666/five-mistakes-of-log-analysis.xhtml)), audit record management typically faces five distinct problems:

1.  Logs are not reviewed on a regular and timely basis.
2.  Audit logs and audit trails are not stored for a long enough time period.
3.  Logs are not standardized or viewable by correlation toolsets—they are only viewable from the system being audited.
4.  Log entries and alerts are not prioritized.
5.  Audit records are only reviewed for the “bad stuff” [[4]](#Ch007_337-359_B978044318734600009X.xhtml#bb0025).

Many organizations collect audit logs, and then commit one or more of these types of mistakes. The useful intelligence referenced in the previous paragraph (identifying worms via antivirus alerts, combined with authentication failures or firewall denials) is only possible if these mistakes are avoided.

### Centralized Logging

Centralized log storage should be configured. Having logs in a central repository allows for more scalable security monitoring and intrusion detection capabilities. A centralized log repository can also help to verify the integrity of log information should the endpoint’s view of the logs be corrupted or intentionally altered. Ensuring the integrity of log information should be considered when transmitting and storing log data.

> **Note**
>
> `Syslog`, the most widely used logging subsystem, by default transmits log data in plaintext over `UDP/514` when sending data to a remote server. `UDP`, a transport protocol that does not guarantee the delivery of transmissions, has implications for ensuring the continuity of logging. This means that the central log server might not have received all the log data, even though the endpoint has no facility for knowing that it failed to be delivered successfully. The plaintext nature of `Syslog` means that a suitably positioned adversary could see the (potentially sensitive) log data as it traverses the network. `Syslog` messages may also be spoofed due to the lack of authentication, lack of encryption, and use of `UDP` as the layer 4 transport protocol.

In addition to the centralized logs, preferably at least some limited recent logs should be maintained on the endpoint system itself. Having local logs in addition to the centralized log store can help in several ways. Should the continuity of logging be disrupted, the logs might still be able to be recovered from the endpoint. If an adversary intentionally corrupts or edits the logs on the endpoint, comparing the differences can guide incident response to the adversary's activities.

### Log Retention

A retention and rotation policy for log information should be created and maintained. The retention and rotation should vary depending upon the source of the log, the type of logged information, and the practical value of the log information. Having a tremendous volume of log data that is categorically ignored provides very little value and can also make finding meaningful data in the rest of the logs more challenging. While the security value of the log information is important, log retention can also be relevant to legal or regulatory compliance matters. Legal or regulatory considerations must be accounted for when considering log retention.

### Compliance Checks

Compliance checks review an organization’s policies and procedures to verify they are compliant with relevant best practices and relevant industry and government standards. `NIST Special Publication 800-53, Revision 5—Security and Privacy Controls for Information Systems and Organizations` states the following:

> *Organizations should answer several key questions when addressing information security and privacy controls:*
>
> *   What security and privacy controls are needed to satisfy security and privacy requirements and to adequately manage mission/business risks or risks to individuals?
> *   Have the selected controls been implemented or is there a plan in place to do so?
> *   What is the required level of assurance (i.e., grounds for confidence) that the selected controls, as designed and implemented, are effective? [[5]](#Ch007_337-359_B978044318734600009X.xhtml#bb0030)

`NIST SP 800-53R5` lists the following controls that should be verified:

*   Access Control
*   Awareness
*   Audit and Accountability
*   Assessment, Authorization, and Monitoring
*   Configuration Management
*   Contingency Planning
*   Identification and Authentication
*   Incident Response
*   Maintenance
*   Media Protection
*   Physical and Environmental Protection
*   Planning
*   Program Management
*   Personnel
*   Personally Identifiable Information Processing and Transparency
*   Risk Assessment
*   System and Services Acquisition
*   System and Communications Protection
*   System and Information Integrity
*   Supply Chain Risk Management [[5]](#Ch007_337-359_B978044318734600009X.xhtml#bb0030)

Then perform the following steps: conduct a gap analysis to see if these controls (and any additional necessary controls) are in place. Then determine whether the controls are comprehensive and effective.

### Synthetic Transactions

Synthetic transactions, or synthetic monitoring, involve building scripts or tools that simulate activities normally performed in an application. The typical goal of using synthetic transactions/monitoring is to establish expected norms for the performance of these transactions. These synthetic transactions can be automated to run on a periodic basis to ensure the application is still performing as expected. These types of transactions can also be useful for testing application updates prior to deployment to ensure the functionality and performance will not be negatively impacted. This type of testing or monitoring is most commonly associated with custom developed web applications.

The Microsoft TechNet article “Monitoring by Using Synthetic Transactions” describes synthetic transactions: “For example, for a Web site, you can create a synthetic transaction that performs the actions of a customer connecting to the site and browsing through its pages. For databases, you can create transactions that connect to the database. You can then schedule these actions to occur at regular intervals to see how the database or Web site reacts and to see whether your monitoring settings, such as alerts and notifications, also react as expected” [[6]](#Ch007_337-359_B978044318734600009X.xhtml#bb0035).

### Application Security Testing

Software testing can be considered a specialized subset of security control testing, focusing on the security of an organization’s applications. There are a variety of software testing methods. In addition to testing the features and stability of the software, testing increasingly focuses on discovering specific programmer errors that could lead to vulnerabilities that risk system compromise, including a lack-of-bounds checking.
