
## Amazon FSx for Lustre

### High-performance computing
Amazon FSx for Lustre is also ideal for HPC workloads that demand massive amounts of data processing power with low latency. This includes applications such as scientific research, simulations, and computational tasks like weather modeling and genomic sequencing, enabling researchers and engineers to perform complex calculations and analyses quickly and efficiently.

### Media processing
Amazon FSx for Lustre excels in media processing applications such as video rendering, transcoding, and editing, where substantial data throughput and low latency are critical. The high-performance characteristics of Amazon FSx for Lustre enable media professionals to process large media files efficiently, meeting the demanding requirements of production environments. This ensures faster completion of tasks and a smoother workflow, making it an excellent storage service for the media and entertainment industry.

## Amazon FSx for NetApp ONTAP

Amazon FSx for NetApp ONTAP is another fully managed AWS storage service that utilizes `file` as its storage type and is built on NetApp’s popular ONTAP operating system.

Amazon FSx for NetApp ONTAP delivers high-performance file storage that enables the use of ONTAP’s unified data management capabilities, including the following:

*   Unified storage management that can span flash, disk, and cloud running storage area network (SAN), network attached storage (NAS), and object workloads
*   Low-latency access
*   Data compression
*   Data deduplication
*   Storage scalability

Data compression and deduplication result in cost savings by reducing the size of data that needs to be stored.

### Use Cases

Typical use cases for Amazon FSx for NetApp ONTAP include the following:

*   **Workload migration.** Seamlessly migrate workloads running on NetApp or other NFSs, SMB, iSCSI, and NVMe-over-TCP servers to AWS without modifying application code or how you manage data.
*   **Business continuity and disaster recovery (BDCR).** Achieve secure backup, archive, and data replication from on-premises file servers or across AWS Regions.
*   **High-performance database workloads.** With submillisecond latencies and scalability to up to millions of IOPS per file system, Amazon FSx for NetApp ONTAP delivers highly available shared file storage for your high-performance database workloads. Additionally, Amazon FSx for NetApp ONTAP allows you to scale out file systems by spreading customers’ workloads across multiple file servers.

## Amazon FSx for Windows File Server

Amazon FSx for Windows File Server is a fully managed service that provides highly reliable, scalable, and performant Windows-based file storage. It seamlessly integrates with your existing Windows applications and environments, offering native support for the Windows Server Message Block (SMB) protocol. This makes it an ideal solution for shared file storage in use cases such as home directories, user profiles, and enterprise applications requiring file storage. With Active Directory integration, it ensures secure access control and user management, and data deduplication features help reduce storage costs by eliminating duplicate files.

This storage service offers robust performance with SSD storage options, ensuring low-latency access to your files and high IOPS for demanding applications. Its flexible scalability allows you to easily adjust the file system size to meet your growing storage needs, making it a powerful and efficient storage solution for Windows-based environments.

### Use Cases

Typical use cases for Amazon FSx for Windows File Server include the following:

*   **Windows file server migration.** By providing a fully managed, native Windows file system that supports the SMB protocol and Active Directory integration, Amazon FSx for Windows File Server allows organizations to seamlessly move their existing file systems to AWS without modifying their applications, ensuring a smooth transition with minimal disruption.
*   **SQL Server cost savings.** Amazon FSx for Windows File Server enables high-availability deployments without requiring SQL Enterprise licensing, leading to significant cost savings. This is especially beneficial for organizations centered around SQL Server that are considering migrating to AWS.
*   **Virtual desktops and application streaming.** With Amazon FSx for Windows File Server, you can store user profile data on shared, persistent storage accessible from Amazon WorkSpaces and Amazon AppStream 2.0. This storage service can simplify virtual desktop user experiences by reducing login times and improving overall productivity.

## Amazon FSx for OpenZFS

Amazon FSx for OpenZFS is a fully managed storage service that allows you to operate and scale OpenZFS file systems on AWS, combining the familiar features and performance of OpenZFS with the scalability and simplicity of AWS. It supports access from Linux, Windows, and macOS compute instances and containers via the NFS protocol (v3, v4, v4.1, and v4.2), delivering IOPS in excess of a million and submillisecond latencies, leveraging the latest AWS compute, disk, and networking technologies for high-performance workloads.

### Use Cases

Typical use cases for Amazon FSx for OpenZFS include the following:

*   **Workload migration.** The main use case for this storage service, as the name suggests, is migrating workloads running on ZFS (or other Linux-based file servers) to AWS without needing to modify application code or data management practices.
*   **Data-intensive applications.** With the advanced features of the OpenZFS file system and the extensive NFS support, Amazon FSx for OpenZFS is best suited for developing data-intensive applications on AWS.

## Amazon Elastic Block Storage (EBS)

Amazon EBS is a high-performance AWS `block` storage service, which can be used as a cloud SAN.

Amazon EBS storage comes in the form of EBS volumes, which are similar to virtual disks in the cloud and can be attached to Amazon EC2 instances. EBS volumes can be solid-state drives (SSDs) or hard disk drives (HDDs). SSD-based volumes are optimized for transactional workloads involving frequent read/write operations with small I/O size, where the key performance metric is IOPS, whereas HDD-based volumes are optimized for large streaming workloads where the key performance metric is throughput.

With Amazon EBS you can also take snapshots, which are point-in-time backups of EBS volumes that can be used to restore new volumes.

### Use Cases

Typical use cases for Amazon EBS include the following:

*   **Block-level storage migration.** Migrate mid-range, on-premises SAN workloads to AWS. Attach high-performance and high-availability block storage for mission-critical applications.
*   **RDBMs and NoSQL workloads.** Deploy and scale your choice of databases, including SAP HANA, Oracle, Microsoft SQL Server, PostgreSQL, MySQL, Cassandra, and MongoDB.
*   **Big data analytics workloads.** Easily resize clusters for big data analytics engines, such as Hadoop and Spark, and freely detach and reattach volumes.

## Amazon Relational Database Service (RDS)

Amazon RDS is a managed relational database service available in eight different engines: Amazon Aurora PostgreSQL-Compatible Edition, Amazon Aurora MySQL-Compatible Edition, RDS for PostgreSQL, RDS for MySQL, RDS for MariaDB, RDS for SQL Server, RDS for Oracle, and RDS for Db2.

Because you get to choose the database engine, the code, applications, and tools you already use today with your existing databases can be also used with Amazon RDS. For example, there is no need to refactor your SQL Server stored procedure, to recode your application (other than the means your application uses to connect to your database), or even to use another SQL editing tool.
