
In [[ABAD2009b](#ch15.xhtml#ref15_3)] and [ABAD2007], researchers reported a vertically partitioned DBMS for storage and retrieval of RDF data. Their solution is a schema with a two-column table for each predicate. Their schema is then implemented on top of a column-store relational database such as CStore [[STON2005](#ch15.xhtml#ref15_46)] or MonetDB [BONC06]. They observed performance improvement with their scheme over traditional relational database schemes. We have leveraged this technology in our predicate-based partitioning within the MapReduce framework. However, in the vertical partitioning research, only small databases (<100 million) were used. Several papers [[SIDI2008](#ch15.xhtml#ref15_43), [MCGL2009](#ch15.xhtml#ref15_31), [WEIS2008](#ch15.xhtml#ref15_57)] have shown that vertical partitioning's performance is drastically reduced as the dataset size is increased.

Jena [CARR2004] is a semantic web framework for Jena. True to its framework design, it allows integration of multiple solutions for persistence. It also supports inference through the development of reasoners. However, Jena is limited to a triple store schema. In other words, all data are stored in a single three column table. Jena has very poor query performance for large datasets. Furthermore, any change to the dataset requires complete recalculation of the inferred triples.

BigOWLIM [KIRY2005] is among the fastest and most scalable semantic web frameworks available. However, it is not as scalable as our framework and requires very high-end and costly machines. It requires expensive hardware (a lot of main memory) to load large datasets and it has a long loading time. As our experiments show, it does not perform well when there is no bound object in a query. However, the performance of our framework is not affected in such a case.

RDF-3X [NEUM2008] is considered the fastest existing semantic web repository. In other words, it has the fastest query times. RDF-3X uses histograms, summary statistics, and query optimization to enable high-performance semantic web queries. As a result, RDF-3X is generally able to outperform any other solution for queries with bound objects and aggregate queries. However, RDF-3X's performance degrades exponentially for unbound queries, and queries with even simple joins if the selectivity factor is low. This becomes increasingly relevant for inference queries which generally require unions of subqueries with unbound objects. Our experiments show that RDF-3X is not only slower for such queries, it often aborts and cannot complete the query. For example, consider the simple query "Select all students." This query in LUBM requires us to select all graduate students, select all undergraduate students, and union the results together. However, there are a very large number of results in this union. While both subqueries complete easily, the union will abort in RDF-3X for LUBM (30,000) with 3.3 billion triples.

RDF Knowledge Base (RDFKB) [[MCGL2010](#ch15.xhtml#ref15_32)] is a semantic web repository using a relational database schema built on bit vectors. RDFKB achieves better query performance than RDF-3X or vertical partitioning. However, RDFKB aims to provide knowledge base functions such as inference forward chaining, uncertainty reasoning, and ontology alignment. RDFKB prioritizes these goals ahead of scalability. RDFKB is not able to load LUBM (30,000) with three billion triples, so it cannot compete with our solution for scalability.

Hexastore [WEIS08] and BitMat [[ATRE2008](#ch15.xhtml#ref15_5)] are main memory data structures optimized for RDF indexing. These solutions may achieve exceptional performance on hot runs, but they are not optimized for cold runs from persistent storage. Furthermore, their scalability is directly associated with the quantity of main memory RAM available. These products are not available for testing and evaluation.

In our previous work [[HUSA2009](#ch15.xhtml#ref15_22), [HUSA2010](#ch15.xhtml#ref15_23)], we proposed a greedy and an exhaustive search algorithm to generate a query processing plan. However, the exhaustive search algorithm was expensive and the greedy one was not bounded and its theoretical complexity was not defined. In this chapter, we present a new greedy algorithm with an upper bound. Also, we did observe scenarios in which our old greedy algorithm failed to generate the optimal plan. The new algorithm is able to obtain the optimal plan in each of these cases. The Join Executer component runs the jobs using MapReduce framework. It then relays the query answer from Hadoop to the user.

## 15.4 Architecture

Our system architecture is illustrated in [Figure 15.3](#ch15.xhtml#fig15_3a). It essentially consists of a SPARQL query optimizer and an RDF data manager implemented in the cloud. The operational architecture is illustrated in [Figure 15.4](#ch15.xhtml#fig15_4a). It consists of two components. The upper part of Figure 15.4 depicts the data preprocessing component and the lower part shows the query answering one. We have three subcomponents for data generation and preprocessing. We convert RDF/XML [[W3f](#ch15.xhtml#ref15_55)] to N-Triples [W3a] serialization format using our N-triples converter component. The predicate split (PS) component takes the N-triples data and splits it into predicate files. The predicate files are then fed into the Predicate Object Split (POS) component which splits the predicate files into smaller files based on the type of objects. These steps are described in the following figures.

![Figure 15.3 System architecture.](images/fig15_3.jpg)

[Figure 15.3 System architecture.](#ch15.xhtml#Ffig15_3)

![Figure 15.4 Operational architecture.](images/fig15_4.jpg)

[Figure 15.4 Operational architecture.](#ch15.xhtml#Ffig15_4)

### 15.4.1 Data Generation and Storage

For our experiments, we use the LUBM [[GUO2005](#ch15.xhtml#ref15_19)] dataset. It is a benchmark dataset designed to enable researchers to evaluate a semantic web repository's performance [[GUO2004](#ch15.xhtml#ref15_18)]. The LUBM data generator generates data in RDF/XML serialization format. This format is not suitable for our purpose because we store data in HDFS as flat files and so to retrieve even a single triple, we would need to parse the entire file. Therefore, we convert the data to N-triples to store the data, because with that format, we have a complete RDF triple (Subject, Predicate, and Object) in one line of a file which is very convenient to use with MapReduce jobs. The processing steps to go through to get the data into our intended format are described in the following sections.

### 15.4.2 File Organization

We do not store the data in a single file because, in a Hadoop and MapReduce framework, a file is the smallest unit of input to a MapReduce job and in the absence of caching, a file is always read from the disk. If we have all the data in one file, the whole file will be input to jobs for each query. Instead, we divide the data into multiple smaller files. The splitting is done in two steps which we discuss in the following sections.

### 15.4.3 Predicate Split
