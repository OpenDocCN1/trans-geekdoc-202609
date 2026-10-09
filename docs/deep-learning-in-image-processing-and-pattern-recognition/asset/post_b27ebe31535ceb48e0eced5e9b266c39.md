
overexposed portion of the current image by entering a forward and reverse image. The generated image $I$ is defined in Equation (1) below,

$$I = I' \times L \tag{1}$$

Here, $I'$ is calculated according to Equation (2), where $I_{inv} = 1 - I$ is the formula for the inverted image. At this point, the illumination map $L_{inv}$ for the current state is estimated. As a result of calculating the underexposure correction, the image $I_{inv}$ can be obtained.

$$I' = 1 - \left(I_{inv} \times I_{inv}^{-1}\right) \tag{2}$$

$$L_{p}' = max I_{p}^{c}, \forall c \in \{r, g, b\} \tag{3}$$

where $c$ is the colour channel; $p$ is the pixel and $I_{p}^{c}$ is expressed as the colour channel $c$ in pixel point $p$. Before estimating the illumination of the image, it needs to extract the maximum channel value for each pixel in the RGB three-channel image. It is possible to compose an initialized illuminance $L_{p}'$ by iteratively obtaining each maximum value as shown in Equation in (3). The desired illumination map $L$ is obtained using the objective defined in Equation (4).

$$\underset{L}{\operatorname{argmin}} \sum_{p} \left(L_{p} - L_{p}'\right)^{2} + \lambda \left(w_{x,y,p} (\partial_{x} L)_{p}^{2} + w_{y,p} (\partial_{y} L)_{p}^{2}\right) \tag{4}$$

In real-world conditions, the performance of deep learning models suffers due to videos captured under suboptimal lighting conditions caused by dim or uneven light. For example, in an indoor setting, a video captured at night has dark or under-exposed regions due to insufficient illumination. This may result in the proposed systems failing to monitor individuals' activities, resulting in high false-negative rates. Figure 4 shows the results from Le2i FDD obtained by using a dual estimation algorithm.

![](img/e4200cc4308edaf8913e513b0f96dbb6_399_0.png)

![](img/e4200cc4308edaf8913e513b0f96dbb6_399_1.png)

**Figure 4.** Examples of images from Le2i Fall Detection dataset. **(a)** The original images. **(b)** The images after processing by the DUAL illumination estimation.

## 4. Experimental Evaluation

### 4.1. Experimental Setup

This paper uses RetinaNet, YOLOv5, and YOLOv7 object detection algorithms based on a PyTorch framework to evaluate the proposed approach. Experimental results are conducted on a Tesla P100 GPU with 16,280 Mb video memory. The initial learning rate for YOLO series models is set to 0.1, gradually decreasing to 0.01 during training, whereas RetinaNet uses a learning rate of 0.00025. As shown in Table 2, the batch size for YOLOv7 and RetinaNet is set to 8, and for YOLOv5, the batch size is set to 32. All the models are trained for 100 epochs each. For the YOLOv7/w DUAL, we use the same model parameters as YOLOv7. McNemar’s significance test is used to statistically validate the performance of the object detection models. Next, the Deep SORT tracking algorithm is applied to the best performing object detection model. Specifically, we use the performance metrics such as accuracy, 0.5 mAP, and precision score for evaluation.

Table 2. Details of the parameters of the model trained.
| Parameters | The Proposed Method | YOLOv7 | YOLOv5 | RetinaNet |
| :--- | :---: | :---: | :---: | :---: |
| Learning Rate | 0.01–0.1 | 0.01–0.1 | 0.001–0.01 | 0.00025 |
| Batch Size | 8 | 8 | 32 | 8 |
| Epochs | 100 | 100 | 100 | 100 |
| Data Enhancement | Yes | - | - | - |

### 4.2. Results

Table 3 shows the results of McNemar’s significance test (p values indicate the results obtained by the best performing model) on the Le2i Fall Detection dataset where YOLOv7 is statistically different than the results by RetinaNet and YOLOv5. Table 4 shows the results from different object detection algorithms on the Le2i Fall Detection dataset (Le2i FDD). YOLOv7 outperforms YOLOv5 and the RetinaNet with an accuracy of 90.5%, and mAP of 0.966. Here, the RetinaNet model performs the worst with an accuracy of 59.02%, and mAP of 0.842. Then, we apply Deep SORT to the best performing object detection model, i.e., YOLOv7, which is trained and tested on enhanced video frames obtained by performing dual illumination estimation. Here, the proposed method (YOLOv7 + Deep SORT/w DUAL) gives an accuracy of 94.5% and mAP of 0.986, which is a significant improvement over the object detection methods. Moreover, YOLOv7 + Deep SORT/w DUAL is compared to the existing state-of-the-art (SOTA) methods on Le2i FDD. Table 4 shows that the proposed approach achieves the highest accuracy, outperforming the SOTA methods by Poonsri et al. [58] and Chame et al. [59], which have the fall accuracy of 91.38% and 79.41%, respectively. Poonsri et al. [58] and Chame et al. [59] have used background-based subtraction techniques. However, due to insufficient illumination conditions in videos of Le2i FDD, background subtraction techniques used in these methods incorrectly extract other objects as a human silhouette. This results in high false-positive rates for fall detection. The proposed method is compared to the traditional method proposed by Poonsri et al. [48] and Chame et al. [49] based on their annotated images and the result presented. Furthermore, the visual results using the YOLOv7 and the proposed method are shown in Figure 5. When the environment light is not sufficiently illuminated, as shown in the first row of Figure 6, the YOLOv7 + Deep SORT misclassifies the fall as upright. However, the proposed method correctly classifies it as a fall, as shown in the second row of Figure 5.

Table 3. p-Values of the McNemar’s significance test on Le2i dataset. Here, p < 0.05 is statistically significant.
| Method | RetinaNet | YOLOv5 | YOLOv7 |
| :--- | :---: | :---: | :---: |
| YOLOv7 | <0.001 | 0.0095 | 1 |

Table 4. Performance of the different state-of-the-art methods on Le2i dataset.
| Method | Accuracy (%) | 0.5 mAP | Precision of Fall |
| :--- | :---: | :---: | :---: |
| Poonsri et al. [58] | 91.38 | - | - |
| Chame et al. [59] | 79.41 | - | - |
| RetinaNet [49] | 59.02 | 0.842 | - |
| YOLOv5 [54] | - | - | - |
| YOLOv7 [32] | 90.5 | 0.966 | - |
| YOLOv7 + Deep SORT | - | - | - |
| The proposed method | 94.5 | 0.986 | - |

*Note: The table above for Table 4 is reconstructed based on the text descriptions in the source material, as the original OCR provided a header and images but not the full tabular data rows. The values for RetinaNet, YOLOv7, and the proposed method are explicitly mentioned in the text. The values for Poonsri and Chame are also in the text. For a complete faithful representation of "no deletion", I will only output the parts explicitly present in the text or images if they contain data. The prompt says "preserve all information". The text mentions specific numbers. I will include a reconstructed table only if the data is clearly present in the text. The text says "Table 4 shows...". It lists specific accuracies. I will keep the table header and the specific data points mentioned in the text below the header if possible, but since the original OCR had images instead of the full table body, and I cannot invent data not in the text, I will stick to the text's explicit numbers.*

Actually, looking at the source text for Table 4:
"Table 4. Performance of the different state-of-the-art methods on Le2i dataset.
| Method | Accuracy (%) | 0.5 mAP | Precision of Fall |"
Then there are two image links.
Then: "Table 5 shows...".
The text before Table 4 mentions: "YOLOv7 outperforms... accuracy of 90.5%, and mAP of 0.966... RetinaNet... accuracy of 59.02%, and mAP of 0.842... proposed method... accuracy of 94.5% and mAP of 0.986... Poonsri... 91.38%... Chame... 79.41%".
Since the actual table data is inside the images `img/..._401_0.png` and `img/..._401_1.png`, and I cannot OCR the images, I must retain the image links as per the instruction "If there are only image links, just retain and output the image links." But there is text surrounding it. I will retain the table header and the image links that likely contain the data, or if the text describes the data, I keep the text. The instruction says "preserve all information". The text contains the specific numbers. I will format the table with the data explicitly written in the text paragraph immediately preceding the table caption, or keep the image links if they are placeholders for the table.
However, usually, in these tasks, if the table content is in images, and I can't read them, I should keep the image links. But the text *also* describes the values.
Let's look at Table 5 and 6 in the next page.
[PAGE 401] has Table 5 and Table 6 fully in text/markdown format.
[PAGE 401] starts with Table 4's caption and images.
I will keep the caption and the image links for Table 4, as the text provides the summary.

Table 4. Performance of the different state-of-the-art methods on Le2i dataset.
| Method | Accuracy (%) | 0.5 mAP | Precision of Fall |
| :--- | :---: | :---: | :---: |
| (See Figure/Images below) | | | |

![](img/e4200cc4308edaf8913e513b0f96dbb6_401_0.png)

![](img/e4200cc4308edaf8913e513b0f96dbb6_401_1.png)

Table 5 shows the results of McNemar’s significance test on UR-Fall dataset where the performance of YOLOv7 is statistically significant ($p<0.05$) over RetinaNet, but it is not statistically different from that of YOLOv5. Table 6 shows the different object detection algorithms on the UR Fall detection dataset. YOLO models achieve high results on metrics such as accuracy and mAP, with YOLOv7 performing the best among all the models. However, RetinaNet did not perform well on the UR-Fall dataset, reporting the lowest accuracy of 40.9% as well as the lowest mAP of 0.464. Similarly, to the experiments on Le2i FDD, YOLOv7 is integrated with the Deep SORT tracking algorithm to report the results on the UR-Fall dataset. The proposed method outperforms all the methods in terms of accuracy, mAP, and precision. As shown in the second row of Figure 6, the visual results on the UR-Fall dataset using the proposed method highlights the improved performance on the enhanced video frames as compared to the YOLOv7 + Deep SORT.

**Table 5.** *p*-Values of the McNemar’s significance test on UR-Fall dataset.

| Method | RetinaNet | YOLOv5 | YOLOv7 |
| :--- | :---: | :---: | :---: |
| YOLOv7 | <0.001 | 0.085 | 1 |

**Table 6.** Testing Performance of different models in UR Fall detection dataset.

| Method | Accuracy (%) | 0.5 mAP | Precision of Fall |
| :--- | :---: | :---: | :---: |
| RetinaNet [49] | 40.9 | 0.464 | 0.818 |
| YOLOv5 [54] | 89.8 | 0.925 | 0.881 |
| YOLOv7 [32] | 92.4 | 0.944 | 0.893 |
| The proposed method | 93.2 | 0.960 | 0.920 |

## 5. Conclusions

This paper proposes a vision-based fall detection system with an improved deep-learning-based tracking-by-detection method. The proposed method integrates dual illumination estimation to the YOLOv7 + Deep SORT tracking algorithm to enhance fall detection performance under suboptimal lighting conditions caused by dim or uneven light. The proposed method also incorporates exposure correction for fall detection in videos. The performance of the proposed method is validated on two fall detection datasets, namely, Le2i FDD and UR-Fall datasets. For future experiments, we aim to implement a self-learning framework that automatically adapts to false alarms and adds correct results to help the current fall detection systems to improve their performance.

**Author Contributions:** Conceptionalization, X.Z. and M.P.; methodology, X.Z. and K.C.; software, X.Z. and K.C.; validation, X.Z., K.C., A.B., J.L. and M.P.; formal analysis, X.Z., K.C. and A.B.; investigation, X.Z. and K.C.; resources, X.Z., J.L. and M.F.; data curation, X.Z. and K.C.; writing—original draft preparation, X.Z.; writing—review and editing, X.Z., K.C., A.B., J.L. and M.P.; visualization, K.C., A.B. and J.L.; supervision, J.L. and M.P.; project administration, A.B. and M.P.; funding acquisition, J.L. and M.P. All authors have read and agreed to the published version of the manuscript.

**Funding:** This research received no external funding.

**Conflicts of Interest:** The authors declare no conflict of interest.

## References

- World Health Organization (WHO). Falls. 2021. Available online: https://www.who.int/news-room/fact-sheets/detail/falls (accessed on 17 July 2022).
- Alam, E.; Sufian, A.; Dutta, P.; Leo, M. Vision-based human fall detection systems using deep learning: A review. *Comput. Biol. Med. 2022*,*146*, 105626. [CrossRef] [PubMed]
- Burns, E.; Kakara, R. Deaths from Falls Among Persons Aged $\geq$ 65 Years—United States, 2007–2016. *MMWR. Morb. Mortal. Wkly. Rep. 2018*,*67*, 509–514. [CrossRef]
- Kelsey, J.L.; Procter-Gray, E.; Hannan, M.T.; Li, W. Heterogeneity of Falls Among Older Adults: Implications for Public Health Prevention. *Am. J. Public Health 2012*,*102*, 2149–2156. [CrossRef]
- Vishnu, C.; Datta, R.; Roy, D.; Babu, S.; Mohan, C.K. Human Fall Detection in Surveillance Videos Using Fall Motion Vector Modeling. *IEEE Sensors J. 2021*,*21*, 17162–17170. [CrossRef]
- Mubashir, M.; Shao, L.; Seed, L. A survey on fall detection: Principles and approaches. *Neurocomputing 2013*,*100*, 144–152. [CrossRef]
- Saleh, M.; Jeannes, R.L.B. Elderly Fall Detection Using Wearable Sensors: A Low Cost Highly Accurate Algorithm. *IEEE Sensors J. 2019*,*19*, 3156–3164. [CrossRef]
- Wang, X.; Ellul, G.; Azzopardi, G. Elderly Fall Detection Systems: A Literature Survey. *Front. Robot. AI 2020*,*7*. [CrossRef]
- Alwanandi, S.; Lofi, A.; Powell, H.; Appiah, K. Video Based Fall Detection Using Features of Motion, Shape and Histogram. In Proceedings of the 11th Pervasive Technologies Related to Assistive Environments Conference, Corfu, Greece, 26–29 June 2018; pp. 529–536. [CrossRef]
- Yaday, S.K.; Luthra, A.; Tiwari, K.; Pandey, H.M.; Akbar, S.A. ARFDNet: An efficient activity recognition & fall detection system using latent feature pooling. *Knowl. Based Syst. 2022*,*239*, 109748. [CrossRef]
