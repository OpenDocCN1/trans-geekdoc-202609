![](bbox=[0.1, 0.12, 0.68, 0.26])

Figure 9.5. Modeling pipeline for detecting and mitigating distribution shift. Accessible caption. A block diagram with a training dataset as input to a pre-processing block labeled adaptation with a pre-processed dataset as output. The pre-processed dataset is input to a model training block labeled robustness with a model as output. A data distribution-based shift detection block is applied to the training dataset. A classifier performance-based shift detection block is applied to the model.

If you’ve started to collect unlabeled feature data from India, you can do unsupervised data distribution-based shift detection by comparing the India feature distribution to the Africa feature distributions. But you kind of already know that they’ll be different, and this unsupervised approach will not permit you to determine which type of distribution shift you have. Thus, in a Phulo-like scenario, you just have to assume the existence and type of distribution shift based on your knowledge of the problem. (Remember our phrase from Chapter 8: “those who can’t do, assume.”)

# 9.2.3 Mitigating Distribution Shift

There are two different scenarios when trying to overcome distribution shift to create a safe and trustworthy machine learning model: (1) you have unlabeled feature data X^(deploy) from the deployment distribution, which will let you adapt your model to the deployment environment, and (2) you have absolutely no data from the deployment distribution, so you must make the model robust to any deployment distribution you might end up encountering.

> > “Machine learning systems need to robustly model the range of situations that occur in the real-world.”

—Drago Anguelov, computer scientist at Waymo

The two approaches take place in different parts of the modeling pipeline shown in Figure 9.5. Adaptation is done on the training data as a pre-processing step, whereas robustness is introduced as part of the model training process. The two kinds of mitigation are summarized in Table 9.2.

Table 9.2. The two types of distribution shift mitigation.

| Type | Where in the Pipeline | Known Deployment Environment | Approach for Prior Probability and Covariate Shifts | Approach for Concept Drift |
|---|---|---|---|---|
| adaptation | pre-processing | yes | sample weights | obtain labels |
| robustness | model training | no | min-max formulation | invariant risk minimization |