
3. B, C. AMIs can be created that provide both a base operating system and a pre-installed application. They would not, however, include any networking or hardware profile information—those are largely determined by the instance type.

4. B, D. `c5d.18xlarge` and `t2.micro` are the names of EC2 instance types, not instance type families.

5. D. A virtual central processing unit (vCPU) is a metric that roughly measures an instance type’s compute power in terms of the number of processors on a physical server. It has nothing to do with resilience to high traffic, system memory, or the underlying AMI.

6. A. An EC2 instance that runs on a physical host reserved for and controlled by a single AWS account is called a dedicated host. A dedicated host is not an AMI, nor is it an instance type.

7. C. A virtualized partition of a physical storage drive that is directly connected to the EC2 instance it’s associated with is known as an instance store volume. A software stack archive packaged to make it easy to copy and deploy to an EC2 instance describes an EC2 AMI. It’s possible to encrypt EBS volumes, but encryption doesn’t define them.

8. C, D. Instance store volumes cannot be encrypted, nor will their data survive an instance shutdown. Those are features of EBS volumes.

9. B. Spot instances are unreliable for this sort of usage since they can be shut down unexpectedly. Reserved instances make economic sense where they’ll be used 24/7 over long stretches of time. “Dedicated” isn’t a pricing model.

10. D. Reserved instances will work here because your “base” instances will need to run 24/7 over the long term. Spot and spot fleet instances are unreliable for this sort of usage since they can be shut down unexpectedly. On-demand instances will incur unnecessarily high costs over such a long period.

11. A. There’s no real need for guaranteed available capacity since it’s extremely rare for AWS to run out. You choose how you’ll pay for a reserved instance. All Upfront, Partial Upfront, and No Upfront are available options, and there is no automatic billing. An instance would never be launched automatically in this context.

12. A, C. Because spot instances can be shut down, they’re not recommended for applications that provide any kind of always-on service.

13. C, D. Elastic Block Store provides storage volumes for Lightsail and Beanstalk (and for EC2, for that matter). Elastic Compute Cloud (EC2) provides application deployment, but no one ever accused it of being simple.

14. A. Beanstalk, EC2 (non-reserved instances), and RDS all bill according to actual usage.

15. B, D. Ubuntu is an OS, not a stack. WordPress is an application, not an OS.

16. B, C. Elastic Block Store is, for practical purposes, an EC2 resource. RDS is largely built on its own infrastructure.

17. A, C. While you could, in theory at least, manually install Docker Engine on either a Lightsail or EC2 instance, that’s not their primary function.

18. A, B. Both Lambda and Lightsail are compute services that—while they might possibly make use of containers under the hood—are not themselves container technologies.

19. D. Python is, indeed, a valid choice for a function’s runtime environment. There is no one “primary” language for Lambda API calls.

20. A. While the maximum time was, at one point, 5 minutes, that’s been changed to 15.

Chapter 8: The Core Storage Services

1. B. Bucket names must be globally unique across AWS, irrespective of Region. The length of the bucket name isn’t an issue since it’s between 3 and 63 characters long. Storage classes are configured on a per-object basis and have no impact on bucket naming.

2. A, C. STANDARD_IA and GLACIER storage classes offer the highest levels of redundancy and are replicated across at least three Availability Zones. Due to their low level of availability (99.9 and 99.5 percent, respectively), they’re the most cost-effective for infrequently accessed data. ONEZONE_IA stores objects in only one Availability Zone, so the loss of that zone could result in the loss of all objects. The STANDARD and INTELLIGENT_TIERING classes provide the highest levels of durability and cross-zone replication but are also the least cost-effective for this use case.

3. A, D. S3 is an object storage service, while EBS is a block storage service that stores volumes. EBS snapshots are stored in S3. S3 doesn’t store volumes, and EBS doesn’t store objects.

4. A, B, D. Object life cycle configurations can perform transition or expiration actions based on an object’s age. Transition actions can move objects between storage classes, such as between STANDARD and GLACIER. Expiration actions can delete objects and object versions. Object life cycle configurations can’t delete buckets or move objects to an EBS volume.

5. A, B. You can use bucket policies or access control lists (ACLs) to grant anonymous users access to an object in S3. You can’t use user policies to do this, although you can use them to grant IAM principals access to objects. Security groups control access to resources in a virtual private cloud (VPC) and aren’t used to control access to objects in S3.

6. C, D. Both S3 and Glacier are designed for durable, long-term storage and offer the same level of durability. Data stored in Glacier can be reliably retrieved within eight hours using the Expedited or Standard retrieval options. Data stored in S3 can be retrieved even faster than Glacier. S3 can store objects up to 5 TB in size, and Glacier can store archives up to 40 TB. Both S3 or Glacier will meet the given requirements, but Glacier is the more cost-effective solution.

7. B. You can create or delete vaults from the Glacier service console. You can’t upload, download, or delete archives. To perform archive actions, you must use the AWS Command Line Interface, an AWS SDK, or a third-party program. Glacier doesn’t use buckets.

8. D. The Standard retrieval option typically takes 3 to 5 hours to complete. Expedited takes 1 to 5 minutes, and Bulk takes 5 to 12 hours. There is no Provisioned retrieval option, but you can purchase provisioned capacity to ensure Expedited retrievals complete in a timely manner.

9. A. A Glacier archive can be as small as 1 byte and as large as 40 TB. You can’t have a zero-byte archive.

10. B, D. The tape gateway and volume gateway types let you connect to iSCSI storage. The file gateway supports NFS. There’s no such thing as a cached gateway.

11. B. All AWS Storage Gateway types—file, volume, and tape gateways—primarily store data in S3 buckets. From there, data can be stored in Glacier or EBS snapshots, which can be instantiated as EBS volumes.

12. A, B, D, E. The AWS Storage Gateway allows transferring files from on-premises servers to S3 using industry-standard storage protocols. The AWS Storage Gateway functioning as a file gateway supports the SMB and NFS protocols. As a volume gateway, it supports the iSCSI protocol. AWS Snowball and the AWS CLI also provide ways to transfer data to S3, but using them requires installing third-party software.

13. A, C, E. The volume gateway type offers two configurations: stored volumes and cached volumes. Stored volumes store all data locally and asynchronously back up that data to S3 as EBS snapshots. Stored volumes can be up to 16 TB in size. In contrast, cached volumes locally store only a frequently used subset of data but do not asynchronously back up the data to S3 as EBS snapshots. Cached volumes can be up to 32 TB in size.

14. C. The 80 TB Snowball device offers 72 TB of usable storage and is the largest available. The 50 TB Snowball offers 42 TB of usable space.

15. A, B. AWS Snowball enforces encryption at rest and in transit. It also uses a TPM chip to detect unauthorized changes to the hardware or software. Snowball doesn’t use NFS encryption, and it doesn’t have tamper-resistant network ports.
