
the transition part of all segments, which have been created due to configuration changes, gets truncated. If segments become smaller than a predefined threshold, they can be ignored in the upcoming phases.

### 3.3 Feature Extraction

Having a set of segments for each configuration, the next step is to determine the characteristics of all segments. While the literature presents multiple approaches to describe the behavior of time series, we will focus on common statistical features extracted from each segment. Nonetheless, the choice of features is not fixed, which is why any feature suitable for the individual application scenario can be used. One example for rather complex features could be the result of a kernel fitting in the context of Gaussian processes, accepting a decrease in performance. Since the goal is to capture comparable characteristics of a segment, we compute different real-valued features and combine them in a vectorized representation. In the case of COMPOSITION, we used the mean to describe the average level, the variance as a measure of fluctuation and the lower and upper quartiles as a coarse distribution-binning of values. Due to the expressiveness of features being dependent from the actual data, one possible way to optimize the selection of features is the Principal Component Analysis [6]. Simply using a large number of features to best possibly cover the variety of characteristics might have a negative influence on the measurement of dissimilarity. The reason for this is the partial consideration of irrelevant features within distance computations.

Moreover, since thresholds could be regarded as a more intuitive solution compared to additionally extracted features, this replacement would lead to a significant decrease in the number of recognized anomalies. Apart from the sensitivity to outliers, the reason is a neglect of the inherent behavior of a time series. As an example consider the measurements of an acoustic sensor attached to a motor that recently is sending fluctuating measurements, yet within the predefined tolerance. Although the recorded values are still considered as valid, the fluctuation with respect to the volume could already indicate a nearly defect motor. Finally, one initially needs to evaluate appropriate thresholds for any parameter of each configuration.

### 3.4 Dissimilarity Measurement

For now we discussed the exploitation of inherent information, extracted from segmented time series. The final step of GADPL is to measure the level of dissimilarity for all obtained representatives. Since no ground truth is available to define the default behavior for a specific configuration, the algorithm uses an approximation based on the given data. One problem in this regard is the variability of a default behavior, consisting of more than one pattern. Therefore, a naive approach as choosing the most occurring representative would already fail for a time series consisting of two equally appearing patterns captured by different segments, where consequently half of the data would be detected as

```
Algorithm 1 GADPL
Require: Time series T, Machine parameters M, Configuration transition time p,
Segment length (l_min, l_max), Number of nearest neighbors k,
Dissimilarity threshold Delta_max
C' = cluster_configurations(T, M)
R' = {R_1, .., R_|C'|}
for all configuration segments C_i in C' do
  for all segments s_j in C_i do
    s_j = truncate_transitions(s_j, p)
    if |s_j| < l_min then
      C_i = C_i \ s_j
    else if |s_j| > l_max then
      s'_j = split_segments(s_j, l_max)
      C_i = C_i U s'_j
      C_i = C_i \ s_j
    end if
    R_i = R_i U extract_features(s'_j)
  end for
end for
for all configuration representatives R_i in R' do
  for all representatives r_j in r_i do
    NN_k = query_index(r_j, k)
    if Delta(r_j, NN_k) > Delta_max then
      emit_anomaly(i, j)
    end if
  end for
end for
```

anomalous behavior.

As one potential solution GADPL instead uses the mean over a specified size of nearest neighbors, depicting the most similar behavior according to each segment. The idea is that even though there might multiple distinct characteristics in the data, at least a predefined number of elements represent the same behavior compared to the processed item. Otherwise, this item will even have a high average dissimilarity with respect to the most similar observations and can therefore be classified as anomaly.

Let $r_i$ be the representative vector of the i-th segment obtained by feature extraction and let $NN_k(r_i)$ be the according set of $k$ nearest neighbors. The dissimilarity measure $\Delta$ for $r_i$ is defined as:

```
\(\Delta(r_i, NN_k(r_i)) = \frac{1}{k} \sum_{j=1}^k \delta(r_i, NN_k^j(r_i))\)
```

where $NN_k^j(r_i)$ corresponds to the $j$-th nearest neighbor and $\delta$ to a ground distance defined on $\mathbb{R}^n$.

Here, for the vectorized feature representations, any suitable distance function \(\delta\) is applicable. In the context of COMPOSITION we decided to use the Euclidean distance for a uniform distribution of weights, applied to normalized

![](img/a2f5eed6507498d886a06be86239344b_30_0.png)

Fig. 1. Application of GDPL: The upper part shows the segmentation of time annotated power consumption data in percent. The lower part illustrates the result of the dissimilarity measurement, where the red rectangle indicates classified anomalies.

feature values. To further increase the performance of nearest neighbor queries, we exploited the R*-tree [1] as a high-dimensional index structure.
Given the dissimilarity for each individual representative together with a predefined anomaly threshold, GDPL finally emits potential candidates having an anomalous behavior.

## 4 Evaluation

In this section we will discuss the evaluation performed on a historical data set, provided in the scope of COMPOSITION. While in future, the algorithm should be applied to continuously streamed sensor data, the initial evaluation was performed on recorded data, captured over a period of seven years. The data consists of machine parameters (already classified by recipe names) and time-annotated sensor measurements including temperature value and power consumption, based on a sampling rate of 5 minutes. In addition, a separate maintenance log covers the dates of previous fan exchanges. However, malfunctions only occurred two times during runtime and are therefore comparatively rare. A confirmation of results due to actual defect components is consequently restricted to some extent. Since this project and the here presented approach are regarded as ongoing work, the outlined evaluation is continuing likewise.
Figure 1 illustrates the application of GDPL, including segmentation (upper part) and dissimilarity measurement (lower part), for the time around one fan failure. Here, differently colored circles represent slices of the time series after segmentation, describing the percentage power consumption of a fan. Using the features mentioned in section 3.3, we intended to perceive deviating values and untypical fluctuations within the data, without being sensitive to outliers arising from single incorrect sensor measurements. Having one of the recorded fan exchanges at the end of February 2012, the result of the algorithm clearly shows significantly higher values for the dissimilarity (red rectangle) prior to the event. Even though increased dissimilarity values at the end of May 2011 and around September 2011 can be explained by analyzing the original data, yet there were no recordings for a defect component at those times. However this does not automatically imply incorrect indications, since defect machine parts are not the only reasoning for anomalous characteristics in the data. An appropriate choice for the value of a maximal dissimilarity, defining the anomaly threshold, can therefore highly influence the accuracy.
Both cases of a defect fan behavior were clearly captured by the algorithm and emphasized by a high dissimilarity.

## 5 Conclusion

With GADPL we introduced a solution to the relevant topic of unsupervised anomaly detection in the context of configuration-based production lines. After a short outline on the topic and related work, we discussed the algorithm and the associated intention of our approach, before briefly showing the evaluation results based on the project data.
Since the approach is ongoing work, in the future we will primarily extend our evaluation based on streaming data. Although we described the algorithm using historical data, the procedure for streaming data is carried out analogous. Another point in the scope of future evaluations is the choice of more complex features and a related automated feature selection. Another idea to further improve the approach is a semantic segmentation of the time series. While currently a time series is segmented exploiting domain knowledge, a segmentation based on characteristics in the data might potentially increase the accuracy. This would also prevent from an unappropriated choice of the maximal segmentation length, which could result in a split of data within a potential motif.
Finally, we plan to investigate the correlation of anomalies within multivariate data. If GADPL in its current state is used for multivariate time series data, each dimension is processed independently. Combining inter-dimensional information within a single dissimilarity measure to cover anomalies would therefore be a useful functionality to further optimize the approach.

## 6 Acknowledgements

This project has received funding from the European Unions Horizon 2020 research and innovation programme under grant agreement No 723145 - COMPOSITION. This paper reflects only the authors views and the commission is not responsible for any use that may be made of the information it contains.
