
In addition, consideration should be given to the development of procedures that address SeCM template use; steps for creation and content of baseline configurations; the prioritization, testing, approval, and integration of patches; help desk change request handling; integration of change management throughout the systems development life cycle; the labeling and destruction of media; and how monitoring should be accomplished to track adherence with the configuration and change management process.

Early on, we presented the security configuration management concept, and we have discussed it in a few different ways such as in relation to computer security. To be clear, SeCM is part of CM, but CM is concerned more comprehensively with performance, and the functional and physical integrity of systems, applications, networks, and information environments relative to a defined “secure state” known as the baseline configuration. In this sense, it goes beyond cybersecurity to include information security as well as natural and other disasters.

SeCM is an extension of CM as you now know. Remember that CM is the management of the integrity of functions and features by controlling changes made to hardware, software, and information throughout the life of an information system. Primary components in the implementation of CM include the protection and management of policies, practices, and processes that ensure conformance and consistency of information and systems through proper governance. It represents the foundations of two key concepts: compliance and auditing.

### 11.4.2 CM and Computer Security Procedures and Frameworks

Let’s refresh our memories and pull all this together from the previous chapters to highlight the importance of configuration management. Recall that configurations are how systems are set up, installed, connected, and so on and involve policies, models, defined stances, and regulatory and governance aspects. The area of CM in security borrows from the software configuration management (SCM) processes defined by Booch and Rumbaugh and others in which the requirements and attributes for applications are defined, and then systematic controls over changes are utilized. This is done to maintain software integrity and traceability throughout the software development life cycle. To accomplish this, (1) a configuration’s stable base must be determined, (2) a control process must be put into place, (3) an accounting and logging mechanism or mechanisms must be established, and (4) an auditing system must be enabled.

For example, CM may need a set of policies, models, and defined stances for a gateway that connects a DMZ to the Internet, which must be monitored and audited to ensure that it stays within the guidelines set and meets specific measures and metrics outlined by the policies and conformance criteria. As such, many CM aspects are addressed under various compliance criteria, including the Capability Maturity Model for integration (CMMi), the ISO 9000 family of standards, Six Sigma, COBIT, and the Information Technology Infrastructure Library (ITIL) that we covered previously. The key to CM is known as traceability, where a change can be traced through a “chain of custody” back to its source. Earlier, we covered key legal, organizational, and administrative aspects of security, we introduced how some of the major technologies work, and we covered a broad swath of how computer, network, and information security is implemented. These topics are also important here from an operational and managerial standpoint.

Changes to the configuration must be (1) proposed, (2) reviewed, (3) approved, (4) tracked, and (5) frozen into a new baseline. As imagined then, configuration management is a vast concept that incorporates the facilities used in production, operations, compliance, and auditing. In this context, compliance is composed of the processes and procedures and rules used to conform to a security policy or a regulation. Auditing is the evaluation and verification of compliance—in other words, audits assess compliance with rules, regulations, policies, procedures, and laws. To help managers with this expansive responsibility, configuration management frameworks exist.

Most management frameworks require the establishment and management of appropriate configurations to the information system. ITIL, COBIT, and NIST SP 800-53 all recognize the importance of change and configuration management to both the operational and security management of information systems, although as we stated earlier, it is conspicuously absent in some of the standards such as ISO 27002. Still, this is critical in managing systems securely. Behr et al.[⁵](#9781284211658_CH11_08.xhtml#c11-bib0005) examined high-performing IT organizations, and they defined “high-performing” as consisting of the following characteristics:

1.  High mean time between failures and low maximum time to repair

2.  Early and consistent integration of security controls into IT operational processes

3.  Low numbers of repeat negative audit findings with less staff time devoted to compliance

4.  High efficiency related to server-to-system-administrator ratios and low amounts of unplanned work

Risk management and good governance dictate that, while little can usually be done with respect to the threat environment, organizations can manage the vulnerabilities in their systems relatively effectively. As stated in Johnson et al., “Using configuration management to gain greater control over and ensure the integrity of IT resources facilitates asset management, improves incident response, help desk, disaster recovery and problem solving, aids in software development and release management, enables greater automation of processes, and supports compliance with policies and preparation for audits.”[⁴](#9781284211658_CH11_08.xhtml#c11-bib0004)

### 11.4.3 Security Management Planning—System Level

At the system level, the CI components involved must be examined both individually and as a group in order to develop a specific system SeCM plan. Again, using National Institute of Standards and Technology (NIST) standards, this plan should include the following recommendations:

*   A brief description of the target information system(s)

*   Information system component inventory

*   Information system configuration items

*   Rigor to be applied to managing changes to configuration items (i.e., based on the impact level of the information system)

*   Identification of the roles and responsibilities

*   Identification and composition of the group or individual(s) that consider change requests

*   Configuration change control procedures to be followed (including references to organization-wide procedures)

*   Identification of the location where SeCM artifacts (change requests, approvals, etc.) are maintained (e.g., media libraries) with overrides of location of SeCM artifacts (if applicable)

*   Access controls employed to control changes to configurations, with overrides of configuration change control procedures (if applicable)

*   Description of secure configuration standards to be used as a basis for establishing approved configuration baselines for the information system

*   Deviations from secure configuration standards for configuration items including justifications

*   Descriptions of approved baseline configurations for the information system[⁴](#9781284211658_CH11_08.xhtml#c11-bib0004)

The baseline configuration will often include the following:

*   Configuration settings (i.e., the set of parameters that can be changed in a hardware or software component of an information system to affect its security posture) including, but not limited to:

    *   OS and application features (enabling or disabling depending on the specific feature)

    *   Services and ports (e.g., automatic updates, DNS over port 53)
