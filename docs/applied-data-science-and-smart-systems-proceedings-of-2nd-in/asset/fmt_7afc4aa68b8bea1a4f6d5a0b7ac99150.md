
The SLIVER dataset includes a variety of liver images with different shapes, sizes, and pathological conditions, making it suitable for robust algorithm training.

### IRCAD dataset

The IRCAD dataset is used as the testing dataset for evaluating the performance of the enhanced algorithm.

It consists of CT images of liver structures, allowing for validation on a different dataset assessing the algorithm’s generalization capability.

Volumetric overlap error (VOE): Measures the overlap error between segmented and ground truth volumes.

Relative volume difference (RVD): Quantifies the relative difference in volume between segmented and ground truth regions.

Average symmetric surface distance (ASD): Measures the average distance between surfaces of the segmented regions (`[Figure 56.1](#ch56.xhtml#fig56_1)`, `[Figure 56.2](#ch56.xhtml#fig56_2)`, `[Figure 56.3](#ch56.xhtml#fig56_3)` and `[Figure 56.4](#ch56.xhtml#fig56_4)`).

![Figure 56.1 The comparison of existing and the proposed methods. (a) Represents the original images. (b) Represents the ground truth images. (c) Represents the existing method and (d) Represents the proposed method.](images/fig56_1_B.jpg)

[Figure 56.1 The comparison of existing and the proposed methods. (a) Represents the original images. (b) Represents the ground truth images. (c) Represents the existing method and (d) Represents the proposed method.](#ch56.xhtml#R_fig56_1)

![Figure 56.2 Shows the original image belongs to the SLIVER dataset](images/fig56_2_B.jpg)

[Figure 56.2 Shows the original image belongs to the SLIVER dataset](#ch56.xhtml#R_fig56_2)

![Figure 56.3 Shows the intensity histogram for the whole CT image](images/fig56_3_C.jpg)

[Figure 56.3 Shows the intensity histogram for the whole CT image](#ch56.xhtml#R_fig56_3)

![Figure 56.4 The intensity histogram for the whole CT image](images/fig56_4_B.jpg)

[Figure 56.4 The intensity histogram for the whole CT image](#ch56.xhtml#R_fig56_4)

It amply illustrates how much superior the pro-posed work segmentation is to the current method.

## Performance metrics

Performance for the proposed algorithm is quantified using several metrics, including RVD, VOE, RMSD, ASD and MSD.

### SLIVER dataset results

The proposed algorithm’s performance metrics are compared with the existing CV model on the SLIVER dataset which is shown in [Table 56.1](#ch56.xhtml#tab56_1).

[Table 56.1 Results for SLIVER](#ch56.xhtml#R_tab56_1)

| Data || Method || VOE || RVD || ASD || RMSD || MSD |
| --- | --- | --- | --- | --- | --- | --- |
| SLIVER || Existing || 7.6 || -0.1 || 0.8 || 1.5 || 20.8 |
| --- | --- | --- | --- | --- | --- | --- |
|  || Proposed || 7.3000 || -0.0800 || 0.6400 || 1.3200 || 19.2000 |

VOE: The proposed algorithm achieves a VOE of 7.3%, indicating improved overlap between segmented and ground truth volumes compared to the existing model’s VOE of 7.6%.

RVD: The proposed algorithm’s RVD is -0.08%, indicating a closer match between segmented and ground truth volumes compared to the existing model’s RVD of -0.1%.

ASD: The proposed algorithm’s ASD value is 0.64 mm, showing better average surface distance compared to the existing model’s ASD of 0.8 mm.

RMSD: The proposed algorithm achieves an RMSD of 1.32 mm, indicating reduced root mean square distance compared to the existing model’s RMSD of 1.5 mm.

MSD: The proposed algorithm’s MSD is 19.2 mm while the existing model’s MSD is 20.8 mm, showing improvement in maximum symmetric surface distance.

### IRCAD dataset results

Similarly, the proposed algorithm’s performance metrics are compared with the existing CV model on the IRCAD dataset which is displayed in [Table 56.2](#ch56.xhtml#tab56_2).

[Table 56.2 Results for IRCAD](#ch56.xhtml#R_tab56_2)

| Data || Method || VOE || RVD || ASD || RMSD || MSD |
| --- | --- | --- | --- | --- | --- | --- |
| IRCAD || Existing || 6.5 || 4.1 || 1.9 || 2.1 || 18.9 |
| --- | --- | --- | --- | --- | --- | --- |
|  || Proposed || 6.1000 || 3.8000 || 1.3000 || 1.2000 || 17.4000 |

VOE: The proposed algorithm achieves a VOE of 6.1%, improved over the existing model’s VOE of 6.5%.

RVD: The RVD of the proposed algorithm is 3.8%, compared to the existing model’s RVD of 4.1%.

ASD: The proposed algorithm’s ASD value is 1.3 mm, showing enhancement over the existing model’s ASD of 1.9 mm.

RMSD: The proposed algorithm’s RMSD is 1.2 mm, whereas the existing model’s RMSD is 2.1 mm.

MSD: The proposed algorithm’s MSD is 17.4 mm, better than the existing model’s MSD of 18.9 mm.

## Discussion

The results obtained from the SLIVER and IRCAD datasets demonstrate the effectiveness of the proposed algorithm in the liver segmentation compared to the existing CV model. The proposed algorithm consistently outperforms the existing model in terms of all performance metrics, indicating its accuracy and robustness in segmenting liver regions from CT images.

The reduction in VOE and RVD values for both datasets signifies improved volume overlap and similarity between segmented regions and ground truth. Moreover, the reduced values of ASD, RMSD, and MSD indicate better surface alignment between the segmented and ground truth liver regions, contributing to enhanced segmentation accuracy.

The visual comparisons of segmented liver regions further support the algorithm’s efficacy, as evident from the images provided in the results section. The proposed algorithm successfully extracts liver structures with higher precision and conforms better to the ground truth contours.

The proposed algorithm’s integration of shape prior information and enhancements to the CV model has resulted in improved liver segmentation performance. The achieved results exhibit higher accuracy, tighter volume correspondence, and reduced surface distance compared to the existing model. This advancement holds promise for more reliable and efficient liver segmentation in medical image analysis applications.

## Conclusion

The proposed liver segmentation algorithm, combining shape prior information and enhancing the CV model, demonstrates superior performance compared to the existing approach. Through comprehensive evaluation on SLIVER and IRCAD datasets, the algorithm consistently achieves better results in terms of various metrics, including volume overlap, surface distance, and symmetry. This advancement offers a more accurate and reliable means of segmenting liver regions from CT images, holding significant potential for enhancing medical image analysis and aiding clinical decision-making.

## Future work

This research could be extended by considering larger and more diverse datasets for training and testing. Additionally, the algorithm’s robustness and adaptability to varying image qualities and noise levels could be further investigated and improved. Incorporating advanced machine learning techniques, such as deep learning, might enhance the algorithm’s performance. Moreover, exploring real-time implementation and integration into medical imaging software could make the proposed method accessible for practical clinical applications. Finally, the algorithm’s applicability to segmenting other organs and structures within medical images could broaden its scope and impact in the area of medical imaging analysis.

## References

*   [Zheng, S., Fang, B., Li, L., Gao, M., Zhang, H., Chen, H., and Wang, Y.](#ch56.xhtml#R_ref56_1) (2017). A novel variational method for liver segmentation based on statistical shape model prior and enforced local statistical feature. 2017 IEEE 14th Int. Symp. Biomed. Imag. (ISBI 2017), 261–264.

*   [Saito, K., Lu, H., Tan, J., Kim, H., Yamamoto, A., Kido, S., and Tanabe, M.](#ch56.xhtml#R_ref56_2) (2017). Automatic liver segmentation from multiphase CT images by using level set method. 2017 17th Int. Conf. Con. Autom. Sys. (ICCAS), 1590–1592.
