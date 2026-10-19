
## How to Implement This Control

The security professional may also want to delve deeper into the specifics of how to implement and manage one or more of the aspects of the control discussed above. The following resources will assist in that effort:

- https://buildsecurityin.us-cert.gov/
- https://www.owasp.org/index.php/Main_Page

## Collect Security Process Data

Information security continuous monitoring (ISCM) is defined as maintaining ongoing awareness of information security, vulnerabilities, and threats to support organizational risk management decisions. Any effort or process intended to support ongoing monitoring of information security across an organization must begin with senior leadership defining a comprehensive ISCM strategy encompassing technology, processes, procedures, operating environments, and people. This strategy:

- Is grounded in a clear understanding of organizational risk tolerance and helps officials set priorities and manage risk consistently throughout the organization;
- Includes metrics that provide meaningful indications of security status at all organizational tiers;
- Ensures continued effectiveness of all security controls;
- Verifies compliance with information security requirements derived from organizational missions/business functions, federal legislation, directives, regulations, policies, and standards/guidelines;
- Is informed by all organizational IT assets and helps to maintain visibility into the security of the assets;
- Ensures knowledge and control of changes to organizational systems and environments of operation; and
- Maintains awareness of threats and vulnerabilities.

An ISCM program is established to collect information in accordance with pre-established metrics, utilizing information readily available in part through implemented security controls. Organizational officials collect and analyze the data regularly and as often as needed to manage risk as appropriate for each area of the enterprise. This process involves the entire organization, from senior leaders providing governance and strategic vision to individuals developing, implementing, and operating individual systems in support of the organization’s core missions and business processes. Subsequently, determinations are made from an organizational perspective on whether to conduct mitigation activities or to reject, transfer, or accept risk.

Organizations’ security architectures, operational security capabilities, and monitoring processes will improve and mature over time to better respond to the dynamic threat and vulnerability landscape. An organization’s ISCM strategy and program are routinely reviewed for relevance and are revised as needed to increase visibility into assets and awareness of vulnerabilities. This further enables data-driven control of the security of an organization’s information infrastructure and increases organizational resilience.

Organization-wide risk monitoring cannot be efficiently achieved through manual processes alone or through automated processes alone. Where manual processes are used, the processes are repeatable and verifiable to enable consistent implementation. Automated processes, including the use of automated support tools (e.g., vulnerability scanning tools, network scanning devices), can make the process of continuous monitoring more cost-effective, consistent, and efficient. Many of the technical security controls defined in NIST Special Publication (SP) 800-53 Rev. 4, Security Controls for Federal Information Systems and Organizations, are good candidates for monitoring using automated tools and techniques.⁵ Real-time monitoring of implemented technical controls using automated tools can provide an organization with a dynamic view of the effectiveness of those controls and the security posture of the organization. It is important to recognize that with any comprehensive information security program, all implemented security controls, including management and operational controls, must be regularly assessed for effectiveness, even if the monitoring of such controls cannot be automated or is not easily automated.

The process for developing an ISCM strategy and implementing an ISCM program is as follows:

- Define an ISCM strategy based on risk tolerance that maintains clear visibility into assets, awareness of vulnerabilities, up-to-date threat information, and mission/business impacts.
- Establish an ISCM program determining metrics, status monitoring frequencies, control assessment frequencies, and establish an ISCM technical architecture.
- Implement an ISCM program and collect the security-related information required for metrics, assessments, and reporting. Automate collection, analysis, and reporting of data where possible.
- Analyze the data collected and report findings, determining the appropriate response. It may be necessary to collect additional information to clarify or supplement existing monitoring data.
- Respond to findings with technical, management, and operational mitigating activities or acceptance, transference/sharing, or avoidance/rejection.
- Review and update the monitoring program, adjusting the ISCM strategy and maturing measurement capabilities to increase visibility into assets and awareness of vulnerabilities, further enable data-driven control of the security of an organization’s information infrastructure, and increase organizational resilience.

Security architects, security professionals and security practitioners all need to work together to play a part in determining what metrics are to be used to evaluate and control ongoing risk to the organization. Metrics, which include all the security-related information from assessments and monitoring produced by automated tools and manual procedures, are organized into meaningful information to support decision-making and reporting requirements. Metrics should be derived from specific objectives that will maintain or improve security posture. Metrics are developed for system-level data to make it meaningful in the context of mission/business or organizational risk management.

Metrics may use security-related information acquired at different times and therefore with varying levels of data latency. Metrics may be calculated from a combination of security status monitoring, security control assessment data, and from data collected from one or more security controls. The following shows some examples of metrics:

- The number and severity of vulnerabilities revealed and remediated
- Number of unauthorized access attempts
- Configuration baseline information
- Contingency plan testing dates and results
- The number of employees who are current on awareness training requirements
- Risk tolerance thresholds for organizations
- The risk score associated with a given system configuration

The security professional needs to be aware of the fact that metrics are fundamentally flawed without assurance that all security controls are implemented correctly. Metrics are defined or calculated in accordance with output from the security architecture. Collecting metrics from a security architecture with security controls that have not been assessed is equivalent to using a broken or uncalibrated scale. The interpretation of metrics data presumes that controls directly and indirectly used in the metric calculation are implemented and working as anticipated. If a metric indicates a problem, the root cause could be any number of things. Without fundamental assurance of correct implementation and continued effectiveness of security controls that are not associated with the metric, the root cause analysis is going to be hampered, and the analysis may be inappropriately narrowed to a predetermined list, causing the security practitioner to overlook the true problem.

According to NIST SP 800-137, Information Security Continuous Monitoring (ISCM) for Federal Information Systems and Organizations, the security practitioner needs to take the following criteria into consideration when establishing monitoring frequencies for metrics or assessment frequencies for security controls: ⁶

- **Security Control Volatility –** Volatile security controls are assessed more frequently, whether the objective is establishing security control effectiveness or supporting calculation of a metric. Controls in the NIST SP 800-53 Configuration Management (CM) family are a good example of volatile controls. Information system configurations typically experience high rates of change. Unauthorized or unanalyzed changes in the system configuration can render the system vulnerable to exploits. Therefore, corresponding controls such as CM-6, Configuration Settings, and CM-8, Information System Component Inventory, may require assessment that is more frequent and monitoring, preferably using automated, SCAP-validated tools that provide alerts and status on demand. Conversely, controls such as PS-2, Position Categorization, or PS-3, Personnel Screening, (from the NIST SP 800-53 Personnel Security family of controls) are not volatile in most organizational settings. They tend to remain static over long periods and would therefore typically require less frequent assessment.
- **System Categorizations/Impact Levels –** In general, security controls implemented on systems that are categorized as high-impact are monitored more frequently than controls implemented on moderate-impact systems, which are in turn monitored more frequently than controls implemented on low-impact systems.
- **Security Controls or Specific Assessment Objects Providing Critical Functions –** Security controls or assessment objects that provide critical security functions (e.g., log management server, firewalls) are candidates for more frequent monitoring. Additionally, individual assessment objects that support critical security functions are deemed critical to the system (in accordance with the Business Impact Analysis).⁷
