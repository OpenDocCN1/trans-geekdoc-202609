
**8.24** The focus of the Report was the introduction of a Code of Practice for Industry on Consumer IoT (‘The Code’). Consumer IoT is defined as ‘consumer purchased “off the shelf” IoT devices; IoT devices used and installed “in the home” and the associated services linked to these devices’.

**8.25** The Code is designed to be applied throughout the IoT sector, specifically for device manufacturers, IoT service providers, mobile application developers, and retailers. The Code is designed to improve the security of consumer IoT products and associated services, and it provides practical guidance, listed in order of importance, for the IoT sector to apply.

**8.26** A summary of the Code is provided below. These steps should be considered by any company supplying IoT devices, with the top three addressed as a matter of priority:

## 8.27 The Internet of Things

| No. | Principle | Description |
|---|---|---|
| I. | **No default passwords** | All IoT device passwords must be unique and resettable, and suppliers must avoid universal default values. The Mirai malware (botnet) utilised common default credentials (universal usernames and passwords: admin/admin), which consumers often failed to change. Device manufacturers must ensure that each device is supplied with a unique default password. |
| II. | **Implement a vulnerability disclosure policy** | All companies that provide internet-connected devices and services must provide a public point of contact as part of a vulnerability disclosure policy in order that security researchers and others are able to report issues. Disclosed vulnerabilities should be acted on in a timely manner. |
| III. | **Keep software updated** | All software components in internet-connected devices should be securely updateable. Updates must be timely and not impact on the functioning of the device. The Code requires that suppliers publish an ‘end-of-life’ policy which states the minimum period for which updates will be received. An explanation must be provided for the reason why updates will not be provided. |
| IV. | **Securely store credentials and security-sensitive data** | Any credentials must be stored securely within services and on devices. Hardcoded credentials in device software, which can be easily discovered through reverse engineering, are not acceptable. Security-sensitive data should be stored securely.36 |
| V. | **Communicate securely** | Appropriate encryption should be used for data relevant to the security of the device. |
| VI. | **Minimise exposed attack surfaces** | Processor, user or program access should be restricted to only the information necessary for the legitimate purpose, and no more (‘Principle of least privilege’). Unnecessary code or hardware which exposes the device should be minimised. |
| VII. | **Ensure software integrity** | The consumer, or a company administrator, should be notified if an unauthorised change or reboot is detected. |
| VIII. | **Ensure that personal data is protected** | The processing of personal data must be in accordance with data protection law. Within the UK, this will be in accordance with the Data Protection Act 2018. Within the EU, the General Data Protection Regulation (GDPR) will apply. |
| IX. | **Make systems resilient to outages** | The IoT device or service should continue to function despite operational issues. |
| X. | **Monitor system telemetry37 data** | All telemetry data, such as usage and measurement data, should be monitored for security anomalies (but only if this data is collected). |
| XI. | **Make it easy for consumers to delete personal data** | Consumers should be provided with clear instructions which allow for the deletion of their personal data. |
| XII. | **Make installation and maintenance of devices easy** | Installation and maintenance should require minimal steps and should follow best security practice. |
| XIII. | **Validate input data** | Data input via user interfaces and transferred via application programming interfaces (‘APIs’) or between networks in services and devices must be validated. |

29. https://assets.publishing.service.gov.uk/government/uploads/system/uploads/attachment_data/file/971440/Code_of_Practice_for_Consumer_IoT_Security_October_2018_V2.pdf.

30. https://assets.publishing.service.gov.uk/government/uploads/system/uploads/attachment_data/file/686089/Secure_by_Design_Report_.pdf, Annex 8, 8.3.

31. ‘The entity that creates an assembled final internet-connected product. A final product may contain the products of many other different manufacturers.’ Ibid, 4.5.

32. ‘Companies that provide services such as networks, cloud storage and data transfer which are packaged as part of IoT solutions. Internet-connected devices may be offered as part of the service.’ Ibid, 4.5.

33. ‘Entities that develop and provide applications which run on mobile devices. These are often offered as a way of interacting with devices as part of an IoT solution.’ Ibid, 4.5.

34. ‘The sellers of internet-connected products and associated services to consumers.’ Ibid, 4.5.

35. An equivalent European standard ‘ETSI EN 303 645’ has been adopted and provides similar guidance.

36. National Institute of Standards and Technology (NIST) Special Publication 800-63B: 'Digital Identity Guidelines, Authentication and Lifecycle Management, 2017' suggests that best practice includes the use of cryptographic keys and initialisation vectors, with credentials stored within a Trusted Execution Environment (see: https://pages.nist.gov/800-63-3/sp800-63b.html).

37. In this context, 'telemetry' means wireless data transfer. An IoT device which suddenly has a spike in data transfer may have been hacked as a result of the external threat gaining access to the device or subsequently using the device. The Code requires that this telemetry is monitored to detect these spikes, but only if this data is already being collected. The Code does not require additional monitoring, as this may be contrary to the privacy of the user.

8.28 The Code remains and non-compliance is generally difficult to enforce. The National Cyber Security Centre (‘NCSC’), the centrepiece of the National Cyber Security Strategy, provides advice and support for the public and private sector in how to avoid computer security threats, but it currently has no enforcement function (see below). It is unlikely that the NCSC’s parent organisation, GCHQ, would ever seek to enforce a voluntary Code. GCHQ’s capabilities include: the collection and analysis of communications and data; and a range of online strategies to cause real-world effect. GCHQ does not employ enforcement officers, for example, to physically enter company premises or to ensure real-world compliance with a voluntary Code.

### NCSC: Practical Steps to Avoid a Ransomware Attack

The National Cyber Security Centre (NCSC) provides a range of advice and guidance relevant to securing Chambers’ systems under their Cyber Essentials programme. Cyber Essentials also provides two forms of certification – Cyber Essentials and Cyber Essentials Plus – which are designed to provide peace of mind that cyber defences are in place to protect against the vast majority of common cyber-attacks.

The following five points are vital to ensure that hackers are not simply being invited to walk through an open-door:

- 1. Use a firewall to secure your internet connection

A ‘firewall’ is an area between your computer, or computers, and your internet connection in which incoming traffic, whether emails or digital downloads, can be analysed and assessed before being permitted to enter the network.

Firewalls can be placed at various points within a network:

- Boundary firewalls are common for most organisations and will protect the whole network.
- Individual firewalls should be considered by each member of chambers for their internet connected personal laptops or computers. These will normally be included within the operating system and can be accessed through ‘Settings’.
- Router firewalls can also provide boundary protection but are not always available. Chambers will need to talk to their internet service providers about the specific models being used.
