SDS-based storage systems provide several types of protection and data availability mechanisms:

+   - **Intelligent Data Placement —** Data protection begins the second that data is written to a physical disk and acknowledged to the application workload. In an SDS storage system, data placement and protection are critical because no hardware-based RAID mechanism does the work of data protection. In SDS, data placement may happen several times.
+   - **Controllers —** In SDS, software-based controllers are responsible for making sure that data is read from and written to disk and remains available for use by applications and virtual machines. Software controllers are often redundant, helping the environment maintain a high level of availability, even in the event of a failure.
+   - **Software RAID —** Although SDS makes hardware-based RAID systems unnecessary, software-based RAID constructs may be used. To conform to the concepts of SDS, these RAID constructs must be fully supported by software-based controllers and must be able to scale to meet enterprise-class capacity and performance needs.

For the security professional to have a clear picture of the nature of SDS technology, we will briefly examine how it is implemented by VMware in their Virtual SAN offering. VMware® Virtual SAN™ is hypervisor-converged storage software that abstracts and pools server-side flash and disk to create a highly performant and resilient persistent storage tier at the hypervisor layer.

# Hypervisor-Converged Storage

Virtual SAN is embedded into the vSphere kernel. This tight integration is important because it is uniquely positioned in the stack to understand the VMs and applications running above vSphere and the underlying storage infrastructure capabilities. It is Virtual SAN’s unique positioning in the stack that allows it to optimize the I/O datapath to deliver better performance than a virtual appliance or external device.

# VM-Centric Policy-Based Management and Automation

Storage requirements are tied to individual virtual machines or virtual disks in the form of policy statements. Virtual SAN provisions storage resources based on those policies governed by SLAs. Using Storage Policy Based Management (SPBM), server administrators are able to create storage policies based on each application or VM’s performance, availability, and capacity needs. Those policies are then matched by Virtual SAN to underlying storage resources to deliver automation to storage resource