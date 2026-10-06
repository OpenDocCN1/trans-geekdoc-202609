# 6.4.3 Empirical Analysis

To provide an intutive justification for the proposed method, we conduct empirical analyses using the MSR-WTT dataset on various OOM scenarios and modalities.

![](bbox=[0.125, 0.281, 0.854, 0.44])

FIGURE 6.5. Connection effect on maximum mean discrepancy and accuracy across modalities.

**Connection mitigates modality gap.** To understand the performance of our VIB-based connection learning, here we show its effect on generalization out-of-modal. Specifically, during connection training, we compute the maximum mean discrepancy (MMD) between the mapping of each IM data and the OOM data. Meanwhile, we select 6 points during the training and extract the IM mappings which are used to a classification head as the optimal classifier. Based on our theoretical result, we apply the classifiers to OOM data and compute their accuracies, as shown in Figure 6.5. We can see that as training goes, the MMD between each IM and OOM data is decreasing and the corresponding accuracy is increasing, which shows that (1) our connection can indeed close the modality gap between their features and (2) the mappings of IM data getting close to OOM data, the optimal classifier shows better classification results on OOM data, which benefits the knowledge transfer from known modalities to unknown ones.

**Modality disagreement identifies uncertainty.** To understand the effect of modality disagreement, we analyze the semi-supervised scenario by training the OOM learner to use only labeled data for 10 epochs. Then, we leverage the modality disagreement criteria to separate OOM data into those with disagreement and agreement and show their prediction accuracies