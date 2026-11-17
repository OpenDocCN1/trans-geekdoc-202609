

- To understand this product in depth, consider an example of an on-premises data center that has SAN/NAS storage. When you run the AWS DataSync agent on a VMware platform, this agent is capable of communicating with the NAS/SAN storage via an NFS/SMB protocol. Once it is on, it communicates with the AWS DataSync endpoint, and from there, it can connect with several different types of locations, including various S3 storage classes or VPC-based resources, such as **Elastic File System (EFS)** and FSx for Windows Server.

- It allows you to schedule data transfers during specific periods. By configuring the built-in bandwidth throttle, you can limit the amount of network bandwidth that DataSync uses.

## AWS Database Migration Service

There are several situations when an organization might decide to migrate their databases from one to another, such as the need for better performance, enhanced security, or advanced features or to avoid licensing costs from vendors. If an organization wants to expand its business to a different geolocation, it will need to carry out database migration, disaster recovery improvements, and database sync in a cost-effective manner. AWS DMS allows you to leverage the benefits of scalability, flexibility, and cost-efficiency when migrating databases from an *on-premises/EC2 instance/Amazon RDS* to Amazon RDS or Amazon Aurora.

In scenarios where multiple databases need to be consolidated into a single database or data needs to be integrated across multiple databases, AWS DMS can be a valuable tool. AWS DMS is designed to move data from a source to a target provided one of the endpoints is on AWS:

- DMS supports both homogeneous and heterogeneous database migrations, allowing you to migrate between different database engines, such as Oracle, MySQL, PostgreSQL, and Microsoft SQL Server.
- DMS simplifies the database migration process by handling schema conversion, data replication, and ongoing synchronization between the source and target databases.
- DMS supports both full-load and ongoing **Change Data Capture (CDC)** replication methods. Full-load migration copies the entire source database to the target, while CDC captures and replicates only the changes made after the initial load. For example, for a database migration with minimal downtime, DMS performs an initial full-load migration, followed by CDC replication to keep the target database up to date with changes in the source database.
- DMS provides a user-friendly console and API for the easy configuration, monitoring, and management of database migrations. It offers detailed logging and error handling to help diagnose and resolve migration issues. For example, during a migration from Oracle to Amazon Aurora, DMS can automatically convert Oracle-specific data types and modify table structures to align with the Aurora database schema.
- DMS supports continuous data replication, allowing you to keep the source and target databases in sync even after the initial migration. This is particularly useful in scenarios requiring ongoing data synchronization or database replication. An example is if a company maintains an active-active database setup for high availability, where DMS replicates data changes between multiple database instances located in different regions for real-time synchronization.
- DMS offers built-in validation and testing capabilities to ensure the integrity and consistency of the migrated data. It performs data validation checks and generates reports to verify the success of the migration process. For example, after migrating a large database from Microsoft SQL Server to Amazon RDS for PostgreSQL, DMS validates the migrated data by comparing row counts, data types, and other metrics to ensure data accuracy.
- DMS supports both one-time migrations and continuous replication for database consolidation and integration scenarios. It enables organizations to consolidate data from multiple databases into a single target database or distribute data across multiple databases as needed. For example, say a company with several subsidiary databases wants to consolidate all the data into a centralized database for unified reporting and analysis. DMS facilitates the migration and ongoing synchronization of data from multiple sources to the target database.

## Processing stored data on AWS

There are several services for processing the data stored in AWS. You will learn about AWS Batch and AWS Elastic MapReduce (EMR) in this section. EMR is a product from AWS that primarily runs MapReduce jobs and Spark applications in a managed way. AWS Batch is used for long-running, compute-heavy workloads.

### AWS EMR

EMR is a managed implementation of Apache Hadoop provided as a service by AWS. It includes other components of the Hadoop ecosystem, such as Spark, HBase, Flink, Presto, Hive, and Pig. You will not need to learn about these in detail for the certification exam, but here’s some information about EMR:

- EMR clusters can be launched from the AWS console or via the AWS CLI with a specific number of nodes. The cluster can be a long-term cluster or an ad hoc cluster. In a long-running traditional cluster, you have to configure the machines and manage them yourself. If you have jobs that need to be executed faster, then you need to manually add a cluster. In the case of EMR, these admin overheads disappear. You can request any number of nodes from EMR and it manages and launches the nodes for you. If you have autoscaling enabled on the cluster, EMR regulates nodes according to the requirement. That means, EMR launches new nodes in the cluster when the load is high and decommissions the nodes once the load is reduced.
- EMR uses EC2 instances in the background and runs in one Availability Zone in a VPC. This enables faster network speeds between the nodes. AWS Glue uses EMR clusters in the background, where users do not need to worry about having an operational understanding of AWS EMR.
- From a use case standpoint, EMR can be used to process or transform the data stored in S3 and output data to be stored in S3. EMR uses nodes (EC2 instances) as the computing units for data processing. EMR nodes come in different variants, including master nodes, core nodes, and task nodes.
- The EMR master node acts as a Hadoop NameNode and manages the cluster and its health. It is responsible for distributing the job workload among the other core nodes and task nodes. If you have SSH enabled, then you can connect to the master node instance and access the cluster.
- An EMR cluster can have one or more core nodes. If you relate it to the Hadoop ecosystem, then core nodes are similar to Hadoop data nodes for HDFS and they are responsible for running the tasks within them.
- Task nodes are optional and they don’t have HDFS storage. They are responsible for running tasks. If a task node fails for some reason, then this does not impact HDFS storage, but a core node failure causes HDFS storage interruptions.
- EMR has a filesystem called EMRFS. It is backed by S3, which makes it regionally resilient. If a core node fails, the data is still safe in S3. HDFS is efficient in terms of I/O and faster than EMRFS.

In the following section, you will learn about AWS Batch, which is a managed batch-processing compute service that can be used for long-running services.

### AWS Batch

This is a managed batch-processing product. If you are using AWS Batch, then jobs can be run without end user interaction or can be scheduled to run:

- Imagine an event-driven application that launches a Lambda function to process the data stored in S3. If the processing time goes beyond 15 minutes, then Lambda stops the execution and fails. For such scenarios, AWS Batch is a better solution, where computation-heavy workloads can be scheduled or driven through API events.
- AWS Batch is a good fit for use cases where a longer processing time is required or more computation resources are needed.
- AWS Batch jobs can be a script or an executable. One job can depend on another job. A job needs to be defined, such as who can run the job (with IAM permissions), where the job can be run (resources to be used), mount points, and other metadata.
- Jobs are submitted to queues, where they wait for compute environment capacity. These queues are associated with one or more compute environments.
- Compute environments do the actual work of executing the jobs. These can be ECS or EC2 instances, or any computing resources. You can define their sizes and capacities too.
- Environments receive jobs from the queues based on their priority and execute them. They can be managed or unmanaged compute environments.
- AWS Batch can store the metadata in DynamoDB for further use and can also store the output in an S3 bucket.

### NOTE

If you get a question in the exam on an event-style workload that requires flexible compute, a higher disk space, no time limit (more than 15 minutes), or an effective resource limit, then the answer is likely to be AWS Batch.

### Summary

In this chapter, you learned about different ways of processing data in AWS. You also learned the capabilities in terms of extending your data centers to AWS, migrating data to AWS, and the ingestion process. You learned about the various ways of using data to process it and make it ready for analysis. You understood the magic of using a data catalog, which helps you to query your data via AWS Glue and Athena.

In the next chapter, you will learn about various machine learning algorithms and their usage.

