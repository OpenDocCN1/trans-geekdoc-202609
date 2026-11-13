![](bbox=[0.07, 0.08, 0.92, 0.4])

**FIGURE 2.** The output and data of Example 1 with different methods. (a) The output and data of the original model. (b) The output and data of the proposed method. (c) The output and data of [42]. (d) The output and data of [32]. (e) The output and data of [43].

![](bbox=[0.07, 0.46, 0.44, 0.64])

**TABLE 3. The established antecedent parameters for Example 2.**

| Rule | \(\alpha_1^i\) | \(\beta_1^i\) | \(\alpha_2^i\) | \(\beta_2^i\) | \(\alpha_3^i\) | \(\beta_3^i\) |
|---|---|---|---|---|---|---|
| \(i=1\) | 4.1372 | 0.4092 | 3.9946 | 0.7690 | 2.4056 | 0.4474 |
| \(i=2\) | 5.0585 | 4.5511 | 1.2503 | 5.3355 | 1.6406 | 5.6395 |
| \(i=3\) | 3.4422 | 1.0316 | 4.0015 | 0.9167 | 3.6998 | 0.8752 |
| \(i=4\) | 5.1032 | 5.9777 | 1.2204 | 12.5761 | 1.4007 | 11.6194 |
| \(i=5\) | 2.9370 | 0.6385 | 4.0283 | 0.5985 | 4.8454 | 0.4265 |
| \(i=6\) | 5.1186 | 4.4907 | 1.1563 | 8.9973 | 1.2933 | 20.2431 |

**FIGURE 3.** Comparison of the established model and real model for Example 1.

**TABLE 4. The established consequent parameters for Example 2.**

| Rule | \(a_0^i\) | \(a_1^i\) | \(a_2^i\) | \(a_3^i\) |
|---|---|---|---|---|
| \(i=1\) | -5.6699 | \(-7.8293 \times 10^{-5}\) | -0.0034 | -0.4234 |
| \(i=2\) | 1.1535 | 0.0002 | -0.0014 | -0.0204 |
| \(i=3\) | 0.1225 | 0.0193 | 0.0002 | 0.0109 |
| \(i=4\) | 0.0086 | 0.0260 | -0.0003 | 0 |
| \(i=5\) | -0.0069 | 0.0262 | 4.5172 | 0 |
| \(i=6\) | 0.0013 | -0.0445 | -1.0352 | 0 |

**TABLE 2. Comparison among various identification methods for Example 1.**

| Model | Number of rules | MSE |
|---|---|---|
| Liu et al. [46] | 10 | 0.1030 |
| Sugeno and Yasukawa [44] | 6 | 0.079 |
| Zarandi et al. [27] | 6 | 0.0715 |
| Kim [42] | 3 | 0.0197 |
| Kung and Su [32] | 3 | 0.0196 |
| Lee and Ouyang [45] | 10 | 0.0148 |
| Li et al. (2009) [29] | 6 | 0.0085 |
| Li et al. (2012) [43] | 6 | 0.0043 |
| Proposed method | 4 | 0.0024 |

Table 3 and Table 4 list the parameters of the antecedent and consequent for the T-S fuzzy model, respectively. The established fuzzy model contains 6 rules with 18 antecedent variables. Each antecedent variable is described by

bell-shaped membership functions with two parameters, namely the center and the standard deviation.

The comparison results of the established model and the real model for the training data and testing data are shown in Fig. 4 and Fig. 5, respectively. From these figures, one can observe that the approximation error between the established fuzzy model and the real model is very small. The performance index APE is adopted to examine the approximation error between the established model and other fuzzy models. Table 5 lists the comparison results between the results of the proposed method and those obtained using other methods. It can be seen that the proposed identification method