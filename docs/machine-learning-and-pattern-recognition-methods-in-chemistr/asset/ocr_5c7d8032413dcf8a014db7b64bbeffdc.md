44 Machine learning and pattern recognition methods in chemistry

The most popular formulation of SIMCA defines the overall distance to the model as:

```
$d_i = \sqrt{\left(\frac{T_i}{T_{0.95}}ight)^2 + \left(\frac{Q}{Q_{0.95}}ight)^2} \quad (2.48)$
```

the subscript 0.95 indicates that both the scores and the orthogonal distances, prior to being combined, need to be normalized by division to the 95th percentiles of their respective distributions under the null hypothesis.

When the overall distance to the model is defined as in Eq. (2.48), as a consequence of the normalization involved, its threshold for acceptance is set to $\sqrt{2}$. Therefore, if the i-th sample presents a $d_i \le \sqrt{2}$, the object is accepted and predicted as belonging to the modeled category; otherwise, it is rejected and considered not belonging to the class of interest.

# 3. Validation

Chemometrics modeling is of empirical nature, i.e., models are built on the collected data, to provide approximations of the system under study and formulate predictions. In this context, it is necessary to point out that, given the available data, the possible models that can be calculated are almost always more than a single one, and the quality and performances of the current candidate models can be influenced by several factors, e.g., the number of samples and their representativeness, the characteristics of the method or the algorithm for calculating the solution. In this context, it is fundamental to assess whether reliable outcomes and predictions can be drawn for a particular model, and whether they can be generalizable or not, at the same time verifying whether the interpretation of the results could be sound and meaningful. This process is called validation, and it constitutes a fundamental step of any chemometric modeling (Westad & Marini, 2015).

Operationally, validation is often conducted by applying the model to a set of data (test set) which was different and independent from the one used for model building (what was defined, in the training or calibration set). This additional set of data is treated along all analyses as if it were a new set of unknown observations, so to be able to obtain the model predictions for those data, but it is also necessary that the true values of the quantities to be predicted are known as well, in order to evaluate the model