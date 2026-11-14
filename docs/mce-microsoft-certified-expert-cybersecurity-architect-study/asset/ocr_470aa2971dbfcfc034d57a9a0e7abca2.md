Detecting, prioritizing, and triaging potential attacks are the responsibilities of the security operations team (also called the security operations center or SecOps). By eliminating false positives and focusing on actual attacks, these operations reduce the mean time it takes to resolve actual incidents.

The central SecOps team monitors telemetry data related to security and investigates security breaches. Communicating, investigating, and hunting activities must be aligned with the application team. Microsoft Cybersecurity Architects must follow the following general best practices when designing SOC operations.

Implement the following NIST cybersecurity framework functions as part of your operations:

+   Identify: Establish an organizational understanding of cybersecurity risk to systems, people, assets, data, and capabilities.

+   Protect: Ensure critical services are delivered by developing and implementing appropriate safeguards.

+   Detect: Analyze the system to detect the presence of adversaries. Neutralizing an adversary quickly is possible if one has been detected. The chances of them conducting attacks and reaching sensitive systems should be reduced.

+   Respond: By investigating it promptly, identify whether it is a false alarm or an actual attack. Respond quickly to an alert. As defenders triage false positives, detected adversaries should not be ignored.

+   Recover: Restore confidentiality, integrity, and workload availability during and after an attack.

Based on the NIST framework core, SOC results can be achieved through specific activities and guidance.

For more information, refer to the following link:

nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.04162018.pdf

As your system matures, actively hunt for adversaries. If you make this effort, an adversary with high skill levels will have less time to operate in the environment.

# Microsoft SOC Function for Azure Cloud

Microsoft defines that SOC functions need to address three critical objectives: incident management, incident preparation, and threat intelligence. Let's take a high-level view of each one of them.

+   Incident management: Protect the environment from active attacks, including the following:

+   Responding to detected attacks in a reactive manner as per the agreed service level agreement.

+   Detecting attacks proactively may elude traditional threat detection methods.

+   Security incidents have legal, communication, and other business consequences that need to be managed.