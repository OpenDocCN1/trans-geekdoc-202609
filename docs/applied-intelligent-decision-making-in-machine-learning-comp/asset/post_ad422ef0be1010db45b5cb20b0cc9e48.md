
# Applied Intelligent Decision Making in Machine Learning

Queries

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_12_0.png)

FIGURE 1.1 General stream processing model.

Traditional algorithms developed for offline processing of the data are not suitable for streaming data due to these issues. There are few models that are incremental such as K-nearest neighbors (KNN) and naive Bayes. But, still, these models cannot cope with all the issues present in streaming data. For example, if there is a concept drift in the data, a separate concept-drift detection and alleviation technique needs to be developed. Many researchers have proposed various models for streaming data which takes care of the issues. We will look at some of these techniques in the coming sections.

As shown in Figure 1.1, a stream processor takes as input a stream of data such as 0, 1, 0, 1, ...... The processor can sample from the stream and process it in main memory, such as when answering a query, and the result of the processing can be dumped into the back-end, such as the hard drive, for downstream tasks if required. Most of the algorithms presented in the subsequent sections will be based on this generic model.

Data mining finds application in several domains such as answering queries over the web, sensor data (Das et al., 2019; Dey et al., 2019), analyzing network packets, patient health monitoring, and surveillance systems to name a few. Because of the vast area of the field, I will present some selected case studies in the field at the end of the chapter.

The rest of the chapter are Research issues related to stream mining are discussed in Section 1.2. Section 1.3 elucidates the simple problems in streaming data such as filtering and counting. Sampling from a data stream is explained in Section 1.4, followed by concept drift detection in Section 1.5. Finally, the chapter ends with a discussion and an open problem in Section 1.6.

## 1.2 RESEARCH ISSUES IN DATA STREAM MINING

Knowledge discovery from a data stream is a challenging task due to reasons mentioned in the previous section. Most challenging is the unbounded size of the stream, low memory, and fast arrival rate. As a result, techniques proposed in the literature rely on to summarize the data stream in some way. The Following are the techniques often employed to handle data streams.

# Data Stream Mining for Big Data

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_13_0.png)

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_13_1.png)

**FIGURE 1.2** (Left) Top figure is a landmark window and bottom figure is a sliding window (used in packet transmission). (Right) Timestamp-based windows. Top figure is a natural tilted window and bottom figure is a logarithmic time window.

- 1. **Approximate query processing (AQP)** is described as the following rules (Chaudhuri et al., 2017): (a) a query language should be generic enough to retrieve all the relevant information, (b) should have a low error rate and high accuracy, (c) the work should be saved at runtime, and (d) extra resources should be made for pre-computation. These dimensions of an AQP scheme are not independent and much of the previous literature makes specific choices along the four dimensions. AQP can be broadly classified into two main categories: (a) online aggregation, which is a sampling in an online manner with samples to answer queries, and (b) offline synopses generation, which is based on some statistics of the data and then answers queries (Li and Li, 2018).

- 2. **Sliding window query processing** is a model of handling a data stream with the assumption that recent items are more important than the older ones. There are two types of sliding window based on how they are defined.

- **Sequence-based sliding window** is defined by the number of observations that determine the window size. These are further divided into *landmark sliding window* and *moving sliding window*, as shown in Figure 1.2 (left).

- **Timestamp-based sliding window**: In this case, the sliding window is determined on the number of observations made in a given time interval and window-width is determined based on the time. They are further categorized into *natural-tilted time window* and *logarithmic time window*, as shown in Figure 1.2 (right).

As we see, some algorithms based on the sliding window guarantee an error rate of approximation to any desired accuracy $\epsilon$. One of the most popular algorithms in this category is the DGIM method (Rajaraman and Ullman, 2011) for counting 1s in a bit stream.

- Sampling is another popular approach for making an approximation of the streaming data. (a) when to sample and (b) how to make that the sample is an unbiased estimator of the original stream. For example, there are many ways of doing sampling. random uniform sampling and reservoir sampling are some of the popular approaches used on the data.

In the forthcoming sections, I present algorithms for some basic tasks in data stream mining, sampling from the data stream, and concept-drift detection in data streams. For other tasks, such as classification, clustering, frequent pattern mining, and novelty detection in data stream mining, the interested reader is referred to Gama (2010) and Aggarwal (2007).

## 1.3 FILTERING AND COUNTING IN A DATA STREAM

In this section, we discuss algorithms for filtering items which satisfy a property and others which count in a data stream.

### 1.3.1 BLOOM FILTERS

Bloom filters are one of the most popular approaches for filtering an item from a data stream. Applications of bloom filters include checking if a user-id is available for sign-up, keeping track of web-pages visited by a user, and recent email addresses used to send messages. A bloom filter consists of three things (Rajaraman and Ullman, 2011).

- A A bit array of length n initialized to 0.
- A number of hash functions $h_1, h_2, ..., h_i$. Each hash function maps 'keys' to bit-array value by setting the bit.
- A set of m keys.

We will use an application of the bloom filter to sign-up at various platforms for finding user-ids. A bloom filter gives guarantees of the form: if a user-id is available, it's 100% of its answer. On the other hand, if a user-id is not available, it gives a probabilistic answer to the query. Let us see this in action. A bloom filter is shown in Figure 1.3. If there are two hash functions $h_1$ and $h_2$ which can map a given string to the bit-array. Suppose the strings 'cow' and 'chicken' are mapped to (6,3) and (2,1). Bits at these locations are set to 1 in the bit-array. Now suppose a query for string 'pigeon' is issued. If the hash functions generate 0 and 3, then we see that at location 0 is not set. This means 'pigeon' can be used as a user-id. However, if the hashes generated were, (2,3), then it means that 'pigeon' may already be taken as a user-id which the bloom filter is not sure

# Data Stream Mining for Big Data

| 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
|---|---|---|---|---|---|---|---|
| 0 | 1 | 0 | 0 | 1 | 1 | 1 | 0 |

h1 6 2 0
h2 3 1 3
Cow Chicken Pigeon

**FIGURE 1.3** Hashing items in a bit-array. $h_1$ and $h_2$ are hash functions.

about. The reason is that some other strings might have the same bit locations as “pigeon” in this scenario and there is no way to be sure who is set for. For this reason, it’s impossible to detect the user-id using a bit-array. To solve this problem, another variation of the bloom filter which uses *counts* of the “strings” to a location is used. Such bloom filters are called *count-bloom filters*. Some important points to note while designing bloom filters are the following:

- 1. The size of the bloom filter is very important. The smaller the bloom filter, the larger the false positive (FP) and vice versa.
- 2. The larger the number of hash functions, the quicker the bloom filter fills, as well as slow filter. Too few hash functions results in too many FPs, unless all *good hash functions*.

A visualization of the FP rate with the number of hash functions is given in Figure 1.4. As we can see, as the number of hash functions grows, the FP rate declines sharply. For a more in-depth analysis of the bloom filter, the reader is referred to Rajaraman and Ullman (2011).

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_15_0.png)

**FIGURE 1.4** Effect of the number of hash functions on the false positive rate. Image source: Bhat (2016).
