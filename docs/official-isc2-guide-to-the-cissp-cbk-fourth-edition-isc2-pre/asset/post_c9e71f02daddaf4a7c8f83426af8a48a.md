
![](img/3be1e4f35d99b14a974b22ecf8355b5e_416_0.png)

Figure 3.19 - A generic Information Security Management System. It starts with key business drivers and determines how the organization will respond to them and how responsibility will be shared within the organization.

ISO/IEC 27001:2013 provides instructions on how to apply the ISMS concept and to construct, run, sustain, and advance information security management. The core of the standard is focused on five key areas:

- 1. General requirements of the ISMS
- 2. Management responsibility
- 3. Internal ISMS audits
- 4. Management review of the ISMS
- 5. ISMS improvement

ISO/IEC 27002:2013 is often used in tandem with 27001:2013. Rather than focus on security governance, it provides a "Code of Practice for Information Security Management," which lists security control objectives and recommends a range of specific security controls according to industry best practice. Unlike 27001:2013, this standard is more of a guideline than a standard, leaving it up to the organization to decide what level of control is appropriate, given the risk tolerance of the specific environment under the scope of the ISMS. The recommended control objectives are the "how" – they demonstrate the implementation of operational controls. A well-rounded information security program will likely include services that address each of these control objectives. ISO/IEC 27002:2013 includes the following 14 focus areas:33

- 1. Information Security Policies — Provide management guidance and support for information security.
- 2. **Organization of Information Security** — Provides a formal and defined security mechanism within an organization that includes information processing facilities and information assets accessed or maintained by third parties.
- 3. **Human Resource Security** — Provides security aspects for employees joining, moving, and leaving an organization.
- 4. **Asset Management** — Protects the organization’s assets by ensuring valuable data assets are identified and receive appropriate protection.
- 5. **Access Control** — Limits access to data, mobile communications, telecommunications, and network services, as well as detects unauthorized activities.
- 6. **Cryptography** — Provides the ability to protect the confidentiality, integrity, and authenticity of information.
- 7. **Physical and Environmental Security** — Prevents unauthorized physical access, damage, and interference to facilities and data.
- 8. **Operations Security** — Ensures the proper and secure operation of data processing facilities by protecting software, communications, data, and the supporting infrastructure.
- 9. **Communications Security** — Ensures proper data exchange between organizations.
- 10. **Information Systems Acquisitions, Development, and Maintenance** — Implements security controls into operations and development systems to ensure the security of application system’s software and data.
- 11. **Supplier Relationships** — Implements security controls to protect corporate information and assets that are accessible by suppliers and ensure that suppliers provide the agreed upon level of service and security.
- 12. **Information Security Incident Management** — Implements procedures to detect and respond to information security incidents.
- 13. **Information Security Aspects of Business Continuity Management** — Mitigates an incident’s impact on critical business systems.
- 14. **Compliance** — Ensures adherence to criminal and civil laws and statutory, regulatory, or contractual obligations, complies with organizational security policies and standards, and provides for a comprehensive audit process.

Each of these control objectives also includes numerous clauses describing specific controls along with recommendations on how they should be implemented in a typical enterprise.

Both standards can be used to guide security architecture and design. The big difference lies with certification. An organization’s ISMS may be certified by a licensed third-party assessor under ISO/IEC 27001:2013, but their control practices cannot be. The certification process allows the assessors to capture the essential elements of the organization’s ISMS and publish their findings in the form of a statement of applicability. This document is intended not only to highlight the ISMS but also to allow different organizations to compare their ISMSs. For this reason, ISO/IEC 27001:2013 certification is commonly used by service organizations to share information regarding the ISMS with current and potential customers.

## Control Objects for Information and Related Technology (COBIT)

The COBIT is a framework for IT management that was created by the Information Systems Audit and Control Association (ISACA) and the IT Governance Institute (ITGI) in the early 1990s. COBIT provides a set of generally accepted processes to assist in maximizing the benefits derived using information technology (IT) and developing appropriate IT governance. It describes security controls as recommended by the IT auditing community and is often thought of as the base minimum security services that every IT organization will need to implement. It is also frequently used as the basis for both internal and external audits.

The most recent version of COBIT (version 5) documents five principles that drive control objectives categorized in seven enablers. See Figure 3.20:

![](img/3be1e4f35d99b14a974b22ecf8355b5e_419_0.png)

Figure 3.20 - COBIT’s 5 Principles and 7 Enablers 34

COBIT is frequently used by security architects as a menu of core security services that must be implemented, and design documents will frequently use the COBIT structure to document security services. This can ease the effort required to provide audit support and allow current control gaps to be addressed as part of the architecture.

## Payment Card Industry Data Security Standard (PCI-DSS)

PCI-DSS was developed by the PCI Security Standards Council to enhance payment card data security. Much like COBIT and ISO 27002, the PCI-DSS provides the security architect with a framework of specifications to ensure the safe processing, storing, and transmission of cardholder information. PCI-DSS is focused on compliance with the standard that includes prevention, detection, and reaction to security incidents.

PCI-DSS is targeted towards merchants and service providers but is mandated for the systems involved in handling an organization’s payment card services.³⁵ Six goals are further defined through twelve broad requirements as seen in Figure 3.21.

| Goals | PCI-DSS Requirements |
|---|---|
| **Build and Maintain a Secure Network** | 1. Install and maintain a firewall configuration to protect cardholder data<br>2. Do not use vendor-supplied defaults for system passwords and other security parameters |
| **Protect Cardholder Data** | 3. Protect stored cardholder data<br>4. Encrypt transmission of cardholder data across open, public networks |
| **Maintain a Vulnerability Management Program** | 5. Use and regularly update anti-virus software or programs<br>6. Develop and maintain secure systems and applications |
| **Implement Strong Access Control Measures** | 7. Restrict access to cardholder data by business need to know<br>8. Assign unique ID to each person with computer access<br>9. Restrict physical access to cardholder data |
| **Regularly Monitor and Test Networks** | 10. Track and monitor all access to network resources and cardholder data<br>11. Regularly test security systems and processes |
| **Maintain an Information Security Policy** | 12. Maintain a policy that addresses information security for all personnel |

Figure 3.21 - **PCI DSS requirements** ³⁶

Each requirement has several sub-objectives that must be met. For example, under the category Protect Cardholder Data and Requirement 4, “Encrypt transmission of cardholder data across open, public networks,” the following objectives apply:

- **4.1 –** Use strong cryptography and security protocols such as SSL/TLS, SSH, or
