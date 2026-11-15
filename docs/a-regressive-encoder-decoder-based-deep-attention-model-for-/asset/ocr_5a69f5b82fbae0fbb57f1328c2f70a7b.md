# Table 9
Comparative Analysis of Proposed Model with state-of-art segmentation models on benchmark performance measures.

| Models | IoU | Precision | Recall | F1-score |
|---|---|---|---|---|
| UNet | 0.88 | 0.87 | 0.86 | 0.86 |
| UNet ++ | 0.96 | 0.94 | 0.95 | 0.94 |
| D-UNet + Augmentation | 0.91 | 0.90 | 0.91 | 0.90 |
| WNet | 0.89 | 0.89 | 0.87 | 0.88 |
| VNet | 0.92 | 0.90 | 0.88 | 0.89 |
| Cascaded Network | 0.94 | 0.92 | 0.94 | 0.93 |
| Proposed Model | 0.96 | 0.94 | 0.94 | 0.94 |

study. One of the limitations of this experimentation is the unavailability of the open-source codes of the benchmark models. Due to the limited availability of open-source codes of newly introduced models, some of the recent models can be experimented with and compared in this work.

In the future, the model can be further refined by using other pre-trained models as the backbone of the encoder and decoder with the attention and regression layer to further increase the Dice metric and reduce the head circumference difference between the segmented region and ground truth.

# ## 6. Conclusion and future work

This paper presents the new encoder-decoder model incorporated with the power of the Attention gate with the regression layer to segment the fetus head from the 2D ultrasound images. The proposed model is designed by using the dense blocks in the encoding and decoding phase to minimize the problem related to gradient descent. It is a must to use dense blocks because in the proposed model the soft attention gate is used with skip connections to minimize the error loss. This soft attention basis is the backpropagation where the gradients are used.

The proposed model is used to do semantic segmentation of the fetus's head from the 2D ultrasound images. Later, the segmented result is post-processed with the help of the eclipse fitting, as the fetus is of shape oval. Thus, the proper fitting of the eclipse helps to map the segmented result on the ultrasound image. In the end, the fetus dimensional analysis is performed that can estimate the appropriate size of the fetus to check its growth. The result analysis by using the proposed methodology helps to identify the fetus with good precision having an average absolute head circumference difference of 0.354 mm.

The proposed model is trained on the dataset of 10,989 images (after augmentation) and tested on the dataset of 335 images. The average absolute head circumference difference of the testing dataset is 0.387 mm. The experimentation results are found satisfactory as the model can achieve the best performance even when experimented with different statistical performance metrics. Besides head circumference analysis, other metrics which are used in this work are the Dice coefficient, Mean average percentage error, and Hausdorff Distance. The experimentation results with these metrics using the proposed model give Dice-97.31%, MAPE-0.65%, and HD-1.09% on training data. Dice-96.30%, MAPE-0.71%, and HD-1.11% accurate results.

Besides the above metrics, the performance of the model is also evaluated on some other benchmark metrics that were used for segmentation like IoU, Precision, Recall, and F-measure. The experimentation with these metrics also proves the efficacy of the model with the achieved values of IoU-0.96, Precision-0.94, Recall-0.94, and F1-score-0.94. The model is also compared with some other benchmark deep models used for the segmentation of objects in different domains of

# ### Author statement

Somya Srivastava: Conceptualization, Methodology, Writing - original draft.
Ankit Vidyar thi: Supervision, Visualization, Investigation.
Shikha Jain: Reviewing, Results Validation, Language Correction.

# ### Data availability

No data was used for the research described in the article.

# ### Declaration of Competing Interest

The authors declare that they have no known competing financial interests or personal relationships that could have appeared to influence the work reported in this paper.

# ## References

+   [1] Luciano Marcondes Machado Nardozza, Ana Carolina Rabachini Caetano, Ana Cristina Perez Zamarian, Jaqueline Brandão Mazzola, Carolina Pacheco Silva, Vivian Macedo Gomes Marçal, Thalita Frutuoso Lobo, Alberto Borges Peixoto, Edward Araújo Júnior, Fetal growth restriction: current knowledge, Arch. Gynecol. Obstet. 295 (5) (2017) 1061–1077.
+   [2] Ulrike Schmidt, Dunja Temerincath, Katharina Bildstein, Benjamin Tschuy, Jade Mayer, Mark Sittlner, Jörn Siemer, Sven Kehl, Finding the most accurate method to measure head circumference for fetal weight estimation, Eur. J. Obstet. Gynecol. Reprod. Biol. 178 (2014) 153–156.
+   [3] Hyunsook Seo, Masoud Badii Khuzaai, Varun Vasudevan, Charles Huang, Hongyi Ren, Ruoxiao Xiao, Jiao Jia, Lei Xing, Machine learning techniques for biomedical image segmentation: an overview of technical aspects and introduction to state-of-art applications, Med. Phys. 47 (5) (2020) e2148–e167.
+   [4] Ankit Vidyar thi, Ankita Kansal, A survey report on digital images segmentation algorithms, Int. J. Comp. Eng. Technol. (IJCET) 3 (2) (2012) 85–91.
+   [5] Ankit Vidyar thi, Namita Mittal, Brain tumor segmentation approaches: Review, analysis and anticipated solutions in machine learning, 2015 9th National Systems Conference (NSC), IEEE 2015, pp. 1–6.
+   [6] Shirwin Minaee, Yuri Y. Boykov, Fatih Porikli, Antonio J. Plaza, Nasser Kehtarnavaz, Demetri Terzopoulos, Image segmentation using deep learning: A survey, IEEE Transactions on Pattern Analysis and Machine Intelligence, 2021.
+   [7] Hariharan Ravishankar, Sahana M. Prabhu, Vivek Vaidya, Nitin Singhal, Hybrid approach for automatic segmentation of fetal abdomen from ultrasound images using deep learning, 2016 IEEE 13th International Symposium on Biomedical Imaging (ISBI), IEEE 2016, pp. 779–782.
+   [8] Lu Wei, Jinglu Tan, Randall Floyd, Automated fetal head detection and measurement in ultrasound images by iterative randomized hough transform, Ultrasound Med. Biol. 31 (7) (2005) 929–936.
+   [9] Sandra M.G.V.B. Jardim, Mário A.T. Figueiredo, Segmentation of fetal ultrasound images, Ultrasound Med. Biol. 31 (2) (2005) 243–250.

# Table 10
Comparative Analysis of Proposed Model with State-of-Art using HC18 dataset of Ultrasound images.

| Ref | Method | DC | DHC | Average Diff | HC |
|---|---|---|---|---|---|
| Sobhaninia et al. [14] | Multi class Link Net | 96.84 ± 2.89 | 1.13 ± 2.69 | 2.12 ± 1.87 | 1.72±1.39 |
| Zeng et al. [24] | Optimized Deep Model | 97.61 ± 1.72 | - | 1.97 ± 1.89 | - |
| Heuvel et al. [25] | Haar Features + Hough Transform with Random Forest | 97.0±2.8 | 0.6 ± 4.3 | 2.8 ± 3.3 | 2.0 ± 1.6 |
| Rong et al. [26] | GVF-Net | 95.53 ± 3.98 | -0.24 ± 3.23 | 2.42 ± 1.93 | 2.18 ± 2.40 |
| Al-Bander et al. [27] | Mask RCNN | 97.73±1.32 | 1.49±2.85 | 2.33±2.21 | 1.39±0.82 |
| Proposed Model | Regression-Attention UNet | 97.31±1.47 | 0.304±1.26 | 1.87±1.21 | 1.09±0.77 |