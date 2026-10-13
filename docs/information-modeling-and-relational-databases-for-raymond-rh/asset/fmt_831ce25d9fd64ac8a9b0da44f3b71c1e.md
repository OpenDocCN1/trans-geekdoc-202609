
# ACID vs. BASE

The ACID viewpoint strongly values consistency, making it well-suited for traditional transactional database systems where reliable data is crucial. The rise of distributed systems has promoted interest in a different perspective, known by the acronym BASE, from the terms **Basically Available**, **Soft state**, and **Eventually consistent** ([Pritchett, 2008](#Ch017_875-933_B9780443237904000050.xhtml#bb1080)).

*   **Basically available** means that the system should always be available for requests, even if the system is experiencing some sort of failure or outage.
*   **Soft state** refers to the fact that different copies of the data do not need to be in a completely consistent state at all times.
*   **Eventually consistent** means that differences in data will eventually become reconciled, given enough time.

The BASE viewpoint strongly values availability over consistency by allowing temporary inconsistencies between replicas of the data. This is obviously a looser requirement than ACID, but it is more relevant for distributed systems.

# Consistency Mechanisms in CP Databases

Databases can ensure consistency by employing various techniques and mechanisms to synchronize data across multiple nodes in a distributed system. Some common methods used by CP databases include the following:

*   **Consensus protocols**: CP databases often utilize consensus protocols, such as `Paxos` or `Raft`, to achieve agreement among nodes about the order and validity of data updates. These protocols ensure that all nodes in the system reach a consistent state by requiring a majority or unanimous agreement before committing changes.
*   **Two-phase commit**: In a distributed transaction, a two-phase commit protocol can be used to coordinate the commit or rollback of changes across multiple nodes. It ensures that all participating nodes agree to commit the transaction or abort it, guaranteeing consistency across the system.
*   **Quorums and replicas**: CP databases typically use replication to maintain multiple copies of data across different nodes. Quorums are used to determine the minimum number of nodes that need to agree on a read or write operation to ensure consistency. By requiring a certain number of replicas to participate in operations, CP databases can ensure that all replicas are consistent before returning a result.
*   **Synchronization and locking**: CP databases may use synchronization mechanisms, such as distributed locks or optimistic concurrency control, to prevent concurrent access and modifications to shared data. These techniques ensure that conflicting changes are serialized and applied in a consistent order.
*   **Data versioning and conflict resolution**: CP databases often employ data versioning or timestamping to track changes and resolve conflicts when concurrent updates occur. By assigning unique versions or timestamps to data, conflicts can be detected and resolved based on predefined rules or policies.

Of course, achieving consistency can introduce latency and may reduce availability, especially during network partitions or failures. The specific mechanisms and trade-offs employed by a CP database depend on its design and the level of consistency required by the application.

# Availability

Availability in distributed systems refers to the ability of the system to respond to client requests, even when some parts of the system have failed. This is important because one of the main reasons for using a distributed architecture is to increase availability and fault tolerance.

In a distributed database, several methods can be employed to provide high availability, ensuring that the system remains operational and accessible even in the presence of failures or network partitions. Here are some common techniques used to achieve high availability:

*   **Replication**, which involves creating multiple copies of data across different nodes in the distributed database. By having replicas in different locations, the system can continue serving read and write requests even if some nodes fail. Replication also improves fault tolerance, as a copy of the data is available even if one or more nodes become unavailable.
*   **Data partitioning**, or sharding, involves dividing the dataset into smaller subsets and distributing them across multiple nodes. Each node is responsible for a specific partition of the data. By distributing the data, the system can handle a larger volume of requests in parallel, improving availability and scalability.
*   **Load balancing** techniques distribute incoming requests across multiple nodes in a distributed database, ensuring that the workload is evenly distributed. This helps prevent any single node from becoming overwhelmed with requests, improving availability by avoiding bottlenecks and optimizing resource utilization.
*   **Failure detection and recovery** mechanisms are crucial for high availability. Nodes can periodically check the health of other nodes and detect failures. Upon failure detection, the system can take appropriate actions, such as promoting replicas to replace failed nodes or redistributing the data. Automatic failure detection and recovery minimize downtime and ensure continuous availability.
*   **Redundancy and Failover**: Redundancy involves having multiple nodes or components that can serve the same function. In case of a failure, failover mechanisms can redirect requests to healthy nodes or activate standby replicas. Redundancy and failover strategies provide fault tolerance and improve availability by minimizing the impact of failures on system operations.

By combining these techniques, distributed databases can achieve high availability by ensuring continuous access to data and uninterrupted operation, even in the face of failures or network disruptions. The specific methods used depend on the database system’s design, requirements, and the desired level of availability.

# NoSQL Benefits

When comparing relational database systems from various suppliers, it’s clear that they have many commonalities. This is hardly surprising given that they are all based on the same fundamental logical concept. The same cannot be said for NoSQL databases. Each NoSQL database is designed to fill a specific niche, resulting in a wide range of variations among different systems. As we will see later, these can be classified into broad families, but they all share a common set of motivations for their existence. These fall into three main categories: coping with large amounts of data, improving performance, and enabling a more agile database development process.

As we’ve already noted, there is a consistent trend toward ever-bigger databases. For practical reasons, this means implementing a “scale-out” policy to support the database on multiple computers, raising all the distributed system issues discussed above.

Distribution is not so easy with a relational database, and many of the NoSQL approaches are aimed at providing ways of scaling using relatively cheap commodity hardware, usually by partitioning the database in some way. This also makes a cloud computing architecture a good fit for Big Data systems, and all cloud service providers offer managed NoSQL solutions.

NoSQL systems usually provide options for adjusting the trade-off boundary between consistency and availability, so that the system is as consistent as possible and as available as possible within the conditions of the intended type of application. A particular application area may offer special features that can be exploited to improve either consistency or availability within that given context.
