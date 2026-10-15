
The managed or enterprise environment is what one would normally find in a larger organization with a centralized IT staff. Checklists for these environments are designed for advanced end users or IT professionals to use in different enclaves to provide enterprise functionality while typically centrally managing the policies related to the IT assets. While the typical managed environment tends to be more restrictive than the standalone environment, including the provision of multiple layers of defense known as defense in depth, they also tend to have greater control over and insight into the flow of information in their environment. As specified in Quinn, et al.,[⁷](#9781284211658_CH11_08.xhtml#c11-bib0007) common security practices that relate to the enterprise environment are as follows:

*`Segmented internal networks`* with internal firewalls and other defense-in-depth techniques

*`Centralized management`* of systems with highly restricted local user access

*`Centralized management`* of security-related applications such as antivirus software

*`Automated installation`* of system and application patches and updates

*`Restricted access`* to printer and multifunction devices and their features

*`Centralized systems`* for log monitoring

*`Centralized backup and recovery facilities`

The specialized cases of the managed environment—SSLF, legacy, and FDCC—are also covered under the NCP. Specialized Security-Limited Functionality custom environments are ones that tend to have security requirements more restrictive than those of other systems in the managed environment, causing security to be of a higher concern and to take a priority over functionality in these systems. Examples of SSLF might include highly sensitive and proprietary organizational information, such as geologic surveys for a “gas and oil” company or a “human resources” computer that contains personally identifiable information on the employees of the organization. The impact of a security incident involving these systems would typically be much greater than for that of other systems in the enterprise. The following general security practices and controls are recommended by NIST for these systems:

*`Systems should generally process as few types of data as possible`* (e.g., do not combine multiple server applications on the same system).

*`Systems should be stripped of all unnecessary services and applications`.

*`If possible`,* host-based firewall applications should be used.

*`Systems should have as few users as possible`.

*`The strongest possible authentication should be used`* (e.g., authentication token, biometrics, and smart cards).

*`Remote administration or access should be restricted`; if used, connections should be encrypted.

*`Security-related operating system and application patches and updates should be tested and applied as soon as possible`.

*`Systems should be placed behind firewalls and other network security devices that restrict access and filter unnecessary protocols`.

*`Intrusion detection logs and other logs should be monitored frequently`.

*`Vulnerability assessment tools should be run against the systems frequently`.

*`System administrators should be highly skilled in the appropriate technologies`.[⁷](#9781284211658_CH11_08.xhtml#c11-bib0007)

### 11.4.6 Managed Legacy Systems

Legacy systems present special configuration challenges, as they often cannot support many advanced or modern security controls. As such, compensating security controls must be identified to account for the current or potential vulnerabilities inherent in the system. An example would be the use of proxies as discussed in the chapter on computer security. The final special case in the NCP is the FDCC. This is a custom desktop environment that is specified by the U.S. Office of Management and Budget (OMB) for federal managed desktops. The checklists that are part of the NCP are specific to a listed IT product and are broadly divided into automated and nonautomated groups. An automated checklist is written in such a way that facilitates implementation by a script or other software product. NIST is encouraging the use of the Security Content Automation Protocol (SCAP) in developing automated checklists to facilitate a standardized and open means that multiple vendors can use for IT product hardening. The repository (found at https://nvd.nist.gov/ncp/repository) can be searched by a variety of fields, including tier, product name, product category, developer (authority), or keyword. Tiers refer to the degree of automation that the checklist provides. Tier I checklists are prose-based, narrative descriptions of how to secure an asset, while Tier IV are machine-readable checklists that can be automatically processed and map the low-level configurations to higher-level security framework specifications, such as those discussed previously.

### 11.4.7 Extended Guidelines

To this point, we have covered a lot about configuration management and focused on criteria such as the NIST checklists for both government and industry; however, some special sets of guidelines are specifically designed for the government sector because in many cases, they must conform to very strict and regulated criteria. Also a vast number of other sets of criteria and checklists can be used for specialized industries. Some of these include specifications defined by the National Security Agency (NSA) or the Defense Advanced Research Projects Agency (DARPA) or even entities associated with DARPA, such as the Department of Defense. In other cases, there is a crossover from government to industry, for example, in the case of government contractors or suppliers.

#### 11.4.7.1 DISA STIGs

The Defense Information Systems Agency (DISA), through the Information Assurance Support Environment, provides a series of baseline system configurations known as Security Technical Implementation Guides (STIGs). These guides are the configuration standards for U.S. Department of Defense information systems and, together with their security checklists, provide a great foundation for securely configuring systems. While some of the STIGs and compliance scripts are not available for general public release, most are available from their website. STIGs cover a wide variety of configuration items and provide an auditable means of ensuring systems are minimally protected against the most common threats. In general, STIGs will include an explanation for the guidance as well as the recommended settings, with the vulnerabilities represented in the configuration checklist divided into three categories related to the associated risk.

Category I vulnerabilities are ones “that allow an attacker immediate access into a machine, allow superuser access, or bypass a firewall,” Category II vulnerabilities are ones “that provide information that has a high potential of giving access to an intruder,” and Category III vulnerabilities “provide information that potentially could lead to compromise.”[⁸](#9781284211658_CH11_08.xhtml#c11-bib0008) The checklists that often accompany the STIGs will include more specific information on exactly how to configure the asset, often including specific commands to enter. While manually configuring a system to a STIG specification can be done, it is often accomplished through the use of configuration scripts and tools that implement the STIG specifications.
