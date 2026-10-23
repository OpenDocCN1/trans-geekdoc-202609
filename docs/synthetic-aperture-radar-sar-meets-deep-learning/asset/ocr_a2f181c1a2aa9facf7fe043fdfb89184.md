# Table 2. Correspondence between NoS and NoI in the SSDD dataset.

| NoS | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 |
| NoI | 725 | 183 | 89 | 47 | 45 | 16 | 15 | 8 | 4 | 11 | 5 | 3 | 3 | 0 |

NoS = number of ships; NoI = number of images.

In addition, to verify the detection performance of our proposed method in different scenarios, we introduced another large-scale SAR target detection dataset, namely, the HRSID dataset. The images in this dataset are high-resolution SAR images, which are mainly used for ship detection, semantic segmentation and instance segmentation tasks. The dataset contains a total of 5604 high-resolution SAR images and 16,951 ship instances. The HRSID dataset borrows from the construction process of the Microsoft Common Objects in Context (COCO) dataset, including SAR images with different resolutions, polarizations, sea states, sea areas and coastal ports. For HRSID, the resolutions of the SAR images are: 0.5 m, 1 m and 3 m, respectively.

To make a fair comparison with previous work, we attempted to use the same settings that previous workers used. We randomly divided the original SSDD dataset according to the ratio of 8:2 commonly used in existing studies and 80% of the datasets were used for the training of all methods. The remaining 20% was used as a test set to evaluate the detection performance of all methods. The data in the training set and test set were not repeated at all among the methods to ensure the rigor and fairness of the experiment. Other parameters included a batch size of 8 and an image size for the input model of 640, RandomHorizontalFlip was adopted, ColorJitter and multiscale were used for data augmentation, and Mosaic and MixUp enhancement strategies were employed. Using the lr×batchsize/64 learning rate, the cosine lr schedule and initial lr = 0.01 were employed. The weight decayed to 0.0005 and the SGD momentum was 0.9. A total of 600 epochs were trained. In the HRSID [35] dataset, we used a ratio of 6.5:3.5 to split the dataset, with 65% data for training and 35% for testing, the same as the original author split. The image size of the input model was 800. All experiments in this paper were carried out on an Ubuntu 18.04 operating system equipped with a GeForce RTX2060.

# 4.2. Evaluation Indicators

We used average precision (mAP) to analyze and verify the detection performance of our proposed method. Average accuracy can be derived from accuracy and recall.

Accuracy is the percentage of targets that are correctly identified in the test set. The percentage is defined by true positives (TPs) and false positives (FPs):

$P = \frac{TP}{TP + FP}$ (9)

TP means that the prediction of the classifier is positive and the prediction is correct; FP indicates that the prediction of the classifier is positive and the prediction is incorrect.

The recall rate is the probability that all positive samples in the test set are correctly identified, which is derived from true positives (TPs) and false negatives (FNs):

$R = \frac{TP}{TP + FN}$ (10)

FN indicates that the prediction of the classifier is negative and the prediction is incorrect.

Based on the accuracy and recall rate, an average accuracy value is also obtained. The graphical meaning can be clearly seen in the coordinate axis, that is, the area under the accuracy and recall rate curve, which is defined as follows:

$\text{mAP} = \int_{0}^{1} P(R) dR$ (11)