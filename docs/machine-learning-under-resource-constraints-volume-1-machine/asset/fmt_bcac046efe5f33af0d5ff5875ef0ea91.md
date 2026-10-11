
![Fig. 6.12 Lane activity profile with push-down parallelism to consolidate expansion divergence.](graphic/b_9783110785944-006_fig_012.png)

Fig. 6.12 Lane activity profile with push-down parallelism to consolidate expansion divergence.

![Fig. 6.13 Execution times of DogQC for TPC-H benchmark queries (scale factor 25). The divergence optimizations improve query performance.](graphic/b_9783110785944-006_fig_013.png)

Fig. 6.13 Execution times of DogQC for TPC-H benchmark queries (scale factor 25). The divergence optimizations improve query performance.

### 6.2.4 Evaluation

With `DogQC`, we provide a query compiler with a wide range of SQL functionality, sufficient to support all queries from the TPC-H benchmark set. Here we use `DogQC` and the database domain to illustrate the aforementioned anti-divergence mechanisms, which could equally be applied to other data-intensive tasks, including those related to machine learning.

#### 6.2.4.1 TPC-H Performance

To assess the benefits of measures to contain divergence, we performed a series of measurements with the TPC-H benchmark set. Our measurements were based on an NVIDIA RTX2080 GPU with 46 Streaming Multiprocessors and 8 GB GPU memory, installed in a host system with an Intel i7-9800X GPU and 32 GB of main memory. As a reference, we compared `DogQC` with the hybrid CPU/GPU system `OmniSci` [[545]](#backmatter-001.xhtml#b_9783110785944-010_ref_545).

Our benchmark results are depicted in [Figure 6.13](#9783110785937_066530.xhtml#b_9783110785944-006_fig_013). For each of the 22 TPC-H queries, the bars indicate the query execution time assuming that the dataset is resident in GPU memory.

For `OmniSci`, we report the total wall clock time needed to execute the query as well as the amount of time spent on GPU processing. `OmniSci` is a hybrid execution engine in which both CPU and GPU will be used to jointly answer the query. As can be seen in [Figure 6.13](#9783110785937_066530.xhtml#b_9783110785944-006_fig_013), several queries can, in fact, not benefit much from GPU in `OmniSci`. Also note that `OmniSci` could successfully execute only 13 of the 22 TPC-H benchmark queries. `DogQC`, by contrast, can run all 22 TPC-H queries entirely on the GPU, with execution times that are up to 86× faster than those of `OmniSci`.

### 6.2.5 Summary

In this research, we put the processing capabilities of data-parallel co-processors for non-uniform, data-intensive workloads to the test. `DogQC` introduces techniques that allow us to gracefully align parallel processing units with work items, even when problems are heavily skewed. We observe that `Lane Refill` and `Push-Down Parallelism` are able to increase processing efficiency for these non-uniform workloads, sometimes with dramatic effects on processing throughput.

Existing query coprocessors typically avoid imbalances by working on a uniform surrogate (such as dictionary keys or materialization barriers). This has led to the perception that GPUs have limited capabilities of processing irregular problems. `DogQC` avoids the overhead of maintaining such additional data structures and instead restores balance during non-uniform processing.

Here we showcase `Lane Refill` and `Push-Down Parallelism` based on an application to database query processing. Compared with state-of-the-art platforms, our prototype `DogQC` achieves better resource utilization, a bigger functionality range, and better runtime performance on realistic benchmarks. Looking ahead, our anti-divergence measures could be applicable to many machine learning scenarios, especially when the problems involved are heavily skewed and/or depend on non-linear computations.

## 6.3 Extreme Multicore Classification

*Erik Schultheis*

*Rohit Babbar*

**Abstract:** There are classification problems, such as assigning categories to a Wikipedia article, where the possible set of labels is very large, numbering in the millions. Somewhat surprisingly, these so-called Extreme-Multilabel Classification (XMC) problems can be solved quite successfully by applying a linear classifier to each label individually. This decomposition into binary problems is called a one-vs-rest reduction. As these problems are completely independent, the reduced task is embarrassingly parallel and can be trivially spread across multiple cores and nodes. After training, the model can be sparsified by culling small weights to only require a fraction of the memory and computational power for prediction on new samples.

### 6.3.1 Introduction to Extreme Multilabel Classification

Extreme Multi-label Classification (XMC) refers to supervised learning with a large target label set where each training/test instance is labeled with a small subset of relevant labels. Machine learning problems consisting of hundreds of thousands of labels are common in various domains such as annotating web-scale encyclopedias [[585]](#backmatter-001.xhtml#b_9783110785944-010_ref_585), hashtag suggestion in social media [[171]](#backmatter-001.xhtml#b_9783110785944-010_ref_171), and image-classification [[168]](#backmatter-001.xhtml#b_9783110785944-010_ref_168). For instance, all Wikipedia pages are tagged with a small set of relevant labels that are chosen from more than a million possible tags in the collection. It has been demonstrated that, in addition to automatic labelling, the framework of XMC can be leveraged to effectively address learning problems arising in recommendation systems, ranking, and web-advertising [9, 585].

**Notation and Setup** Let the training data `D` := {(`x`^((1)), `y`^((1))), ..., (`x`^((`N`)), `y`^((`N`)))} consist of input feature vectors `x`[(`i`)] *∈* 𝒳 *⊆* **ℝ**[`d`] and respective output vectors `y`[(`i`)] *∈* 𝒴 := {0, 1}[`m`] such that `y`[`l`]^((`i`)) = 1 iff the `l`-th label belongs to the training instance `x`[(`i`)]. The feature vectors form the rows of the feature matrix `X`. In XMC settings, the cardinality `m` of the set of target labels, the dimension of the input `d`, and the size of the dataset `N` can all be of the order of hundreds of thousands or even millions.

For text data, the input can be represented by term-frequency inverse-document-frequency (tf-idf) features. In that case, the dimensionality of the feature space is determined by the size of the vocabulary, and for each text `x` *∈* 𝒳 the feature `x`[`j`] is nonzero only if the corresponding word appears in the text. As a result, the input features are highly sparse. The magnitude of the feature is determined by how often the word appears in the document and in the entire corpus. For details on tf-idf, see, e.g., Manning, Raghavan, and Schütze [[463]](#backmatter-001.xhtml#b_9783110785944-010_ref_463).

![Fig. 6.14 Label frequency in XMLC datasets. X-axis shows the label rank when sorted by the frequency of positive instances and Y-axis gives the number.](graphic/b_9783110785944-006_fig_014.png)

Fig. 6.14 Label frequency in XMLC datasets. X-axis shows the label rank when sorted by the frequency of positive instances and Y-axis gives the number.

Similarly, for any given instance `x`[(`i`)] only a small subset of the labels will be relevant, `‖y`[(`i`)]`‖`[1] *≪ m*. Additionally, the number of instances for which a label is relevant is very imbalanced: Few labels will be relevant to many instances, but most labels will apply only to an extremely small fraction. This gives rise to a *long-tailed* label distribution, as shown in [Figure 6.14](#9783110785937_066530.xhtml#b_9783110785944-006_fig_014). The labels with very few positives are called *tail labels*. The characteristics of well-known benchmark datasets in XMC are presented in [Table 6.4.](#9783110785937_066530.xhtml#b_9783110785944-006_tab_004)
