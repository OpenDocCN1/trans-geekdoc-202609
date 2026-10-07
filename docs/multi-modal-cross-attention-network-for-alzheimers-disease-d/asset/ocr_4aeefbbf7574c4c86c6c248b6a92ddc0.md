# Zhang et al.

# Computers in Biology and Medicine 162 (2023) 107050

![](bbox=[0.135, 0.053, 0.856, 0.219])

**Fig. 6. Performance of methods using different combinations. (a) AD vs. CN. (b) MCI vs. CN. (c) AD vs. MCI vs. CN.

![](bbox=[0.135, 0.263, 0.856, 0.413])

**Fig. 7. The boxplots of the cross-validation results in AD-related diagnostic tasks. The line in the middle of each box represents the mean of the boxes the current evaluation index. * indicates the significance difference. (a) AD vs. CN. (b) MCI vs. CN. (c) AD vs. MCI vs. CN.

![](bbox=[0.135, 0.466, 0.856, 0.616])

**Fig. 8. Comparison of results based on single-modality data. (The error bar represents the standard deviation.) (a) AD vs. CN. (b) MCI vs. CN. (c) AD vs. MCI vs. CN.

modality. For the CSF biomarkers, the CSF encoder followed by two layers is used for classification, while the image layers are added for integrating data. The results of AD diagnosis using single-modality marker are shown in Fig. 8.

As shown in Fig. 8(a), AD diagnostic employing features from MRI and FD-PET is significantly higher in terms of ACC, AUC, and F1 scores, which highlights the importance of multi-modality biomarkers in AD diagnosis.

overall standard deviation (minimum of 1.80%) for folds all evaluation metrics. The ROC curves in the two-class classification are employed to evaluate the performance of single-modality data for AD diagnosis, as demonstrated in Fig. 9.

# 5.2. Distributions of diagnostic markers

We investigate the influence of fusing markers on the performance of AD diagnosis. The experiments are conducted by adding different markers by one in three AD-related diagnostic tasks. That is to compare the performance of fusion from different modalities, as reported in

It is highlighted in Fig. 10, in all experiments, the diagnostic performance of methods with multi-modality data such as MP and MRI, is superior to using single-modality data such as MRI., the diagnostic performance of MPC is greatly better than MP. For instance, distinguishing AD from CN, our Gray method with MPC

As shown in Fig. 8(a), AD classification, the performance from MRI and FD-PET is significantly higher in terms of ACC, AUC, and F1, which is increased by 2.77% (from 75.23% to 78.00%). We also find that FD-PET can yield relatively better performance than MRI, which is consistent with the finding in [68, 6]. It is due to the fact that hippocampal biomarkers can be detected earlier in the early stage of AD. Our Gray method obtains viable results with a mean ACC of 89.78%, an AUC of 93.92% and an F1 of 89.39, which are 5.14%, 4.30% and 3.35% higher than using MRI and CSF, and 6.71%, 7.08% and 6.13% higher than using CSF in AD classification. Also, FD-PET achieves between

10