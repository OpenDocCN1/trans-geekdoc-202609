
### 3.4 A Simple and Practical Predictor

We now introduce a simple and practical noisy ranking predictor. That is, we describe a temporal min-degree predictor which can be built efficiently with a single pass on the input stream, and can be used within our algorithm STEP. We define the temporal degree of node \( u \in V \) within a time interval \( [t_a, t_b] \) as \( d(u, t_a, t_b) = |\{(x, y, t') \in E : (x = u \text{ or } y = u) \text{ and } t' \in [t_a, t_b]\}| \). That is, the temporal degree is the number of edges incident to \( u \) within the given time interval. Next, given a temporal edge \( e = (u, v, t) \in E \) and a time duration \( \delta \) let \( w_{\text{m-d}}(e) = \min \{d(u, t - \delta, t + \delta), d(v, t - \delta, t + \delta)\} \) be the temporal min-degree weight. That is, \( w_{\text{m-d}}(e) \) is the minimum between the temporal degrees of the nodes of edge \( e \). Intuitively, the temporal min-degree weight accounts for the temporal activity of nodes over the graph, which is crucial for our goal of designing a highly accurate predictor for STEP. Let \( \mathbf{W}^{\text{m-d}} \) be the edges \( e \in E \) ordered by non-increasing values of their weight \( w_{\text{m-d}}(e) \), ties broken arbitrarily. Then, for any edge \( e \in E \), the temporal min-degree ranking predictor classifies \( \mathcal{Q}(e)_K = 1 \) if \( e \) is within the first \( K \) edges of \( \mathbf{W}^{\text{m-d}} \), and \( \mathcal{Q}(e)_K = 0 \) otherwise. Therefore, the temporal min-degree predictor uses the temporal min-degree weights \( w_{\text{m-d}}(e) \) as a proxy for the unknown values \( W(e) \) of a perfect predictor. Clearly, the temporal min-degree predictor may not be accurate when the rankings of \( \mathbf{W}^{\text{m-d}} \) and \( \mathbf{W} \) do not align. Note that the temporal min-degree predictor can be computed extremely efficiently, with a single pass over the stream, and avoiding exact temporal triangle counting. Finally, note that our temporal min-degree predictor leverages both structural and temporal properties in the data—in contrast with predictors for static triangle counting [4, 7], that do not consider time. In our extended version [40], we provide an empirical comparison for STEP coupled with different predictors, showing the superior performance of our temporal min-degree predictor compared with state-of-the-art static predictors.

## 4 Experimental Evaluation

Our extensive experiments investigated the following questions:

- Q1. How does STEP compare to SotA approaches in terms of accuracy of its estimates and computational resources (time and memory)?
- Q2. What is the impact of the predictor \(\mathcal{Q}(\cdot)\) on the estimates of STEP?
- Q3. How does STEP perform in an online setting. Namely, when a predictor \(\mathcal{Q}(\cdot)\) is learned on historical data, and then used on previously unseen data?

**Datasets and Environment.** We considered four massive publicly available temporal graphs (Table 1), which are extremely challenging for Problem 1 and used by previous works [9, 28, 30, 36]. More details on the used datasets and the setting of our experiments can be found in our extended version [40]. Our code is publicly available online.

Table 1. Datasets. We report: $n = |V|$ the number of nodes; $m = |E|$ the number of temporal edges; the *precision* of the timestamps; and the total *timespan*.

| Dataset | $n$ | $m$ | precision | timespan |
|---|---|---|---|---|
| Stackoverflow (SO) | 2.6 M | 63.5 M | sec | 7.60 years |
| Bitcoin (BI) | 48.1 M | 113.1 M | sec | 7.08 years |
| Reddit (RE) | 8.4 M | 636.3 M | sec | 10.06 years |
| EquinixChicago (EC) | 11.1 M | 3.3 B | $\mu$-sec | 62.00 mins |

**Baseline Methods.** We compared STEP with the following SotA algorithms: **Degeneracy** [30], an *exact* algorithm for computing the counts of all temporal triangles; **FAST-Tri** [9], an *exact* algorithm specifically tailored to temporal triangles; **MoTTo** [18], a recent SotA *exact* algorithm for counting 3-nodes 3-edges motifs, including triangles; and **EWS** [41], the SotA *approximate* method for solving Prob. 1.7. We also compared with the sampling approach of STEP *without* a predictor that we denote with **NAIVE-S**. Note that all exact approaches considered cannot process the input in streaming, requiring therefore large memory.

**Memory and Runtime.** We measured the peak RAM memory (in GB) of each algorithm over a representative run. The runtime is an average over ten runs, unless otherwise stated. Since **EWS** counts triangles independently, its runtime is an average of the aggregated time to process all triangles, across ten runs.

**Parameters.** We select a small, a medium, and a large value for the parameter $\delta$ according to the precision of each dataset. We set on SO, BI and RE $\delta \in \{3600, 86400, 259200\}$, while for EC we set $\delta \in \{1 \times 10^5, 2 \times 10^5, 3 \times 10^5\}$. We set the parameter $K$ to $\frac{m}{100}$. The sampling probability $p_{NS}$ of **NAIVE-S** is set to obtain, in *expectation*, the same number of edges retained by STEP (i.e., $|S_L| + |H|$). All the parameters used in our experiments are in the extended version [40].

**Ranking Predictors.** We considered two ranking predictors for STEP: _1)_ a _perfect predictor_ that exactly classifies the $K$ edges with the highest weights $W(e), e \in E$ as defined in Sect. 3.3, and _2)_ a _temporal min-degree_ predictor, as described in Sect. 3.4. We denote the resulting methods with STEP$_p$ and STEP$_{\text{TMD}}$ respectively. The perfect predictor allows us to evaluate the performance of STEP when the edge weights correspond to the actual number of temporal triangles an edge is involved in—this is not of practical interest but provides a lower bound on the error of the estimates of STEP. The temporal min-degree predictor (TMD) is instead simple, general, domain-agnostic, and can be computed from simple structural properties in the data. The TMD uses the temporal min-degree as edge weight to classify the top-K most heavy edges to retain, as described in Sect. 3.4. The resulting method, STEP_TMD is simple and of *practical* interest, given that the TMD can be computed efficiently.

$^7$ **EWS** requires two parameters $p_{EWS}$ and $q_{EWS}$ that we set as suggested by the authors [41] (see [40] for further details).

Table 2. Peak RAM memory, in GB, of a representative run for the largest $\delta$. OOM denotes out of memory.

| Dataset | NAIVE-S | STEP_P | STEP_TMD | EWS | Degeneracy | FAST-Tri | MoTTo |
|---|---|---|---|---|---|---|---|
| SO | 0.78 | 0.74 | 0.74 | 8.04 | 5.10 | 5.81 | 12.07 |
| BI | 1.70 | 1.81 | 1.74 | 27.05 | 15.40 | 17.43 | 34.08 |
| RE | 14.68 | 14.74 | 15.53 | 103.75 | 71.30 | 79.59 | 159.74 |
| EC | 63.46 | 62.70 | 63.47 | OOM | OOM | OOM | OOM |

### 4.1 Comparison with State-of-the-Art Methods

We first compared STEP with SotA baselines to answer question **Q1**. For such comparison, we fixed the parameters of all the approximation algorithms (STEP, NAIVE-S, and EWS) to ensure comparable runtime and MAE. Specifically, we ran STEP with the same sampling probability as EWS (\(p = 0.01\)) on all datasets except for SO, where \(p = 0.1\) was used since STEP is much faster than EWS. When discussing results for STEP, we focus on STEP_TMD. Table 2 reports the peak memory usage for each algorithm, and Table 3 presents the runtime of all algorithms except STEP_P and NAIVE-S (see [40] for additional results). Figure 2 shows the accuracy of each approximate method on SO, BI and RE datasets for the largest values of \(\delta\) (exact methods always report 0 MAE). While Fig. 3 reports the accuracy of the STEP_P, STEP_TMD and NAIVE-S approaches on the EC dataset (EWS is not reported since it violates the RAM budget, see Table 2). Results for other values of \(\delta\) are available in the extended version [40]. On the SO dataset, STEP_TMD requires substantially less memory than EWS, Degeneracy, FAST-Tri and MoTTo while achieving more accurate estimates than EWS for all values of \(\delta\) and for most temporal triangle counts. On the RE dataset, STEP_TMD similarly demonstrates a significant reduction in memory usage compared to EWS, Degeneracy, FAST-Tri and MoTTo, and often provides higher-quality estimates than EWS. On the BI dataset, STEP_TMD is much more memory efficient compared to EWS, Degeneracy, FAST-Tri and MoTTo. For larger values of \(\delta\), when the estimation problem becomes more challenging, STEP_TMD obtains more accurate estimates than EWS. For smaller values of \(\delta$, the estimates provided by STEP_TMD are comparable but slightly less accurate than those of EWS. In terms of runtime, STEP_TMD consistently outperforms Degeneracy, FAST-Tri and MoTTo, and, in most cases, also EWS, with the exception of $\delta = 259200$ on the BI dataset. The BI dataset contains almost 40 billion $\delta$-instances, most of which are counted
