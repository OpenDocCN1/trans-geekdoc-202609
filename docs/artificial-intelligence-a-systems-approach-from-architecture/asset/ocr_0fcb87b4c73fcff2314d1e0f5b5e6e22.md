# 3.3: Databases: Management and Evolution

| Table 3.1 Key questions prior to starting the data-conditioning stage |
| Key Questions | Comments |
|---|---|
| What insight does the customer need? | Work from the expected result back to the needed data. |
| What data input is required to achieve the desired insight? | Make sure that we have curated data. |
| Are the incoming data and required processing batched or streaming? | Forwardly deployed applications batched in the cloud, streaming, or both. |
| Can we solve the AI problem using ML techniques other than deep learning? | Deep learning is very powerful when we have data that is representative (statistically) of the population, scenarios, or both. |
| Do we need edge computing (in real time)? | We might need to operate under low-capacity and intermittent data links. |
| How do we protect our AI system from adversarial AI (e.g., data poisoning?) | AI systems are very fragile and easy to fail. |
| What measures of effectiveness (MoEs) are critical? | Many measures of performance (MoPs) are available. The challenge is to aggregate MoPs into Moe metric |

distributed structured data table referred to as HBase. HBase (an Apache open-standard), with MapReduce (a distributed processing model) plus the Hadoop Distributed File System (HDFS), became accepted standards for their scalability features and able to enable rapid ingestion of streaming data [19]. The new approach and standard, for managing distributed files across a large number of computing nodes, became as Not-only Structured Query Language (NoSQL).

Today, the Apache Hadoop open-source project develops and maintains the library necessary for managing large volumes and ingesting data at high speeds. Hadoop consists of common utilities, such as HDFS, MapReduce, and Hadoop YARN (framework for job scheduling and cluster resource management; which refers to yet another resource negotiator) [20]. This library set is popular and well accepted for implementing data processing in a large cloud computing environment.

Database designers strive to have the standards meet a set of properties referred to as atomicity, consistency, isolation, and durability (ACID). Table 3.2 defines these properties, including the benefits and challenges of each. The goal with relational databases using a SQL format was to meet these properties, but unfortunately, as data grew in