# Implied Rules.

Implied rules are separate from but are part of the default configuration. The network-security device will process the implied rules prior to packets getting to the policy rules. The implied rules may allow the GSD to process specific and known administrative traffic without using processing cycles to go through the entire rule base. It is essential to determine whether these rules exist as well as whether they match the desired security posture. If not, disable or modify the implied rules to fit specific protection needs.

# 26.6.6 Harden the Device.

Protecting the network-security device is a critical part of the security of the overall infrastructure. The two most common ways to reduce these exposures are through the administrative console and validation using vulnerability assessment. The management or system console can provide information such as default listening ports, services running, and the like. If a service is not critical to the functioning of the firewall, disable it to remove any threat of it becoming a compromise vector. Even with the service disabled, ensure you continue to apply patches for those services. Only specific administrative hosts should have direct access to the system. As with the GSD policies, it is useful to validate that configuration changes are actually making the device more secure. By conducting a vulnerability assessment, you are able to determine whether unexpected services are still available or additional vulnerabilities exist.

# 26.7 DISASTER RECOVERY.

The impact of a GSD outage can range from an annoyance to critical event depending on implementation, necessity, and disaster recovery planning. Since these systems represent part of the backbone of the security infrastructure, it is a necessity to provide continual, protected network access.

# 26.7.1 Fail-Over/High Availability.

High availability (HA) architectures are essential in situations where reliable access is a necessity. The HA deployment will typically have an Active/Standby pair; where the active member is processing live packets and the standby member is ready to take over in the case of a failure of the active member. If the standby member is continually synchronizing connection information from the active member, there would be little to no loss of connectivity if the active member fails because the standby would then become active and already have the connection information to allow continued processing of the current sessions and service new sessions.

# 26.7.2 Load-Balancing.

Distributing the load between multiple systems is another way to reduce an availability exposure. If the load equally distributes between two or more systems, the failure of one does not eliminate all access. One caveat is that the load balancer must continue to route each connection to the same system on the back-end to maintain connection information. Otherwise, it may be possible for the load balancer to route traffic to another system that does not know about the established connection (e.g., asymmetric routing).

# 26.7.3 Backup/Restore.

Backup and restore functionality is the most rudimentary disaster recovery method. If the system crashes or suffers a compromise, there must be a way to recover the system in an efficient manner. By having a reliable backup process, it becomes easier to restore the device configuration in the event of a failure. Depending on the vendor, backups may consist of a text file or something more complex, like a GZIP file containing the crucial configuration information. The backup