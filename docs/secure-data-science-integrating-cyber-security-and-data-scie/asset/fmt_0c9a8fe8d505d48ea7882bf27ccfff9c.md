
### 15.6.1.3 Hardware

We have a 10-node Hadoop cluster which we use for our framework. Each of the nodes has the following configuration: Pentium IV 2.80 GHz processor, 4 GB main memory, and 640 GB disk space. We ran Jena, RDF-3X, and BigOWLIM frameworks on a powerful single machine having 2.80 GHz quad core processor, 8 GB main memory, and 1 TB disk space.

### 15.6.1.4 Software

We used `Hadoop-0.20.1` for our framework. We compared our framework with `Jena-2.5.7`, which used `MySQL 15.12` for its SDB model. We used `BigOWLIM` version `3.2.6`. For `RDF-3X`, we utilized version `0.3.5` of the source code.

### 15.6.2 Evaluation

We present performance comparison between our framework, `RDF-3X`, `Jena` In-Memory and SDB models, and `BigOWLIM`. More details are found in `[HUSA2011a]`. We used three LUBM datasets: 10,000, 20,000, and 30,000 which have more than 1.1, 2.2, and 3.3 billion triples, respectively. Initial population time for `RDF-3X` took 655, 1,756, and 3,353 minutes to load the datasets, respectively. This shows that the `RDF-3X` load time is increasing exponentially. LUBM (30,000) has three times as many triples as LUBM (10,000) yet it requires more than five times as long to load.

For evaluation purposes, we chose LUBM Queries 1, 2, 4, 9, 12, and 13 to be reported in this work. These queries provide a good mixture and include simple and complex structures, inference, and multiple types of joins. They are representatives of other queries of the benchmark and so reporting only these covers all types of variations found in the queries we left out and also saves space.

Query 1 is a simple selective query. `RDF-3X` is much faster than `HadoopRDF` for this query. `RDF-3X` utilizes six indexes `[NEUM2008]` and those six indexes actually make up the dataset. The indexes provide `RDF-3X` a very fast way to look up triples, similar to a hash table. Hence, a highly selective query is efficiently answered by `RDF-3X`.

Query 2 is a query with complex structures, low selectivity, and no bound objects. The result set is quite large. For this query, `HadoopRDF` outperforms `RDF-3X` for all three dataset sizes. `RDF-3X` fails to answer the query at all when the dataset size is 3.3 billion triples. `RDF-3X` returns memory segmentation fault error messages and does not produce any query results.

Query 4 is also a highly selective query, that is, the result set size is small because of a bound object in the second triple pattern but it needs inferencing to answer it. The first triple pattern uses the class `Person` which is a superclass of many classes. No resource in LUBM dataset is of type `Person`, rather there are many resources which are its subtypes. `RDF-3X` does not support inferencing so we had to convert the query to an equivalent query having some union operations. `RDF-3X` outperforms `HadoopRDF` for this query.

Query 9 is similar in structure to Query 2 but it requires significant inferencing. The first three triple patterns of this query use classes which are not explicitly instantiated in the dataset. However, the dataset includes many instances of the corresponding subclasses. This is also the query which requires the largest dataset join and returns the largest result set out of the queries we evaluated. `RDF-3X` is faster than `HadoopRDF` for 1.1 billion triples dataset but it fails to answer the query at all for the other two datasets.

Query 12 is similar to Query 4 because it is both selective and has inferencing in one triple pattern. `RDF-3X` beats `HadoopRDF` for this query.

Query 13 has only two triple patterns. Both of them involve inferencing. There is a bound subject in the second triple pattern. It returns the second largest result set. `HadoopRDF` beats `RDF-3X` for this query for all datasets. `RDF-3X`'s performance is slow because the first triple pattern has very low selectivity and requires low selectivity joins to perform inference via backward chaining.

These results lead us to some simple conclusions. `RDF-3X` achieves the best performance for queries with high selectivity and bound objects. However, `HadoopRDF` outperforms `RDF-3X` for queries with unbound objects, low selectivity, or large dataset joins. `RDF-3X` cannot execute the two queries with unbound objects (Queries 2 and 9) for a 3.3 billion triples dataset. This demonstrates that `HadoopRDF` is more scalable and handles low selectivity queries more efficiently than `RDF-3X`.

We also compared our implementation with the `Jena` In-Memory, the SDB and `BigOWLIM` models. Due to space and time limitations, we performed these tests only for LUBM Queries 2 and 9 from the LUBM dataset. We chose these queries because they have complex structures and require inference. It is to be noted that `BigOWLIM` needed 7 GB of Java heap space to successfully load the billion triples dataset. We ran `BigOWLIM` only for the largest three datasets as we are interested in its performance with large datasets. For each set we obtained the results for the `Jena` In-Memory model, `Jena` SDB model, our `Hadoop` implementation and `BigOWLIM`, respectively. At times the query could not complete or it ran out of memory. In most of the cases, our approach was the fastest.

For Query 2, `Jena` In-Memory and `Jena` SDB models were faster than our approach, giving results in 3.9 and 0.4 seconds, respectively. However, as the size of the dataset grew, the `Jena` In-Memory model ran out of memory space. Our implementation was much faster than the `Jena` SDB model for large datasets. For example, for 110 million triples, our approach took 143.5 seconds as compared to about 5,000 seconds for `Jena` SDB model. We found that the `Jena` SDB model could not finish answering Query 9. `Jena` In-Memory model worked well for small datasets but became slower than our implementation as the dataset size grew and eventually ran out of memory.

For Query 2, `BigOWLIM` was slower than ours for the 110 and 550 million datasets. For the 550 million dataset, it took 22693.4 seconds, which is abruptly high compared to its other timings. For the billion triple dataset, `BigOWLIM` was faster. It should be noted that our framework does not have any indexing or triple cache whereas `BigOWLIM` exploits indexing which it loads into main memory when it starts. It may also prefetch triples into main memory.

For Query 9, our implementation is faster than `BigOWLIM` in all experiments.

It should also be noted that our `RDF-3X` and `HadoopRDF` queries were tested using cold runs. What we mean by this is that main memory and file system cache were cleared prior to execution. However, for `BigOWLIM`, we were forced to execute hot runs. This is because it takes a significant amount of time to load a database into `BigOWLIM`. Therefore, we will always easily outperform `BigOWLIM` for cold runs. So, we actually tested `BigOWLIM` for hot runs against `HadoopRDF` for cold runs. This gives a tremendous advantage to `BigOWLIM`, yet for large datasets, `HadoopRDF` still produced much better results. This shows that `HadoopRDF` is much more scalable than `BigOWLIM`, and provides more efficient queries for large datasets.
