
There is an exponential increase in the generation of data since last few years. This heavy data growth poses a challenge for industry and academia for storage and query processing. While analyzing logs for huge data sets, it is required to perform different query operations, such as counting unique items, computing frequency of a data item, searching any item in a set, etc. Additionally, we need to probe more complex datasets, such as images, videos, web pages, etc. Clearly, in order to process such query operations on data, it is essential to store data in computer memory. Tapes, hard disk, solid state drives are different types of memory available for a computing system. However, these different types of memory have different characteristics as presented in [Fig. 9.1](#12chap_09.xhtml#fig9_1). For example, hard disks are mechanical devices and they are slow to access as compared to main memory integrated on a semiconductor chip which makes querying from database in hard disk time consuming. Hence, for a query, a processor has to every time access the hard disk for the data it requires which clearly would be a slow operation. Also, disk access proves costly as compared to the main memory (that's why a GB of main memory is much costlier than a GB of hard drive).

![FIGURE 9.1 Computer memory hierarchy.](images/fig9_1.jpg)

**FIGURE 9.1**  

Computer memory hierarchy.

Besides, a process needs to be in the main memory in order to get executed so, it has to get swapped in from secondary memory to main memory as depicted in [Fig. 9.2](#12chap_09.xhtml#fig9_2). Simultaneously, for a developer, main memory is easy to use as creating an array, linked list, or set in main memory is easy as compared to writing files in or out by using a Hadoop database or Apache Solr in secondary storage. These upcoming big data technologies are oftenly used in providing accurate analysis and decision making. These technologies provide distributed data storage and parallel processing. Although the distributed database Hadoop with a heavy processing engine (Spark, MapReduce) is good with batch processing framework where the aim is to improve job throughput rather than handling speed of access issue. Notably, the batch processing of data doesn't impose any time constraints so, it can be stored on disk and queries can be processed in batches. Additionally, the popular approach of using SQL for processing queries on database in secondary storage results in high space complexity. For instance, Powerdrill is a column oriented data storage approach that faces the challenge of high memory and computational overhead for large datasets. However, streaming data requires real-time processing with a minimal delay which is possible with improved speed of access. Moreover, streaming data requires processing in a single pass. So, it is always better to work more in main memory for real-time processing of streaming data along with processing data in a single pass. Subsequently, the growing size of databases and applications dataset demands a compact data structure in order to get managed and handled properly.

![FIGURE 9.2 Memory management via swapping.](images/fig9_2.jpg)

**FIGURE 9.2**  

Memory management via swapping.

The current scenario of data generation has resulted in the release of new applications that need to deal with a huge volume of data. Conventional algorithms assumption of fitting data in main memory fails when dealing with such a huge amount of data. In this context, streaming algorithms (that process data in one or a few passes while consuming a limited amount of storage and time) are getting popular among researchers.

Unfortunately, in order to fix above mentioned issue, deterministic data structures, such as hash tables, array, binary search tree fail to deal with large data sets as it is difficult to accommodate large streaming data into memory at once. The conventional data structures can't go on the further side of linear processing. Moreover, for large dataset, a polynomial running time complexity served by deterministic data structures is not beneficial. Also, 3 V's (volume, variety, and velocity) of data demands real-time analysis and processing. Additionally, complexity of data and noise in data is not defined. As size of data is not known in prior, one can't predict the memory requirements for storing data. Therefore, there is a need for an effective data structure that can support quick response time and efficient storage space in the main memory. To address these challenges, probabilistic data structures (PDS) are used recently by many researchers and programmers.

PDS allows performing basic query operation on data in the main memory itself. The use case of PDS is to process big data that does not fit inside the main memory. PDS are used for query operations, such as membership check, frequency check, similarity check, and cardinality check. Low memory requirements and good processing speed are the two unique properties of PDS. Nevertheless, the working of PDS is highly dependent on cryptographic hashing functions that enable randomness and flexibility in inserting data. Hash functions when applied on large data sets summarize it in a compact form which dramatically reduces storage requirements and its behavior is hard to predict. Here, also cryptographic hash functions have to satisfy three main requirements:

*   Work factor: In order to defend brute force, hash function should be computationally expensive.

*   Sticky state: It is impossible to create a state with a plausible input pattern.

*   Diffusion: The associated output bit of hash function should be complex function of each input bit.

Cryptographic hash functions are further categorized into keyed hash functions and unkeyed hash functions. A keyed hash function involves a secret key whereas, for a unkeyed hash function, the key is known to everyone. A keyed hash function is used for message authentication code (MAC).

Notably, PDS's are based on unkeyed hash function. With this insight, the nature of this data structure is randomized because of randomly selected hash functions. Also, in most cases, it is not important to know which item from the set has been matched, sometimes it is necessary to know only whether a match has bee made or not. Hence, only signatures of the items can be stored instead of the value. Over and above, PDS does not result in same structure every time for the same series of operations. Hence, PDS are also known as sketching data structures \[[116](#bib.xhtml#ch00-bib-116)\]. Notably, inaccuracy with a specific structure is expected with PDS. However, they have a constant query processing time and can be easily parallelized (as hashes have independent property) to be used for real-time data processing for a quick response. The coming sections will discuss the membership query, cardinality estimation, similarity search, and frequency estimation PDS in detail along with their Python implementation. Refer to [Fig. 9.3](#12chap_09.xhtml#fig9_3) for taxonomy of PDS.

![FIGURE 9.3 Taxonomy of PDS.](images/fig9_3.jpg)

**FIGURE 9.3**  

Taxonomy of PDS.

Due to minimized memory requirements PDS are useful for big data and streaming data applications.

## [9.2 Deterministic Data Structures vs. Probabilistic Data Structures](#contents.xhtml#rsec9_2)
