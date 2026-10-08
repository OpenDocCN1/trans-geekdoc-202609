# A Multi-Stage Hybrid Model for Odia Compound Character Recognition

TABLE 3.2
Recognition Performance of Different Possible Hybrid Models

| Hybrid Model | Accuracy (%) |
| --- | --- |
| Two-stage hybrid classification | Stage I: DCST + PCA and SVM<br>Stage II: LFD and GRNN<br>Stage I: DCST + PCA and SVM<br>Stage II: LFD and SVM<br>Stage I: DOST + PCA and SVM<br>Stage II: LFD and SVM<br>Stage I: DOST + PCA and SVM<br>Stage II: GRNN | 75.38<br>78.73<br>80.45<br>83.64 |
| Three-stage hybrid classification | Stage I: SSIM matching<br>Stage II: Projection profile matching (KROCC)<br>Stage III: LFD and GRNN<br>Stage I: SSIM matching<br>Stage II: Projection profile matching (KROCC)<br>Stage III: LFD and SVM | 90.60<br>80.80 |

consideration. However, these models achieved a reduced accuracy compared to the single-stage models which are shown in Table 3.2. This is because stage I similar probability values for the characters with the same geometric structures. Here, we designed a three-stage hybrid model to overcome the limitations of the two-stage model. Here, we used template matching and ranking methods to reduce the number of predicted character classes. Then, we employed SSIM matching and profile ranking to further reduce the highly improbable characters predicting the final class using LED and GRNN/SVM. The results of the hybrid models are shown in Table 3.2. It is observed that the three-stage model with LED and GRNN provides the highest recognition performance (i.e., 90.6%) in comparison to the other hybrid models and state-of-the-art methods.
The proposed model is applied to form an OCR for Odia characters. Figures 3.9–3.14 shows the results for a sample input and at different stages of the proposed model.

![](bbox=[0.121, 0.706, 0.879, 0.903])

FIGURE 3.9 Result of conversion of (a) original image and (b) binary image.