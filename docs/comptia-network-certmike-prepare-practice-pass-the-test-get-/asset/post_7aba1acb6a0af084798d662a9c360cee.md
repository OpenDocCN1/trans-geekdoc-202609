
[content]
# Risk Management

The problem with local authentication is that each system requires its own set of user accounts. When users want to change their passwords, someone must change them on every system where each user has an account. Typically, local authentication functions only as a fallback that allows users to log on to their computers, when the network is down.

# 802.1X

802.1X is a standard published by the IEEE defining an authentication method for controlling access to networks by manipulating port security settings. An 802.1X transaction involves three parties: a switch, an authenticator, and an authentication server.

The supplicant, which is a user or device requesting access to a resource, sends an access request and its credentials to the authenticator, which is typically a switch, but can also be a wireless access point or a virtual network (VPN) server. The authenticator then forwards the credentials to an authentication server, which typically runs TACACS+ or RADIUS and verifies the credentials. If the authentication is successful, the authentication server informs the authenticator, which grants the requested access.

One of the main advantages of 802.1X is that it enables switches and other devices to offload authentication processing to a dedicated authentication server, lessening the burden on the switches themselves.

# Extensible Authentication Protocol

Extensible Authentication Protocol (EAP) is not really a protocol, but rather a framework that extends the 802.1X framework to support a variety of authentication mechanisms, including smart cards, fingerprints, and other forms of biometrics, as well as passwords. There are many protocols that use the EAP framework, including Protected Extensible Authentication Protocol (PEAP), which encapsulates EAP within an encrypted TLS tunnel, and Extensible Authentication Protocol-Transport Layer Security (EAP-TLS), used on wireless networks.

# RISK MANAGEMENT

In IT, risk management is the process of identifying potential dangers to the network, prioritizing those dangers, and taking steps to minimize or eliminate them. An enterprise network should have a formal risk management program in place that performs regular assessments of the network's security posture.

One of the primary elements of a comprehensive risk management program is to perform security risk assessments on a regular basis. These are tests to evaluate the network's resistance to known risks, as with the following:

- Threat Assessment: Administrators must remain aware of the new threats that appear regularly and the dangers they pose to the network. There are many websites that track the latest threats and describe their characteristics.

- Vulnerability Assessment: A scan, typically performed by a third-party software, which evaluates the potential vulnerabilities of a network by identifying open ports, missing software updates, configuration anomalies, and other weaknesses.

- Penetration Testing: A test in which a third party—acting as an intruder—attempts to exploit the weaknesses in the network’s security posture under ordinary operating conditions and access its protected resources. In many cases, for a more realistic assessment, the test is provided with no prior knowledge of the network and the company’s IT personnel are not told that the test is pending.

- Posture Assessment: Often occurring with a penetration test, a posture assessment is a test of how the IT department reacts to a network attack.

- Business Risk Assessment: Beyond the existence of vulnerabilities, a business risk assessment evaluates vulnerabilities with regard to the dangers they pose to the organization’s business interests. This enables the administrators to prioritize the vulnerabilities and refine their reaction plans.

- Process Assessment: An examination, with an eye to network security, the business processes that company workers perform on a regular basis.

- Vendor Assessment: An examination of the security posture of the organization’s vendors and other business partners, including what access they have to the organization’s network and data resources as well as their own security procedures.

# SIEM

Security Information and Event Management (SIEM) is an umbrella term used for products that combine the functions of security information management (SIM), which provides long-term log storage and analysis, and security event management (SEM), which provides real-time monitoring of network devices. Available as software, hardware, or a managed service, an SIEM product can gather logs from various network devices, such as firewalls and switches; collate the information; and then evaluate it by comparing the data with known threat behaviors. If the SIEM product detects a threat, it can typically notify an administrative contact in various ways. Some products can even take action to remediate a threat.

# CERTMIKE EXAM ESSENTIALS

- The CIA triad defines the three basic security goals for an enterprise network: confidentiality, integrity, and availability.
- Defense in depth is a security principle that calls for multiple layers of security between the protected material and its potential threats. Some of the associated concepts are network segmentation enforcement, perimeter networks, NAC, and honeypots.
- Authentication is one of the most critical security elements in an enterprise network. It can involve many different concepts and technologies, including multifactor authentication, AAA, single sign-on, LDAP, Kerberos, 802.1X, and EAP.

# Practice Question 1

Ralph is designing the network for his company's new branch office. The office will be running a custom application that frequently needs updating. Ralph's director has instructed him to set up the network so that users cannot connect to it unless their workstations have been updated with the latest patches for custom application. Which of the following technologies must Ralph use to achieve this goal?

- A. LDAP
B. SIEM
C. RADIUS
D. NAC

# Practice Question 2

Alice is working the IT help desk when she receives a call from the Director of Human Resources, informing that an employee had just been terminated and had to be escorted out of the building by Security. The director instructed her to disable all of the employee's accounts, change the passwords for all network devices to which the employee had access, and have the data center rekeyed. Alice was surprised to receive these instructions because company employees had been terminated before these precautions.

Which of the following terms best describes the director's specific concern?

- A. Social engineering
B. Internal threats
C. War driving
D. External threats

# Practice Question 1 Explanation

A. is incorrect because Lightweight Directory Protocol (LDAP) is used for Active Directory communication, not for enforcing configuration standards.

B. is correct because Security Information and Event Management (SIEM) is a security product that provides long-term log storage and analysis and real-time monitoring of network devices.

C. is incorrect because Remote Authentication Dial-In Service (RADIUS) is a centralized authentication, authorization, and does not enforce configuration standards.

D. is correct because Network Access Control (NAC) is a technology that enforces configuration standards that systems must meet before they can connect to the network.

Correct Answer: D, NAC

# Practice Question 2 Explanation

A. is incorrect because social engineering is a form of attack in which an innocent user is persuaded by an attacker to provide sensitive information via email or telephone.

B. is correct because the director's concern is that the disgruntled employee might take advantage of access to company resources to sabotage the network. When individuals take advantage of information gathered during their employment, it is called an internal threat.

C. is incorrect because war driving is an attack method that consists of driving around a neighborhood with a computer scanning for unprotected wireless networks.

D. is incorrect because an external threat is originating from a non-employee.

Correct Answer: B, Internal threats
[/content]
