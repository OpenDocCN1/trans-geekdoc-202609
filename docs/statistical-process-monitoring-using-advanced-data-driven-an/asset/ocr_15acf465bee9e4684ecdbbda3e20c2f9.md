![](bbox=[0.143, 0.106, 0.865, 0.268])

FIGURE 8.5 Illustration of the DSA-based kNN obstacle detection method.

where $X$ is the input ($n \times m$) normalized V-disparity matrix and $\hat{X}$ is the reconstructed V-disparity matrix via the built model of size ($n \times m$).

Stage 2. The obstacle detection phase involves evaluating the features extracted through DSA using the kNN scheme, which is an efficient nonparametric algorithm for separating different features (Fig. 8.5). Briefly, the kNN algorithm separates normal features from abnormal features (to identify inliers from outliers) by measuring the distance between the actual observation and the kNNs of obstacle-free data. The kNN scheme are applied by computing all distances, \(d_j\), in elements of the training set, \(S\), using the following equation, \(d_j = \text{distance}(x, S_J)\). The kNN distances with large values are used as indicators of obstacles in front of the vehicle. Euclidean distance is often used to measure similarity in kNN-based approaches. In scenes with no obstacles in front of the vehicle, the kNN distance fluctuates near zero, and in scenes with obstacles, the kNN distance significantly diverges from zero. Hence, large kNN distances indicate that there is a significant inconsistency between new observations and the training (obstacle-free) observations. Specifically, for every observation \(x_i\) (output of the DSA) in the training data, the kNN distances to its nearest neighbor in the training data, \(D_i\), are determined, based on which the sample distributions of distances can be computed:

```
\(\begin{aligned} D_i = \sum_{j=1}^{k} d_{ij}, \end{aligned}\) (8.4)
```

where \(d_{ij}\) is the distance from an observation to its \(j\)th nearest neighbor. The goal is to find obstacles at any time point within an observed scene using image pairs (left and right). This can be done by creating a detection threshold or control limit that distinguishes between free and busy scenes. We utilize the 3-sigma rule to fix the detection threshold, UCL, based on the kNN distance. In other words, we aim to