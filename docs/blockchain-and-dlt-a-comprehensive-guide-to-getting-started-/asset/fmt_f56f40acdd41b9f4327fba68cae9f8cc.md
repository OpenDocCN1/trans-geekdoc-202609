
# Proof-of-authority (PoA)

With PoA, block validators are predetermined, making it even more centralized. New blocks on the blockchain are created only when the validators are in the majority. The protocol resembles PoS. The validators are publicly known and accountable for determining their role and eligibility for PoS validation. PoA is employed by Elysian, a newer blockchain, as well as some Ethereum testnets or test blockchains.

# Fault tolerance

Fault tolerance is a property of the system that helps to continue its working when a fault occurs.

Nowadays, many computers work together on a shared task in a distributed manner. For example, imagine there are 10 different systems working together and if one system happens to have a problem, the other 9 systems will take over and continue the work without any interruptions to the user. This is similar to how big online stores operate, where even if one system malfunctions, the other systems will take control and customers can still purchase products without any issues. There are generally three types of issues that can arise in distributed systems: failures, errors, and faults. A fault refers to any problem that occurs within the system. When we investigate the system after a fault, we may find mistakes or errors in the code or the way it functions. A failure is when the system is unable to produce an outcome due to faults and errors. We need fault tolerance in distributed systems because of reliability, availability and security. Common example of fault tolerance applications are as follows:

- Air traffic control
- Banking services
- Patient monitoring system

# Distributed file systems

A distributed file system (DFS) differs from conventional file systems such as `NTFS` and `HFS` by allowing direct access to the same file data from multiple sources. The data stored within a DFS can be located anywhere within the network, making it accessible to users who have the necessary permissions and access to the host. The primary objective of DFS is to facilitate resource and information sharing among users of geographically distributed systems through a shared common file system (CFS). DFS is integrated into operating systems and operates as part of the overall system configuration, connecting workstations and mainframes within a LAN. The process of creating a namespace within DFS is transparent to clients. The services provided by DFS consist of two components.

- Local transparency
- Redundancy

## Features of distributed file system

Some of the features of distributed file system are as follows:

- **Multi-protocol access**: Hosts can utilize standard `NFS`, `SMB`, or a `POSIX` client provided by the solution provider to access DFS data. Occasionally, `NVMe-oF` for files and (`NVIDIA`) `GPU` direct storage access can also be observed. This implies that the same file can be accessed using all the protocols supported by the DFS solution.
- **Data integrity**: Multiple users typically share a file system, and the file system must ensure the integrity of the data stored in transferred files. A concurrency control method is required to properly synchronize concurrent access requests from multiple users competing for access to the same file. A file system commonly offers atomic transactions as a high-level concurrency management system to maintain data integrity.
- **Transparent local access**: From the perspective of a host, the data is accessed as if it were local to the host accessing it.
- **Location independence**: Hosts may have no knowledge of the physical location of file data. The DFS manages data location, not the host accessing it.
- **Coherent access**: DFS file data is managed in such a way that it appears to the host(s) as if it all resides within a single file system, even though the data may be distributed across multiple storage devices/servers and locations.
- **Data-in-flight encryption**: Most DFS systems support encryption of data and metadata while it is being transmitted.
- **Local gateways and scale-out storage solution**: DFS systems may require server and storage resources at each location with access to file data. Local gateways often cache metadata and data referenced by hosts. These gateways can be scaled up or down as needed to meet performance requirements. In some cases where access and data reside together, gateways are not necessary.

Refer to Figure 1.10 for an example of DFS:

![](images/Figure_1.10.png)

Some pros and cons of DFS are as follows:

- **Storage management flexibility**: Storage management is very flexible and easy to modify it according to our need.
- **Availability**: High availability is also one of the best benefits of DFS. It keeps all the important data available all the time.
- **Security integration**: It is easy to implement security checks in DFS.
- **Load sharing**: Load sharing can be done with optimal results using the DFS.
- **Graphical way of administration**: Graphical view of administration window is available which reduces the cost by cutting down administration level.

# Distributed database

Distributed databases are employed for horizontal scalability, and they are crafted to fulfil the workload demands without necessitating modifications in the database application or vertical scaling of a solitary machine. Distributed databases address diverse concerns such as accessibility, fault tolerance, throughput, response time, scalability, and numerous other challenges that can arise from employing a lone machine and a solitary database.

In a distributed system, multiple computers work independently on a common task. This can be seen in large e-commerce stores where multiple systems are used to handle the website's operations. If one system encounters a problem or failure, the other systems can take over and continue to operate without interruption. This type of system can also be seen in distributed databases, where multiple nodes work together to store and retrieve data. This approach allows for more efficient storage and retrieval, as well as increased availability and the ability to handle more requests. Additionally, distributed databases can scale horizontally by adding more nodes, providing more computing power, and eliminating the risk of a single point of failure.

There are mainly three types of problems (as discussed in previous section of fault tolerance) that can occur in distributed systems: failures, errors, and faults. A failure is when the system is unable to provide an outcome due to issues with the code or system. An error is a problem that is noticed when inspecting the system after a failure has occurred. A fault is a problem that occurs within the system. This approach helps to prevent single points of failure and increase overall system availability. A distributed database is spread across multiple physical locations, with processing tasks divided among processors on various database nodes. In a centralized distributed database management system (DDBMS), the distributed data is managed as though it were stored in a single physical location. The DDBMS coordinates all data operations across databases and ensures that updates made in one database are automatically propagated to other sites.

Distributed databases are databases that are spread across multiple locations, nodes, or servers.

## Different types of Distributed databases

There are various types of distributed databases, each designed to meet specific requirements. Here are some common types:

### Homogeneous distributed database

- **Definition**: All nodes have the same DBMS and data model.
- **Advantages**: Uniformity simplifies management and maintenance.
- **Example**: `Oracle Real Application Clusters (RAC)`.

### Heterogeneous distributed database

- **Definition**: Different nodes may run different DBMS or have different data models.
- **Advantages**: Allows integration of diverse systems.
