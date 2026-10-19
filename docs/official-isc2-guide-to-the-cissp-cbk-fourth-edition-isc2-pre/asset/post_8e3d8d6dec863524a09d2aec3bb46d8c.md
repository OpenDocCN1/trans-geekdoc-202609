
trusted and less trusted environments. Such boundaries may be deployed within the enterprise network using firewalls, routers, proxies, and other technologies to control the boundary between more trusted and less trusted network segments. Similar technologies can be deployed within individual systems. For example, the boundaries between kernel functions and end-user processes may be enforced through common anti-malware systems, ring protection, and various process isolation techniques.

Security operations will focus on ensuring that these technologies have been deployed effectively and monitoring their use over time to ensure that they are still effective. Changes to firewall rules and router Access Control Lists (ACLs) need to be carefully examined to determine if they accomplish their intended purpose without affecting other rules or the stability of the platform. Secured systems will need to be examined regularly to ensure that system boundaries remain intact.

## Detection

Intrusion detection and prevention systems are used to identify and respond to suspected security-related events in real time or near real time. Intrusion detection systems (IDS) will use available information to determine if an attack is underway, send alerts, and provide limited response capabilities. Intrusion prevention systems (IPS) will use available information to determine if an attack is underway, send alerts, but it will also block the attack from reaching its intended target.

Network-based intrusion systems focus on the analysis of network traffic, while host-based intrusion systems focus on audit logs and processes inside a single system.

The distinction between IDS and IPS is very important because it materially affects both how the system must be deployed and its effect on the systems it is monitoring. If an IDS is used, it may be deployed out-of-band, meaning that it is not deployed in the middle of the communications path, and will not affect normal processing or cause latency. Any attacks, however, will likely reach their intended target. If an IPS is used, it must be deployed in-line (also known as in-band), meaning that it is deployed in the middle of the communications path. Because it is in-line, it will cause some latency and slow down normal processing to a slight extent. Detected attacks, however, will not likely reach their intended targets. On many modern systems, both IDS and IPS techniques can be used within the same device, allowing the security practitioner to decide whether to use one technique or the other.

Intrusion systems use a number of techniques to determine whether an attack is underway:

- **Signature- or Pattern-Matching systems —** Examine the available information (logs or network traffic) to determine if it matches a known attack.
- **Protocol Anomaly-Based systems —** Examine network traffic to determine if what it sees conforms to the defined standard for that protocol, for example, as it is defined in a Request for Comment or RFC.
- **Statistical-Anomaly-Based systems —** Establish a baseline of normal traffic patterns over time and detect any deviations from that baseline. Some also use heuristics to evaluate the intended behavior of network traffic to determine if it intended to be malicious or not. Most modern systems combine two or more of these techniques together to provide a more accurate analysis before it decides whether it sees an attack or not.

In most cases, there will continue to be problems associated with false-positives as well as false-negatives. False-positives occur when the IDS or IPS identifies something as an attack, but it is in fact normal traffic. False-negatives occur when the IPS or IDS fails to interpret something as an attack when it should have. In these cases, intrusion systems must be carefully "tuned" to ensure that these are kept to a minimum.

An IDS requires frequent attention; it requires the response of a human who is knowledgeable enough with the system and types of normal activity to make an educated judgment about the relevance and significance of the event. Alerts need to be investigated to determine if they represent an actual event or if they are simply background noise.

## Anti-Malware Systems

Today, anti-malware systems may be deployed at various points throughout the enterprise. They are installed on individual hosts, on systems such as email servers, and even at key points in the network in email and Web gateways as well as Unified Threat Management (UTM) devices, which combine anti-malware with other functions (such as firewall, intrusion detection/prevention, and content filtering).

To remain effective, anti-malware solutions require continual updates and must be monitored to ensure they are still active and effective. Each implementation should be monitored to ensure that updates are received and active. Likewise, the anti-malware engines should be configured to take advantage of automatic scanning for new media and email attachments. Scanning should be scheduled and accomplished on a regular basis. It is best for the scanning to be done automatically during nonpeak usage times.

## Security Event Information Management (SEIM)

Few solutions tools are more important to security operations than one that provides the ability to get a view into security-related events in real time. System audit logs collect valuable information on the operation of the system, but logs do not alert security professionals. They also do not provide ways to collate audit logs across multiple systems.

Security-related audit logs will typically log access attempts (including successes and failures), the use of privileges, service failures, and the like. Even on a single system, these logs can get to be very large. They may need to be tuned to ensure that you are only collecting the logs that you want using appropriate clipping levels. For example, successful login attempts may not be required for analysis and may be filtered out.

One disadvantage of system logs is that they provide a view into that single system. They do not provide a view into events that may be affecting multiple systems or where multiple systems have some information that may be required to detect an incident and track it back to its sources. Security Event Information Management (SEIM) solutions products are intended to provide a common platform for log collection, collation, and analysis in real time to allow for more effective and efficient responses.

They can also provide reports on historical events using log information from multiple sources.

Log management systems are similar: They also collect logs and provide the ability to report against them, although their focus tends to be on historical analysis of log information rather than real time analysis. They may be combined with SEIM solutions to provide both historical and real time functions.

In both cases, log information must be carefully managed, and security operations must maintain a disciplined practice of log storage and archiving. For most SEIM or log management systems, there is a practical limit to the amount of information they can analyze at once or generate reports against. For most systems, only a fraction of the logs will be stored online with the remaining logs moved into longer term storage or archival solutions. These solutions store online logs for 30 to 180 days, shift them into an online or near-line archive for up to a year, and then move any logs into longer term backup to cover the remainder of the retention period. At the end of that period, security operations are responsible for ensuring that old log information is properly disposed of using defined data disposal procedures and tools.

Modern reporting tools can also be used to transform security event information into
useful business intelligence. Rather than focusing on basic log analysis, they tend to focus on higher level reporting on service metrics as well as reporting for compliance purposes.

## Response

When an incident is detected, a containment strategy must be decided. Containment may include disconnecting devices from the network, shutting systems down, or redirecting traffic around an affected area of the network. The containment strategy should be driven by several criteria including:

- The need to preserve forensic evidence for possible legal action.
- The availability of services the affected component provides.
- The potential damage that leaving the affected component in place may cause.
- The time required for the containment strategy to be effective.
- The resources required to contain the affected component.

Delaying containment when a system is compromised by a suspected attacker is often a poor choice because it can lead to further attacks on more information systems. Arguments may be made that the security professional could observe the attacker to learn more about what is happening; however that is best left to honeypots and experienced security engineers. There may also be legal implications if the organization knows about the compromised system and then the compromised system is used to attack another system.

The team should instead focus on obtaining a forensic image of the RAM and hard drive of the compromised system and then determine how to mitigate the vulnerability that caused the compromise. The security professional should consult an organization’s legal team to determine if the image gathered must be suitable for law enforcement or be admissible in court. If needed for law enforcement or court, the security professional must avoid violating the chain of custody and is best assisted by law enforcement or an experienced forensics team while creating an image.

The initial incident and as much relevant information as possible should be documented in an incident management system. The incident should be updated as more information becomes available until the incident is deemed resolved by the security operations team. The documented incident is often one of the most important parts of reconstructing the attack and explaining what happened to third parties.

## Reporting
