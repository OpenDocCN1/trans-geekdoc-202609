
## Explanation

Capability-based security is a concept in the design of secure computing systems. A capability (known in some systems as a key) is a communicable, unforgivable token of authority. It refers to a value that references an object along with an associated set of access rights. A user program on the capability-based operating system must use a capability to access an object. Capability-based security refers to the principle of designing user programs such that they directly share capabilities according to the principle of least privilege, and to the operating system infrastructure necessary to make such transactions efficient and secure. Although most operating systems implement a facility that resembles capabilities, they typically do not provide enough support to allow for the exchange of capabilities among possibly mutually untrusting entities to be the primary means of granting and distributing access rights throughout the system. A capability-based system, in contrast, is designed with that goal in mind. Answer options B, C, and A are incorrect. These are not correct statements about capability-based security.

## Question 48

A helpdesk manager at a financial company has received multiple reports from employees and customers that their phone calls sound metallic on the voice system. The helpdesk has been using `VoIP` lines encrypted from the handset to the `PBX` for several years. Which of the following should be done to address this issue in the future?

1. SIP session tagging and `QoS`
2. A dedicated `VLAN`
3. Lower encryption setting
4. Traffic shaping

**Answer: B**

## Question 49

A new startup company with very limited funds wants to protect the organization from external threats by implementing some type of best-practice security controls across many hosts located in the application zone, the production zone, and the core network. The 50 hosts in the core network are a mixture of `Windows` and `Linux`-based systems, used by development staff to develop new applications. The single `Windows` host in the application zone is used exclusively by the production team to control software deployments into the production zone. There are 10 `UNIX` web application hosts in the production zone which are publicly accessible. The development staff is required to install and remove various types of software from their hosts regularly while the hosts in the zone rarely require any type of configuration changes. Which of the following, when implemented, would provide the best level of protection with the least amount of disruption to staff?

1. `NIPS` in the production zone, `HIPS` in the application zone, and anti-virus/anti-malware across all `Windows` hosts.
2. `NIPS` in the production zone, `NIDS` in the application zone, `HIPS` in the core network, and anti-virus/anti-malware across all hosts.
3. `HIPS` in the production zone, `NIPS` in the application zone, and `HIPS` in the core network.
4. `NIDS` in the production zone, `HIDS` in the application zone, and anti-virus/anti-malware across all hosts.

**Answer: A**

## Question 50

An administrator is reviewing the logs and sees the following entry:

```
Message: Access denied with code 403 (phase 2). Pattern match “\bunion\b.{1,100}?\bselect\b” at ARGS:$id. [data “union all select”] [severity “CRITICAL”] [tag “WEB_ATTACK”] [tag “WASCTC/WASC-19”] [tag “OWASP_TOP_10/A1”] [tag “OWASP_AppSensor/CIE1”] Action: Intercepted (phase 2) Apache-Handler: php5-script
```

Which of the following attacks was being attempted?

1. Session hijacking
2. Cross-site script
3. SQL injection
4. Buffer overflow

**Answer: C**

# Chapter 21

# CASP+ Skill Assessment Questions and Answers

## Question 51

A University uses a card transaction system that allows students to purchase goods using their student ID.

Students can put money on their ID at terminals throughout the campus.

The security administrator was notified that computer science students have been using the network to illegally put money on their cards.

The administrator would like to attempt to reproduce what the students are doing. Which of the following is the best course of action?

1. Notify the transaction system vendor of the security vulnerability that was discovered.
2. Use a protocol analyzer to reverse engineer the transaction system's protocol.
3. Contact the computer science students and threaten disciplinary action if they continue their actions.
4. Install a `NIDS` in front of all the transaction system terminals.

**Answer: B**

## Question 52

For a company to boost profits by implementing cost savings on non-core business activities, the IT manager has sought approval for the corporate email system to be hosted in the cloud. The compliance officer has been tasked with ensuring that data lifecycle issues are taken into account. Which of the following best covers the data lifecycle end-to-end?

1. Creation and secure destruction of mail accounts, emails, and calendar items
2. Information classification, vendor selection, and the `RFP` process
3. Data provisioning, processing, in transit, at rest, and de-provisioning
4. Securing virtual environments, appliances, and equipment that handle email

**Answer: C**

## Question 53

A security administrator at a Lab Company is required to implement a solution that will provide the highest level of confidentiality possible to all data on the lab network. The current infrastructure design includes the following:

- Two-factor token and biometric-based authentication for all users
- Attributable administrator accounts
- Logging of all transactions
- Full disk encryption of all `HDDs`
- Finely granular access controls to all resources
- Full virtualization of all servers
- The use of `LUN` masking to segregate `SAN` data
- Port security on all switches

The network is protected with a firewall implementing `ACLs`, a `NIPS` device, and secured wireless access points. Which of the following cryptographic improvements should be made to the current architecture to achieve the stated goals?

1. `PKI` based authorization
2. Transport encryption
3. Data at rest encryption
4. Code signing

**Answer: B**

## Question 54

An organization has had six security incidents over the past year against their main web application. Each time the organization was able to determine the cause of the incident and restore operations within a few hours to a few days. Which of the following provides the most comprehensive method for reducing the time to recover?

1. Create security metrics that provide information on response times and requirements to determine the best place to focus time and money.
2. Conduct a loss analysis to determine which systems to focus time and money on increasing security.
3. Implement a knowledge management process accessible to the help desk and finance departments to estimate cost and prioritize remediation.
4. Develop an incident response team, require training for incident remediation, and provide incident reporting and tracking metrics.

**Answer: D**

## Question 55

A developer is coding the crypto routine of an application that will be installed on a standard headless and diskless server connected to a `NAS` housed in the data center.

The developer has written the following six lines of code to add entropy to the routine:

1. If `VIDEO` input exists, use video data for entropy
2. If `AUDIO` input exists, use audio data for entropy
3. If `MOUSE` input exists, use mouse data for entropy
4. If `KEYBOARD` input exists, use keyboard data for entropy
5. If `IDE` input exists, use `IDE` data for entropy
6. If `NETWORK` input exists, use network data for entropy

Which of the following lines of code will result in the strongest seed when combined?

1. 2 and 1
2. 3 and 5
3. 5 and 2
4. 6 and 4

**Answer: D**
