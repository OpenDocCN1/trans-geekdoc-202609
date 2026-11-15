detection method, early drift detection method, and drift detection using Hoeffding bounds with moving average and weighted average method, Kolmogorov–Smirnov Windowing method and Page–Hinkley method for concept drift detection.

Evaluation—For evaluation of data stream mining operations in multiflow, three evaluation strategies are present in the multiflow API. These evaluation methods are holdout evaluation, prequential evaluation and prequential evaluation delayed method. Parameters accuracy, kappa, precision, recall, f-measure and gmean are used for the evaluation of classification algorithms in multiflow API. For multi target classification parameters hamming score, hamming loss, exact match and j index are used. For Regression techniques mean square error, mean absolute error and average root mean square error are used. For multi target regression average mean squared error, average mean absolute error and average root mean square error are used.

# ## 4.5.3 Implementation in R

Stream data mining in R programming language is provided using stream package. Stream package is developed by Hahsler _et al._ [18] and provides a simple and nice way for clustering and animation of stream clustering. A sample code snippet for performing data stream clustering is presented in Figure 4.13 along with the output. The cluster visualization sample output is shown in Figure 4.14.

Another code snippet for cluster animation in R is shown in Figure 4.15 and animation output is shown in Figure 4.16.

Stream Generation and Clustering algorithms—BICO (K-means coresets algorithm), BIRCH (Balanced Iterative Reducing Clustering using Hierarchies), DBSCAN (density based clustering algorithm), DBSTREAM, D-Stream, Evolutionary Algorithm, Hierarchical Micro cluster re-clusterer

```
```
>>stream <- DSD_Gaussians(k=5, d=2)
>>stream <- DSC_DStream(gridsize=0.05, Cm=1.5)
>>update(stream, stream, 500)
>>plot(dstream, stream)
>>evaluate(dstream, stream, measure=c("numMicro","numMacro","purity","crand","SSQ"),
...   n = 100)
Evaluation results for micro-clusters.
Points were assigned to micro-clusters.
   numMicroClusters numMacroClusters    purity    cRand        SSQ
25.0000000 5.0000000   0.9145658 0.1286303  0.4904225
```
```

**Figure 4.13** Code snippet for demonstrating stream package from R for stream clustering.