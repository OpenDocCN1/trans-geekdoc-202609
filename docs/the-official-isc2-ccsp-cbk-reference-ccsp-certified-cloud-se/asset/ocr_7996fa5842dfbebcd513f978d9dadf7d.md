Especially in large environments, storage tools like storage area networks (SAN) will include their own health and diagnostic tools; the information from these should be integrated into the organization’s continuous monitoring strategy.

+   - **Environmental:** All computing components generate heat and are generally not designed for use in very wet environments or in direct contact with water. Monitoring environmental conditions including heat, humidity, and the presence of water can be critical to detecting issues early.

The types of monitoring tools in use will depend on a number of factors. Many vendors of cloud-grade hardware such as SAN controllers or virtualization clusters include diagnostic and monitoring tools. The usefulness of these built-in tools may be limited if your organization’s measurement needs require data that is not captured, in which case a third-party tool may be required.

In general, hardware monitoring will be the purview of the CSP and not the consumer, as the CSP is likely to retain physical control of hardware. Data center design and infrastructure management are entire fields of endeavor largely outside the scope of the CCSP, but it is obviously important for a CSP to have appropriately skilled team members. The Uptime Institute (uptimeinstitute.com/tiers) is one resource that provides guidance and education on designing and managing infrastructure; another is the International Data Center Authority (www.idc-a.org).

# Configuration of Host and Guest Operating System Backup and Restore Functions

There is a clear delineation of responsibility between the CSP and consumer when it comes to configuring, testing, and managing backup and restoration functions in cloud environments. In SaaS cloud models, the CSP retains full control over backup and restore and will often be governed by SLA commitments for restoration in the event of an incident or outage.

In the PaaS model, there will be backup and restoration responsibilities for both the consumer and the CSP, especially for VMs. The CSP is responsible for maintaining backup and restoration of the host OS and any hypervisor software and for ensuring the availability of the system in line with agreed-upon service levels.

Backup and recovery of individual VMs in IaaS are the responsibility of the consumers and may be done in a variety of ways. This might include full backups, snapshots, or definition files used for infrastructure as code deployments. Regardless of which backup method is utilized, a number of security considerations should be taken into account.

+   - Sensitive data may be stored in backups, particularly in snapshot functions that do not support the same access controls or encryption as the OS they are created from. In this case, access to snapshots and need-to-know principles must be considered when designing the backup plan.