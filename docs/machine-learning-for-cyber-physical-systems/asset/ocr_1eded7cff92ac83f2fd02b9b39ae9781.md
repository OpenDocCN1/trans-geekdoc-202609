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

As one potential solution GADPL instead uses the mean over a specified size
of nearest neighbors, depicting the most similar behavior according to each seg-
ment. The idea is that even though there might multiple distinct characteristics
in the data, at least a predefined number of elements represent the same be-
havior compared to the processed item. Otherwise, this item will even have a
high average dissimilarity with respect to the most similar observations and can
therefore be classified as anomaly.

Let $r_i$ be the representative vector of the i-th segment obtained by feature ex-
traction and let $NN_k(r_i)$ be the according set of $k$ nearest neighbors. The dis-
similarity measure $\Delta$ for $r_i$ is defined as:

```
\(\Delta(r_i, NN_k(r_i)) = \frac{1}{k} \sum_{j=1}^k \delta(r_i, NN_k^j(r_i))\)
```

where $NN_k^j(r_i)$ corresponds to the $j$-th nearest neighbor and $\delta$ to a ground dis-
tance defined on $\mathbb{R}^n$.

Here, for the vectorized feature representations, any suitable distance function
\(\delta\) is applicable. In the context of COMPOSITION we decided to use the Eu-
clidean distance for a uniform distribution of weights, applied to normalized