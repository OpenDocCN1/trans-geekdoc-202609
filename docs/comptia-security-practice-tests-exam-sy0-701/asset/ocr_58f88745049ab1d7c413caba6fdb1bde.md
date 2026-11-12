configured to fail-closed because their failure removes critical security functionality. Fail over describes the ability to fail to another device, which is not a common function for an in-line tap. Fail-reset was made up for this question.

73. D. Software-defined wide area networks (SD-WANs) are the core component of secure access, secure edge technology. Additional tools like zero trust functionality, cloud access security brokers, and firewalls are all combined to build a complete SASE implementation.

74. A. Network access control (NAC) has the ability to both profile device security and validate that a given user is authorized to plug a device into a specific Ethernet jack makes this the best solution for Mikayla’s use case. Port security’s list of recognized MAC addresses is both potentially vulnerable to MAC spoofing and does not meet the device security check requirements described. An IPS can help prevent network attacks but does not control port-level access, and jump servers are used to allow access to secured network segments, not to protect individual network jacks.

75. C. Version control will allow staff from Mark’s organization to identify a bad version and revert to a previous known-good version if needed. Threat modeling, least privilege, and artifact signing are all common best practices for IaC, but don’t directly impact version changes.

76. A. PaaS vendors are responsible for the underlying service and platform, including the networks, systems, and infrastructure that it runs on, including their security. Customers are responsible for their use of the platform, including endpoints, users, and applications built on the platform, again including their security.

77. B. The biggest issue for resilience is that placing backups in the same facility as the devices or systems they are backing up means that a single disaster could destroy both. Nick should consider off-site backup storage. Tape recovery can be slow, but this is a restoration timeframe issue, not a resilience issue. Tape lifetime is typically quite long, and backups are usually rolled over in time periods shorter than a year for most organizations. Finally, validation of backups can be a concern, but there is no description in the question that would lead to conclusions about testing.

78. B. AES-256 is the current mainstream standard for encryption. AES 128 and 192 are both less secure, and AES-512 is not an implemented or commonly used standard.

79. C. While RTOS issues with vulnerabilities, the inability to install security tools. and a lack of patches for RTOS-based devices are all common security concerns, they are not as frequently targeted by malware infections.

80. B. Tokens should not be easily reversible. Instead, they should require access to the original tokenization function or a mapping to the original data. Tokens should not have intrinsic meaning or value, and frequently rely on hash functions as part of their generation process to ensure this.

81. B. Replication is typically the fastest means to recovery since the replica system is running and ready to take over. Snapshot recovery is normally the next fastest, followed by restoration from other storage. Journaling can introduce additional slowdowns depending on how