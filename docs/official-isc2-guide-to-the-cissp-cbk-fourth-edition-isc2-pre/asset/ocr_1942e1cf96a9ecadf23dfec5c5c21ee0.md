and compatibility will arise.

+   - **Database Maintenance and Updating** — A database or dataset should have carefully defined procedures for updating. If a dataset is live or ongoing, this will include such things as additions, modifications, and deletions, as well as frequency of updates. Versioning will be extremely important when working in a multi-user environment.
+   - **Database Backup and Recovery Requirements** — The requirements for the backing up or recovery of a database in case of user error, software/media failure, or disaster, should be clearly defined and agreed upon to ensure the longevity of a dataset. Mechanisms, schedules, frequency and types of backups, and appropriate recovery plans should be specified and planned. This can include types of storage media for onsite backups and whether off-site backing up is necessary.

Archiving of data should be a priority data management issue. Organizations with high turnovers of staff and data stored in a distributed manner need sound documenting and archiving strategies built into their information management chain. Snapshots (versions) of data should be maintained so that rollback is possible in the event of corruption of the primary copy and backups of that copy.

In addition, the security professional needs to consider the costs associated with the deployment and management of the data throughout its lifecycle in the organization. For instance, the hardware cost for a deployment of a dataset managed on a Microsoft SQL server cluster or an Oracle server cluster will be higher if that deployment is done onsite versus through a cloud provider via an IaaS solution. However, the operational costs associated with providing access to the dataset over the lifecycle of its use will be potentially higher for the cloud-based deployment then for the onsite deployment. It is up to the security architect and the security professional to work together to document and help the organization understand the costs issues associated with the security solution but also the overall costs associated with platform choices due to security considerations.

# Longevity and Use

# Data Security

Security involves the system, processes, and procedures that protect a database from unintended activity. Unintended activity can include misuse, malicious attacks, inadvertent mistakes, and access made by individuals or processes, either authorized or