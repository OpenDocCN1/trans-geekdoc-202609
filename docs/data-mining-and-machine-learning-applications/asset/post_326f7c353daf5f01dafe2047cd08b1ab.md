
Stream (ASPMS) algorithm. Apriori is the oldest, popular and simplest algorithm for finding the frequent itemsets from a database or from a data stream. It uses the concept of apriori property which states that all the subsets of a frequent itemset are also frequent or it can also be stated that if any subset is not frequent then all its supersets can also be non-frequent. Using this property and counting the frequency of individual items in the database or data stream frequent itemsets can be generated. The only problem with apriori algorithm is more numbers of database scans are required. FP growth algorithm only takes two scans of database for finding the frequent itemsets. It works on a special data structure called a frequent pattern tree (FP-Tree) which stores the items along with its frequencies from which frequent itemsets are mined. RARM computes tries itemsets for finding the frequent itemsets, using the tries generated from the input data stream frequent itemsets are generated. In Equivalence Class Transformation (ECLAT) algorithm items along with the list of transactions are maintained and processing is performed on the basis of list of transactions rather than on items. ASPMS algorithm is specifically designed for the wireless sensor network data which uses a specific data structure known as sensor pattern stream tree. Then using a suitable size of window and batch by batch processing frequent patterns can be generated from the sensor pattern stream tree. It is shown that the algorithm performance and selection depends on number of parameters such as number of database scans, execution time and memory requirements.

## 4.5 Tools & Techniques

In this section various tools and techniques available on different platforms are discussed for implementing the stream data mining operations. Almost every platform supports the following essential functionalities for implementing stream data mining operations:

- 1. Stream Generation: Stream generation is an important activity provided in stream data mining tools, using its various types of streams can be generated for simulating the stream data mining operations.
- 2. Classification: Various types of classification algorithms provided for categorizing the data streams.
- 3. Clustering: Various types of clustering algorithms provided for grouping the data streams. Few tools also provide the functionalities of outlier detection in stream data to handle noise in data streams.
- 4. Concept Drift Detection: Concept drift detection is a critical operation in handling data streams. As discussed earlier data streams take a theoretically infinite memory so processing it is a complex task and an analyst needs to identify the cut-off points (known as concept drifts) from where the stream changes and make impact on stream mining operations. So concept drift detection mechanism is also provided by most of the data stream mining tools.

Apart from the above mentioned functionalities, a few other utilities and supporting operations are also provided in the tools dealing with the data stream mining.

### 4.5.1 Implementation in Java

Stream mining implementation in Java is provided through a MOA platform which is developed by Bifet et al. [16]. MOA is Massive Online Analysis platform and is developed by the Waikato University who has earlier developed the WEKA (Waikato Environment for Knowledge Analysis) tool. MOA provides a standard framework for stream mining and includes most of the basic operations for stream mining such as classification, regression, cluster analysis, detection of concept drifts and generation of data streams.

Stream Generators in MOA—MOA supports a number of stream generation algorithms. It includes the Agrawal Generator, Hyperplane Generator, LED Generator, Random RBF Generator, Random Tree Generator, SEA Generator, Stagger Generator and Waveform Generator. In order to generate a particular data stream using any generator some configuration settings are required where user needs to set the value of few parameters. Typically the settings of configuration parameters are namely, instance limit, time limit, sample frequency, memory check frequency, width and alpha are required for generating a particular data stream. A snapshot of configuring settings for generating a data stream is shown in Figure 4.2.

Classifiers—Classification is a key operation in data mining. It is used for categorizing data elements in a collection of data. Various classification models available in MOA are shown in Figure 4.3. It provides the implementation of all standard and popular classification algorithms such as Naive Bayes, SAMkNN, OzaBag, Adaptive Random Forest and Hoeffding Tree.

![](img/48ffcb334b2fea865a1f194394911123_127_0.png)

Figure 4.2 Configuration settings for stream generators in MOA.

![](img/48ffcb334b2fea865a1f194394911123_127_1.png)

Figure 4.3 Learning models for various classifiers in MOA.

Parameters—In order to evaluate the performance of classifiers in MOA, various performance measures are supported. Evaluation measures are shown in Figure 4.4. Performance parameters accuracy, Kappa, time and memory can be evaluated for the selected stream classifiers.

Clustering—Clustering is the process of grouping the similar objects. For stream mining, clustering can be applied to create the groups of objects coming from a stream. The clustering window of MOA is shown in Figure 4.5. User can select the stream generator, clustering algorithm and performance parameter from this window.

| Measure | Current | Mean |
|---|---|---|
| Accuracy | 80.60 | 80.59 |
| Kappa | 70.90 | 70.88 |
| Kappa Temp | 70.15 | 71.00 |
| Ram-Hours | 0.00 | 0.00 |
| Time | 51.42 | 25.99 |
| Memory | 0.01 | 0.01 |

Figure 4.4 Performance Parameters for Evaluating Classifiers in MOA.

![](img/48ffcb334b2fea865a1f194394911123_128_0.png)

Figure 4.5 Clustering window of MOA for data stream clustering.

Clustering algorithms available in MOA are presented in Figure 4.6. MOA provides the implementation of clustering algorithms like Cluster Generator, CobWeb, ClusTree, Clustream, StreamKM, etc.

Parameters—In order to evaluate the performance of clustering algorithms, numerous parameters are provided by MOA. The list of clustering performance parameters are shown in Figure 4.7. Performance parameters namely, CMM, entropy, purity, precision, recall, number of clusters, time, memory and sum of square error, etc. can be evaluated for evaluation of clustering algorithms in MOA.

Apart from the clustering algorithms and performance parameters, MOA also provides the visualization of stream clusters with the help of clustering visualization window shown in Figure 4.8. Cluster centers, population density and cluster overlapping kind of information can be visualized using the visualization tool of MOA in Java.

Concept Drift—Concept drift window of MOA implementation is shown in Figure 4.9. User can select a particular concept drift detection technique for a data stream and evaluate the performance of it.

Active Learning—MOA also supports the implementation of active learning algorithms shown in Figure 4.10. User can generate any type of data stream, apply the active learning algorithm and select the performance parameters for evaluating the algorithms in this window.

Outlier Detection—Outlier detection and outlier visualization window in MOA is shown in Figures 4.11 and 4.12 respectively. Here user can also select any outlier detection algorithm and stream generator to evaluate any outlier detection technique in a data stream. Just like cluster visualization interface, outlier visualization interface is also provided in the Java MOA for outlier visualization in a data stream.
