# # 14 Homology boundary learning

# ## 14.1 Boundary learning algorithm

Boundary division can be divided into data partition and image division. At present, the main boundary learning algorithms are the TVQ algorithm, [1], Canny algorithm, [2], and the RLMC algorithm, [3].

# ### 14.1.1 Tangent vector quantisation (TVQ) algorithm

For this algorithm, Fabio Aiolli and Alessandro Sperduti proposed a good scheme to improve the boundary problem, which is based on the boundary theory. The algorithm is based on the sample weighting strategy. The basic idea is to increase the new copy of the training set, and the sample is not classified under the sufficient boundary.

Fabio Aiolli and Alessandro Sperduti proposed this algorithm as an example of learning, i.e., a pre-scheduled instance. It includes the distance cut based on the 1-NN classifier. The 1-NN classifier implements quantisation of a cut distance prototype. The generalisation ability of the cut distance model created in this way is obviously improved. This generalisation ability comes from the standard cut model. Furthermore, the obtained model has advantages over other algorithms, such as the SVM algorithm, in OCR tasks.

```
**Algorithm 14.1:**
**Input:** $T$ : Iteration number; $Q$ : Number of patterns per class; $\theta$: Marginal critical value
**Output:** $W$

(1) Initialisation: $W(1) \leftarrow N, \gamma_{i} \leftarrow 1/N$; For any $\gamma$, $q$, In random mode,
$$\boldsymbol{M}_{\gamma}^{(q)} \leftarrow \left(\mathbf{c}_{\gamma}^{(q)}, T_{\gamma}^{(q)}\right)\text{ . }$$

for $t = 1, \dots T$

$\forall \gamma$, $\forall q$, $\Delta \boldsymbol{M}_{\gamma}^{(q)} = 0$ , $\Delta \boldsymbol{M}_{\gamma_{i}}^{(q_{p})} \leftarrow \Delta \boldsymbol{M}_{\gamma_{i}}^{(q_{p})} + \gamma_{i}(t) \frac{\boldsymbol{\delta \mu}_{i}}{\boldsymbol{\delta M}_{\gamma_{i}}^{(q_{p})}}$ , $\Delta \boldsymbol{M}_{\gamma_{i}}^{(q_{n})} \leftarrow \gamma_{i}(t) \frac{\boldsymbol{\delta \mu}_{i}}{\boldsymbol{\delta M}_{\gamma_{i}}^{(q_{n})}}$ .

(2) Regularisation $r_{i}^{*} \boldsymbol{\mathcal{S}}$.
```

Compared with the SVM method, this method works directly on the nonlinear model instead of taking the kernel. When both methods are based on the concept of statistical learning theory, they converge uniformly from empirical risk to ideal risk.

This approach is very similar to the boosting algorithm. However, the boosting algorithm places greater emphasis on the independent hypothesis. Hence, multiplication strategies are better suited for switches.