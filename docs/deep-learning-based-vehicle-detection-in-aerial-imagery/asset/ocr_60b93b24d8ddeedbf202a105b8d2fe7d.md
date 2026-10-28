is achieved by employing FCN-32s as semantic labeling architecture, which slightly outperforms FCN-D16 and SegNet. The IMT Faster R-CNN exhibits an improved AP compared to the baseline Faster R-CNN except for using FCN-16s as semantic labeling architecture, which indicates that implicitly inducing scene knowledge by sharing features results in improved detection accuracy. Note that the baseline Faster R-CNN is trained on augmented data as well. Thus, the achieved AP is higher compared to the AP reported in Table 6.4. One reason for the absent gain in AP in case of FCN-16s may be the training procedure as no staged training as proposed in [Lon15] is performed. In [Som17a], notably worse semantic labeling results are achieved on the Potsdam dataset by training FCN-16s at once compared to FCN-32s. EMT Faster R-CNN shows better detection results for all semantic labeling architectures compared to its IMT Faster R-CNN counterparts and clearly improved detection results compared to the baseline Faster R-CNN. Hence, explicitly adding features from the semantic labeling branch and consequently more semantic context information boosts the detection accuracy. Overall, the best AP is achieved for FCN-D16, which outperforms the baseline Faster R-CNN by 1.1% in AP.

# Table 6.9: Impact of varying the weighting factor λ₁ of the semantic labeling loss exemplarily for EMT Faster R-CNN with FCN-D16.

| Weighting factor λ₁ | AP (in %) |
|---|---|
| 1 | 96.5 |
| 2 | 96.5 |
| 3 | 96.7 |
| 4 | **96.8** |

The impact of varying the weight ratio between the semantic labeling loss and the detection loss is given in Table 6.9 exemplarily for EMT Faster R-CNN using FCN-D16 for the semantic labeling branch. For this, the weighting factor λ₁ of the semantic labeling loss (see eq. (6.2)) is varied in the range between 1 and 4, while all other weighting factors are kept fixed at 1. Weighting all losses equally (λ₁ = 1) results in the lowest AP, while the best AP is achieved