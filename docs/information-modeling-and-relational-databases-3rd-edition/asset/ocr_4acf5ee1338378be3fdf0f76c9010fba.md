A schema also has value as a convenient summary of the information deemed important by the enterprise. This makes it easier to form a shared culture among those responsible for the database and its applications.

# Distributed Databases

Distributed systems play an essential role in modern computing. A distributed database system stores its data on more than just a single node, using multiple physical or virtual machines at the same time. The distributed machines have one shared state and operate concurrently.

Distributed systems offer three important features: scalability, availability, and fault tolerance. There is some overlap between these concerns, as we will see shortly, but scalability especially is one of the key motivators for the NoSQL movement.

The two main approaches to scalability can be summarized as _scale-up_ or _scale-out_. The first of these uses progressively more powerful servers as demands increase. The second splits the database into different parts that can be mounted on an increasing number of servers as demands increase.

One way of scaling up is to migrate the database to a more powerful machine, but there are obvious limits to this. An alternative is to use a cluster of servers that shares a common data store. This obviously introduces additional complications and will sooner or later also come to a point where further extension is not feasible.

NoSQL databases focus more on the scale-out strategy, which can cope with databases far larger than would be possible by scaling-up. The key step is to identify a suitable method of partitioning the database. Partitioning could be done in two ways, vertically or horizontally. Consider the example shown in Fig. 17.1.

| empNr | name | photo |
|---|---|---|
| 1 | Alice | alicepic.jpg |
| 2 | Bob | bob2023.jpg |
| 3 | Carol | carol1.jpg |
| 4 | Dave | dave.jpg |

FIG. 17.1 Simple employee data.

Vertical partitioning effectively assigns different table columns to different servers. This can provide some advantages. First, relatively slow-moving data can be separated from more dynamic data. Slow-moving data is a good candidate for an application to cache in a lower-performance store. Second, sensitive data can be stored in a separate partition with additional security controls. Finally, vertical partitioning can reduce the amount of concurrent access that's needed. A possible outcome is shown in Fig. 17.2.