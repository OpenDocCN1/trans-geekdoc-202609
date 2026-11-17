
Lambda consumer as soon as data arrives in the Kinesis stream.

- Kinesis is scalable due to its shard architecture, which is the fundamental throughput unit of a Kinesis stream. _What is a shard?_ A shard is a logical structure that partitions the data based on a partition key. A shard supports a writing capacity of 1 MB/sec and a reading capacity of 2 MB/sec. 1,000 `PUT` records per second are supported by a single shard. If you have created a stream with _three shards_, then 3 MB/sec write throughput and 6 MB/sec read throughput can be achieved, and this allows 3,000 `PUT` records. So, with more shards, you have to pay an extra amount to get higher performance.

- The data in a shard is stored via a Kinesis data record and can be a maximum of 1 MB. Kinesis data records are stored across the shard based on the partition key. They also have a sequence number. A sequence number is assigned by Kinesis as soon as a `putRecord` or `putRecords` API operation is performed so as to uniquely identify a record. The partition key is specified by the producer while adding the data to the Kinesis data stream, and the partition key is responsible for segregating and routing the record to different shards in the stream to balance the load.

- There are two ways to encrypt the data in a Kinesis stream: server-side encryption and client-side encryption. Client-side encryption makes it hard to implement and manage the keys because the client has to encrypt the data before putting it into the stream and decrypt the data after reading it from the stream. With server-side encryption enabled via **AWS KMS**, the data is automatically encrypted and decrypted as you put the data and get it from a stream.

## NOTE

Amazon Kinesis shouldn't be confused with Amazon SQS. Amazon SQS supports one production group and one consumption group. If your use case demands multiple users sending data and receiving data, then Kinesis is the solution.

For decoupling and asynchronous communications, SQS is the solution, because the sender and receiver do not need to be aware of one another.

In SQS, there is no concept of persistence. Once the message is read, the next step is deletion. There's no concept of a retention time window for Amazon SQS. If your use case demands large-scale ingestion, then Kinesis should be used.

In the next section, you will learn about storing the streamed data for further analysis.

## Storing and transforming real-time data using Kinesis Data Firehose

There are a lot of use cases that require data to be streamed and stored for future analytics purposes. To overcome such problems, you can write a Kinesis consumer to read the Kinesis stream and store the data in S3. This solution needs an instance or a machine to run the code with the required access to read from the stream and write to S3. The other possible option would be to run a Lambda function that gets triggered on the `putRecord` or `putRecords` API made to the stream and reads the data from the stream to store in the S3 bucket:

- To make this easy, Amazon provides a separate service called Kinesis Data Firehose. This can easily be plugged into a Kinesis data stream and will require essential IAM roles to write data into S3. It is a fully managed service to reduce the load of managing servers and code. It also supports loading the streamed data into Amazon Redshift, Elasticsearch, and Splunk. Kinesis Data Firehose scales automatically to match the throughput of the data.

- Data can be transformed via an AWS Lambda function before storing or delivering it to the destination. If you want to build a raw data lake with the untransformed data, then by enabling source record backup, you can store it in another S3 bucket prior to the transformation.

- With the help of AWS KMS, data can be encrypted following delivery to the S3 bucket. It has to be enabled while creating the delivery stream. Data can also be compressed in supported formats, such as gzip, ZIP, or Snappy.

In the next section, you will learn about different AWS services used for ingesting data from on-premises servers to AWS.

## Different ways of ingesting data from on-premises into AWS

With the increasing demand for data-driven use cases, managing data on on-premises servers is pretty tough at the moment. Taking backups is not easy when you deal with a huge amount of data. This data in data lakes is used to build deep neural networks, create a data warehouse to extract meaningful information from it, run analytics, and generate reports.

Now, if you look at the available options to migrate data into AWS, this comes with various challenges too. For example, if you want to send data to S3, then you have to write a few lines of code to send your data to AWS. You will have to manage the code and servers to run the code. It has to be ensured that the data is commuting via the HTTPS network. You need to verify whether the data transfer was successful. This adds complexity as well as time and effort challenges to the process. To avoid such scenarios, AWS provides services to match or solve your use cases by designing a hybrid infrastructure that allows data sharing between the on-premises data centers and AWS. You will learn about these in the following sections.

### AWS Storage Gateway

Storage Gateway is a hybrid storage virtual appliance. It can run in three different modes – File Gateway, Tape Gateway, and Volume Gateway. It can be used for the extension, migration, and backups of an on-premises data center to AWS:

- In Tape Gateway mode, Storage Gateway stores virtual tapes on S3, and when ejected and archived, the tapes are moved from S3 to Glacier. Active tapes are stored in S3 for storage and retrieval. Archived or exported tapes are stored in Virtual Tape Shelf (VTS) in Glacier. Virtual tapes can be created and can range in size from 100 GiB to 5 TiB. A total of 1 petabyte of storage can be configured locally and an unlimited number of tapes can be archived to Glacier. This is ideal for an existing backup system on tape and where there is a need to migrate backup data into AWS. You can decommission the physical tape hardware later.

- In File Gateway mode, Storage Gateway maps files onto S3 objects, which can be stored using one of the available storage classes. This helps you to extend the data center into AWS. You can load more files to your file gateway and these are stored as S3 objects. It can run on your on-premises virtual server, which connects to various devices using Server Message Block (SMB) or Network File System (NFS). File Gateway connects to AWS using an HTTPS public endpoint to store the data on S3 objects. Life cycle policies can be applied to those S3 objects. You can easily integrate your Active Directory (AD) with File Gateway to control access to the files on the file share.

- In Volume Gateway mode, the storage gateway presents block storage. There are two ways of using this; one is **Gateway Cached** and the other is **Gateway Stored**:

- **Gateway Stored** is a volume storage gateway running locally on-premises. It has local storage and an upload buffer. A total of 32 volumes can be created, and each volume can be up to 16 TB in size for a total capacity of 512 TB. Primary data is stored on-premises and backup data is asynchronously replicated to AWS in the background. Volumes are made available via **Internet Small Computer Systems Interface (iSCSI)** for network-based servers to access. It connects to a Storage Gateway endpoint via HTTPS public endpoint and creates EBS snapshots from backup data. These snapshots can be used to create standard EBS volumes. This option is ideal for migration to AWS, disaster recovery, or business continuity. The local system will still use the local volume, but the EBS snapshots are in AWS, which can be used instead of backups. It’s not the best option for data center extensions because you require a huge amount of local storage.

- **Gateway Cached** is a volume storage gateway running locally on-premises. It has cache storage and an upload buffer. The difference is that the data that is added to Storage Gateway is not local but uploaded to AWS. Primary data is stored in AWS. Frequently accessed data is cached locally. This is an ideal option for extending an on-premises data center to AWS. It connects to a Storage Gateway endpoint via an HTTPS public endpoint and creates S3-backed volume (AWS-managed bucket) snapshots that are stored as standard EBS snapshots.

## Snowball, Snowball Edge, and Snowmobile

These belong to the same product category or family for the physical transfer of data between business operating locations and AWS. To move a large amount of data into and out of AWS, you can use any of the three:

- **Snowball**: This physical device can be ordered from AWS by logging a job. AWS delivers a device for you to load your data onto before sending it back. Data in Snowball is encrypted using KMS. It comes with two capacity ranges: 50 TB and 80 TB. It is economical to order one or more Snowball devices for data between 10 TB and 10 PB. The device can be sent to different premises. It does not have any compute capability; it only comes with storage capability.

- **Snowball Edge**: This is like Snowball, but it comes with both storage and compute capability. It has a larger capacity than Snowball. It offers fast networking, such as 10 Gbps over RJ45, 10/25 Gb over SFP28, and 40/100 Gb+ over QSFP+ copper. This is ideal for the secure and quick transfer of terabytes to petabytes of data into AWS.

- **Snowmobile**: This is a portable data center within a shipping container on a truck. It allows you to move exabytes of data from on-premises to AWS. If your data size exceeds 10 PB, then Snowmobile is preferred. Essentially, upon requesting to use the Snowmobile service, a truck is driven to your location and you plug your data center into the truck and transfer the data. If you have multiple sites, choosing Snowmobile for data transfer is not an ideal option.

## AWS DataSync

AWS DataSync is designed to move data from on-premises storage to AWS, or vice versa:

- It is an ideal product from AWS for data processing transfers, archival or cost-effective storage, disaster recovery, business continuity, and data migrations.

- It has a special data validation feature that verifies the original data with the data in AWS, as soon as the data arrives in AWS. In other words, it checks the integrity of the data.
