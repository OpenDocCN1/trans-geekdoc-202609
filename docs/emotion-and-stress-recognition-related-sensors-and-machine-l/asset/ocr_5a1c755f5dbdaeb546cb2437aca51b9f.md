where $tp_i, fp_i$ and $fn$, respectively, the true positives, false positives and false negatives of the $i$th class. The results of the evaluation are depicted in Figure 9, for both the BVDB (Figure 9a) and the SEDB (Figure 9b).

![](bbox=[0.168, 0.173, 0.831, 0.313])

(a) Motion Emotion Images. (b) Optical Flows. (c) Mean Attention Weight Values.

Figure 8. SenseEmotionDatabase: Attention network weight values for the classification task $T_{ij}, T_j$. Within each boxplot in (a,b), the mean and median weight values are depicted respectively with a dot and a horizontal line. In (c), the average values are normalised between the maximum average value and the minimum average value to allow a better visualisation of the values distributions.

![](bbox=[0.189, 0.423, 0.809, 0.613])

(a) BioHeat Pain Database (Part A). (b) SenseEmotion Database.

Figure 9. Weighted score aggregation performance. Within each box plot, the mean and median values of the performance evaluation metrics are depicted with a dot and a horizontal line, respectively.

These results depict a high variance among all performance metrics, in particular the Macro Recall, which points at the fact that the classification tasks remain difficult. On some participants yields a F1 Score of null or nearly null, pointing out the fact that the architecture is unable to discriminate between low and high levels of pain elicitation for these specific participants. This is, similar and in agreement with previous works on these specific datasets. The authors of the BVDB in [73] were able to identify a set of participants who did not react to the levels of pain elicitation, therefore causing the huge variance in the classification experiments.

The performance of the weighted score aggregation approach is compared to other pain-related-facial expressions classification approaches in the literature. For the sake of fairness, we compare the results of the proposed approach with results in related works which are based on the exact same dataset and computed based on the exact same evaluation protocol (LOSO). The results are depicted in Table 3 for the BVDB and in Table 4 for the SEDB.