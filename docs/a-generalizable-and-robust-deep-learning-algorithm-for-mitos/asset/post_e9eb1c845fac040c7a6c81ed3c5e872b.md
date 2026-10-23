
![](img/dd801f3ecf64db6a702e880d08ce4487_9_0.png)

(a) MIDOG21 (No. 1)

![](img/dd801f3ecf64db6a702e880d08ce4487_9_1.png)

(b) MIDOG21 (No. 2)

![](img/dd801f3ecf64db6a702e880d08ce4487_9_2.png)

(c) MIDOG21 (No. 3)

![](img/dd801f3ecf64db6a702e880d08ce4487_9_3.png)

(d) AMIDA13

![](img/dd801f3ecf64db6a702e880d08ce4487_9_4.png)

(e) MITOSIS14

![](img/dd801f3ecf64db6a702e880d08ce4487_9_5.png)

(f) TUPAC16 (Center 2)

![](img/dd801f3ecf64db6a702e880d08ce4487_9_6.png)

(g) TUPAC16 (Center 3)

![](img/dd801f3ecf64db6a702e880d08ce4487_9_7.png)

(h) MIDOG22

Fig. 3. Visualization of mitosis detection results from the proposed FMDet method. The predicted semantic segmentation results are converted into bounding boxes by drawing a rectangle of fixed size around the centroid of each segmentation mask. The green and blue bounding boxes are ground truth annotated by the corresponding data providers, which represent the true mitoses and hard negative samples (mitosis-like), respectively. The yellow bounding boxes are the predicted results by our method. The sub-figures correspond to sub-regions cropped from WSIs from different data sources for better visualization. Sub-figures (a)–(c) show examples from the MIDOG21, which are collected from No. 1: Hamamatsu XR nanozoomer 2.0, No. 2: Hamamatsu S360 (0.5 NA), and No. 3: Aperio ScanScope CS2 scanners, respectively. Sub-figures (d) and (e) show examples from the AMIDA 13 and MITOSIS14, respectively. Sub-figures (f) and (g) show examples from SPEC-Alkmaar (Center 2) and SPEC-Zaandam (Center 3) in the TUPAC16 dataset. Sub-figure (h) shows examples from MIDOG22, which are collected from a new center (FU Berlin).

accuracy. In the full TUPAC-auxiliary data, the two-stage mitosis detection method (Mahmood et al., 2020) is lower than ours by about 5% in terms of F1 score, which may be due to the fact that it does not consider the domain shift problem. Our method employs Fourier-based data augmentation to reduce domain discrepancies, which has shown robust performance in all experiments. Even though one study has reported higher performance on the TUPAC-auxiliary data (Sohail et al., 2021b), the same dataset is utilized during the model training.

In other words, the reported results are not independently validated. In contrast, our results are computed on completely independent test data, which is more objective and can better indicate the generalization ability of the proposed method in real practice. Although our method obtains the highest F1 and recall scores, the precision metric is not optimal. For example, the SegMitos (Li et al., 2019a) on AMIDA13, the two-stage mitosis detection method (Mahmood et al., 2020) on TUPAC-auxiliary, and the MaskMitosis (Sebai et al., 2020) on MITOSIS14 produce higher precision scores than our FMDet, which indicates that the results predicted by our method contain more false-positive images. The possible reasons can be summarized as follows. (1) Some non-mitotic cells (e.g., apoptotic or necrotic nuclei, dense nuclei, compressed nuclei, and “junk” particles) have a similar appearance to that of mitotic cells, which may be mistakenly detected as mitosis by our algorithm, as shown in Fig. 3(d)–(g). But it is able to improve the rate of missed mitosis detections, which is significantly important in clinical practice. (2) In some works (e.g., SegMitos and MaskMitosis methods (Li et al., 2019a; Sebai et al., 2020)), no domain discrepancy exists in their data, where the training and test images are from the same labs and scanners. Different from their settings, we adopt these datasets listed in Table 6 as unseen domains for independent algorithm validation, which can imitate the actual clinical scenario. (3) Some works employ complex computations to improve performance. For example, Mahmood et al. (2020) adopt a model ensemble to infer mitotic regions, which can be a valid strategy to reduce false predictions. SegMitos (Li et al., 2019a) requires complex post-processing to obtain accurate mitotic regions. In contrast, our end-to-end model does not require any post-processing step, which ensures a faster inference speed and more reliable predictions.

From Table 6, it is seen that the accuracy of our method on the MITOSIS14 data is the lowest. There are a couple of explanations. First, the MITOSIS14 dataset is known to be more challenging due to high variations in tissue appearance (Mahmood et al., 2020; Beevi et al., 2019; Sebai et al., 2020). Second, there are annotation inconsistencies across different datasets, since each dataset was labeled by different human observers and thus subject to inter-rater variations. We note that the reported results of other methods on MITOSIS14 were computed using only data from one scanner type, but our method was tested on all MITOSIS14 data. If tested using only data from the same scanner (1200 images in total), the F1 score will be 0.5218 instead of 0.4901, which is about 5% higher than the previously best-reported result.

### 4.8. Comparison with stain normalization methods

In this subsection, we conduct a set of experiments to compare our strategy for mitigating domain shift (i.e., FFT-based data augmentation) with existing stain normalization methods. A stain normalization method aims to remove stain variation so as to get consistent color distributions for both training and testing data, which is often adopted as a preprocessing step in histopathological image analysis. The most widely used stain normalization scheme is color deconvolution, where separating stains from the RGB images is a key step (Tosta et al., 2019). Three popular stain normalization methods are compared in Table 7. The SVD-based method of Macenko et al. (2009) uses singular value decomposition (SVD) to obtain the stain vectors. The structure-preserving color normalization (SPCN) method uses sparse non-negative matrix factorization to separate stains (Vahadane et al., 2016). The whole-slide image color standardizer (WSICS) method derives the stain components using the image color and spatial information (Bejnordi et al., 2015).

Table 7
Comparison with other stain normalization methods on the out-of-domain validation set of MIDOG21. The baseline method is our mitosis segmentation method with the combination of SK-Unet (SEResNeXt50 + SK) and instance masks. Nor. and Aug. denote normalization and Fourier-based data augmentation, respectively.

| Methods | F1 score | Recall | Precision |
|---|---|---|---|
| Baseline | 0.7343 | 0.8096 | 0.6719 |
| Baseline + SVD-based Nor. | 0.7375 | 0.7946 | 0.6881 |
| Baseline + SPCN | 0.7390 | 0.7756 | 0.7056 |
| Baseline + WSICS | 0.7428 | 0.7938 | 0.6980 |
| Baseline + Aug. (Ours) | 0.7773 | 0.8146 | 0.7440 |

From Table 7, it is seen that these stain normalization methods have little performance gains for the mitosis detection task, while our Fourier-based data augmentation method offers a much larger performance improvement. These results are consistent with that of a previous study (Tellez et al., 2019), where data augmentation was found to provide higher accuracy in a pathology classification task than using stain normalization. The reason is that it is difficult to accurately estimate the stain from a single image, and traditional stain normalization methods could create image artifacts. When used with deep learning methods, the reduced sample diversity due to stain normalization may increase the risk of model overfitting, whereas our data augmentation method increases data variation and promotes more robust network training.

## 5. Conclusion

In this work, we propose a mitosis detection method (FMDet) on breast histopathological images. To alleviate the problem of domain shift, we employ Fourier-based data augmentation to generate diverse domain-agnostic images. The importance of our data augmentation method has been verified in our ablation experiments. And then, we transform the detection task as a semantic segmentation one based on a fully convolutional network, where the coarse bounding box annotations are converted into fine pixel-level boundaries of mitotic nuclei. The instance-based semantic segmentation with precise supervision produces higher performance compared with the bounding-box-based segmentation. To achieve more robust feature extraction, we integrate a channel-wise multi-scale attention mechanism into the U-Net framework, which has also been verified to achieve superior performance in our ablation study. Our FMDet algorithm has been evaluated in the MIDOG 2021 challenge and secured first place. The comparison experiments with state-of-the-art mitosis detection methods also demonstrate the effectiveness of our solution. Further, we externally validate our generalization capability on four independent datasets for mitosis detection. The corresponding experimental results provide evidence for model generalization and reproducibility across multi-center cohorts. In our future work, we will attempt to improve the model generalizability by combining self-supervised learning on large-scale unlabeled data.

## Declaration of competing interest

The authors declare that they have no known competing financial interests or personal relationships that could have appeared to influence the work reported in this paper.

## Data availability

I have shared the link to my data/code at the manuscript.

## Acknowledgments

This research was in part funded by the National Natural Science Foundation of China (No. 61571314), Science & technology department of Sichuan Province, China (No. 2020YFG0081), and the Innovative Youth Projects of Ocean Remote Sensing Engineering Technology Research Center of State Oceanic Administration of China (No. 2015001).

## References

- Akram, S.U., Qaiser, T., Graham, S., Kannala, J., Heikkilä, J., Rajpoot, N., 2018. Leveraging unlabeled whole-slide-images for mitosis detection. In: OMIA COMPAY. Springer, pp. 69-77.
- Alirezazadeh, P., Hejrati, B., Monsef-Esfahani, A., Fathi, A., 2018. Representation learning-based unsupervised domain adaptation for classification of breast cancer histopathology images. Biocybern. Biomed. Eng. 38 (3), 671-683.
- Aubreville, M., Bertram, C.A., Donovan, T.A., Marzahl, C., Maier, A., Klopfleisch, R., 2020. A completely annotated whole slide image dataset of canine breast cancer to aid human breast cancer research. Sci. Data 7 (1), 1-10.
