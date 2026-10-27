# TABLE 7.4

# t-test for Evaluating Significance of Feature Extraction with VQ using LBG

| Existing Techniques | Mean | Standard Deviation (SD) | Standard Error of the Mean (SEM) | t-calc | p-Value | Significance |
|---|---|---|---|---|---|---|
| Liu, 2013 | 0.626 | 0.220 | 0.073 | 3.550 | 0.007 | Significant |
| Ramírez-Ortegón et al., 2010 | 0.601 | 0.240 | 0.080 | 3.770 | 0.005 | Significant |
| Yanli and Zhenxing, 2012 | 0.638 | 0.223 | 0.074 | 3.190 | 0.012 | Significant |
| Shaikh et al., 2013 | 0.595 | 0.214 | 0.071 | 3.870 | 0.004 | Significant |

[Observation: The p-values indicate significant difference in Precision results for classification with all the existing feature extraction techniques compared to the feature extraction with VQ using LBG.]

the proposed technique is better than the existing techniques. On the other hand, the SD and SEM have a lesser value for the proposed technique compared to the existing techniques. Therefore, the proposed technique can be considered to have better consistency compared to the existing techniques. Hence, classification by feature extraction with VQ using LBG has outclassed the state-of-the-art techniques in classification performance for content-based image classification.

The t-test is performed with four different comparisons; a post hoc analysis must be conducted to accept the significance of the derived results using the Bonferroni correction. The value of α is considered to be 0.05 for the t-test. The expression to calculate the Bonferroni correction value is given as follows:

Bonferroni_α = α / Number_of_tests

where α = 0.05 and Number_of_tests = 4. Therefore, Bonferroni_α = 0.013 Now, the p-values in Table 7.4 are compared to the newly calculated .. value of 0.013. The comparison shows that all the p-values in Table 7.4 are smaller than the Bonferroni_α value. Thus, the proposed technique has significantly different classification results even after post hoc analysis compared to all the existing techniques in Table 7.4.

# Chapter Summary

This chapter presented two feature extraction techniques, namely, VQ using LBG and GLCM for content-based image classification. The techniques were