computed the median vector $\hat{t}_s$ across each feature. Then, all feature vectors **u** for the same user $s_i$ were transformed according to Equation (1)

```
$$\hat{u}[k] = \begin{cases} u[k] > \hat{t}_s[k], \ u[k] \le \hat{t}_s[k], \end{cases}$
```

Figure 3 contains the t-SNE representation for the data when this transformation is applied to the entire set. data samples from a same group appear more sparse, and these plots suggest a more effective reduction of the subset-related component of the signals. A further analysis of the data topology with regard to the labels revealed a certain level of grouping, suitable for classification purposes. As an example, Figure 4 shows the positive and negative samples in the MAHNO dataset in the t-SNE space, according to self-reported arousal levels. An inspection of this plot in relation to Figure 3b suggests that the samples for certain groups of subjects may have been split according to their label.

![](bbox=[0.131, 0.346, 0.868, 0.773])

**Figure 3.** Dimensionality reduction by t-SNE, after transforming the data binarizing values according to whether they are lower or greater than the median: (a) DEAP, (b) MAHNO-HCl, and (c) DREAMER.

The proposed transformation allowed us to train the classifier using data from all available subjects, avoiding the small sample size and the need for the personalized training that is typically required when using intra-subject approaches. The only data required by the proposed transformation are the median for each feature, and these can easily be computed and progressively refined from unlabeled data as soon as the EEG capturing device is connected.