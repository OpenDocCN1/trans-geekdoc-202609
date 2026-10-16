
**Figure 4.13.** ROC (AUC) comparison between the ML and DL methods for tumor classification.

### 4.6 Model validation and verification

#### 4.6.1 Hypothesis validation

A DL network learns the features during training via suitable filters. The low level features are accrued in the network through earlier layers and the high-level features via later layers. The convolution layers feed the learned features forward to further layers after the convolution operation using suitable filters in the form of multiple 2D arrays (channels). Fully connected layers accumulate all the high-level combinations of the features learned by earlier layers. Since the working mechanism of DL is unclear, it is assumed to be a black box. However, the learned features can be visualized using the MATLAB function `deepDreamImage`. In our experiment the features learned via the last fully connected layer (layer FC-3 in figure [4.6](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4fig6)) during the training for all the above tumor classifications are depicted in figure [4.14](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4fig14). These images differentiate visually between high- and low-grade tumors and their combinations. It is also seen from the visual inspection of these images that each tumor type and its grade is different from each other. However, this can be justified by the feature analysis of these images. Thus, in order to understand what the network learns and validate the CNN model for tumor classification between high and low grades, we proposed a unique statistical test for scientific validation using the tumor separation index (TSI). The TSI defines the degree of separation (in percentage) between two classes. In order to calculate the TSI, the mean and standard deviation of the above-mentioned features were calculated for each grade separately. The TSI between two classes is the mathematical expression of equation ([4.1](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4eqn1)), where *a* and *b* are the mean of all the features learned by the CNN during the training via the *K*‑fold cross-validation protocol (here, *K* = 5, 10).

$${TSI} = \\frac{a - b}{a} \\times 100.$$  

(4.1)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch4eqn12.gif" position="float"/

The TSIs of the K5 and K10 CV protocol of AST (g2 versus g3), OLI (g2 versus g3), and LGG versus HGG classifications are shown in table [4.4](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4t4). The features learned by the CNN in the form of images (one round of K10) are shown in figure [4.14](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4fig14). In the experiment we obtained a higher classification accuracy in the K10 CV protocol than in the K5 protocol and, interestingly, we note that the highest TSI difference is also found in the K10 CV protocol. The mean K10 TSIs of AST (g2 versus g3), OLI (g2 versus g3), and LGG versus HGG are 14.23%, 27.32%, and 21.42% respectively.

![Figure 4.14. Features learned by the last fully connected layer of the CNN from training samples of different tumor classification.](images/bk978-0-7503-2244-7ch4f14_online.jpg)

**Figure 4.14.** Features learned by the last fully connected layer of the CNN from training samples of different tumor classification.

**Table 4.4.** Tumor separation index: a statistical analysis test of deep learning features.

|  || AST (g2 versus g3) || OLI (g2 versus g3) || LGG versus HGG |
| --- | --- | --- |
| TSI, K5 CV || 13.56% || 26% || 17.54% |
| --- | --- | --- |
| TSI, K10 CV || 14.23% || 27.32% || 21.42% |

#### 4.6.2 Software verification

In order to test the legitimacy of the selected classifier (AlexNet), we have chosen well-known known biometric data (Face95) \[[85](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4bib85)\] which already produced high classification accuracy. The dataset has 72 subjects, including 58 males and 14 females. It further consists of 20 images per subject. Male versus female image classification was performed using the same model (AlexNet) and under the same circumstances as tumor classification. A total of 1440 image samples, further consisting of 1160 for males and 280 for the females class, we used. Although there is a huge difference in the size of male and female class samples, our model attained overwhelming average performance: ACC (99.86% ± 0.31%), SE (100% ± 0.00%), SP (99.91% ± 0.00%), PPV (99.43% ± 2.00%), NPV (100.00% ± 0.00%), and AUC (100.00% ± 0.00%) for *p* ⩽ 0.0001.

### 4.7 Discussion

Due to the deep locations of tumors in the brain, biopsies can sometimes be life‑threatening. However, they are an important gold standard and are always needed for validating the tumor grading processes. MRI is most popularly adapted for brain imaging due to its ability to capture the soft tissue characteristics in high‑resolution displays. However, due to the large number of slices, manual delineation and classification (the grading process) is tedious and error‑prone. Further, the manual process introduces inter‑ and intra‑operator variabilities. The previous methods of segmentation and grading were based on classical tools of machine learning, which were not robust enough or required heavy number crunching with ad hoc local parameterization. Here, we adapted an automated feature selection combined with grading in a deep learning paradigm. This study used a special form of CNN, AlexNet, for tumor grading, which offered a more robust and accurate solution. To the best of our knowledge, our study is the first to design a grading solution where the tumor types AST and OLI were categorized into their subgrades g2 and g3. Further, our system categorized the tumors into low‑grade and high‑grade glioma classes. To better understand the grading solution, our study attempted to create an innovative solution for the understanding of the tumor grade separations during the training of the deep learning paradigm. We call it the tumor separation index (TSI). This helps us to validate our scientific hypothesis that showed that DL solutions are better than ML solutions.

*A special note on CNN/AlexNet*

Designing a suitable CNN from scratch is a challenging task. This process takes a lot of iterations of trial and error, and has high computational cost for suitable layer selection \[[58](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4bib58)\]. Therefore, utilizing some of the existing recognized models (such as LetNet, VGGNet, AlexNet, GoogLeNet, etc) for the grading mechanism is a wise idea. Similarly, limited medical data is another serious issue and data are often highly insufficient for classification tasks via DL networks. Thus, we resolved these challenges via a pre‑trained CNN network with the transfer learning technique. Transfer learning has been proven to be constructive in transferring feature knowledge learned from a large number of natural databases to medical tasks \[[78](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4bib78)\]. Moreover, it has been found in the literature \[[29](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4bib29)\] that a pre‑trained network performs better compared to a network which is designed from scratch and optimized. Therefore we decided to go with a pre‑trained CNN network with transfer learning to enhance the accuracy of tumor classification. As stated above, LetNet, VGGNet, AlexNet, GoogLeNet, etc, have shown remarkable performance in image classification and are able to classify more than 1000 objects. It has been proven that a deeper network such as GoogLeNet performs well compared to shallower networks \[[29](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4bib29)\]. However, it is also expensive in terms of computational cost. In the presence of limited computational resources (a CPU), we have chosen AlexNet (an eight‑layer CNN) for brain tumor classification, which is a moderately deep network that produced an almost comparable performance compared to GoogLeNet.

*Challenges of deep learning and their solutions*
