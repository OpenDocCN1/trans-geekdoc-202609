
| 32 × 32 | SoftMax 2 类-(0/1) | 2.4 × 10⁶ | 80.2 × 10³ | 30 × 10³ | 0.0077 | 99.8115% | 99.7981% |

整体鸡蛋分类与计数的准确率超过 97%，Figure 2.7 展示了所提方法的结果，绿点代表已孵化鸡蛋，红点代表未孵化鸡蛋。由于输入图像过大无法完整显示，部分区域已放大并在 Figure 2.7 中单独展示，以便观察细小的鸡蛋特征。

![Figure 2.7 所提方法生成的鸡蛋分类结果。](img/fig2-7.jpg)

**Figure 2.7** 所提方法生成的鸡蛋分类结果。

## 2.4 数据集生成

与传统的数字图像直接提取鸡蛋计数、几乎不需要训练数据的方法相比，所提 CNN 方法需要大量数据集来自动学习特征并提供所需结果。CNN 方法在隐藏层数增加时，需要丰富的训练数据以及测试和验证数据集。

市面上有许多免费可下载的数据集，可用于训练自己的 CNN 模型以识别手写数字、识别物体等。但针对蚕卵计数或分类的专用公开数据集并不存在。因此，在本工作中，训练数据集通过从蚕卵纸中裁剪类图像并添加类标签、蛋中心位置等必要特征来生成。为蛋位置和分类（HC 与 UHC）分别生成了超过 40 万张图像的数据集，以及 10 万张用于单类（HC 和 UHC）的图像。同时实施了数据增强以扩大数据规模。

## 2.5 结果

The trained CNN models were tested with new silkworm egg sheets that were scanned using a Canon`^` paper scanner at 600 dpi, to classify and count the number of eggs. These digital datasets were completely isolated from the training step; thereby, the trained CNN models had to predict the results than providing learned results. Table 2.4 represents the performance of the overall CNN model trained using our datasets. The performance of a few datasets is shown due to space restriction. It can be observed that CNN models trained with two hidden layers perform superior to the conventional techniques by providing accuracy of over 97%. The accuracy shown in Table 2.4 is the accuracy of the number of eggs counted and accuracy in classifying the eggs. The model consistently outperforms the conventional computer vision/image processing technique of silkworm counting and classification with accuracy over 97% for newer data of the same breed. The inference time shown in Table 2.4 was performed on an Nvidia GPU (GTX 1060).

The model performance drops to newer egg data that are completely different in color and texture, which were not available in the training dataset. This happens due to the nature of different breed eggs that are spatially different from the trained model. Collecting and training a deep learning model to a different breed of silkworm eggs will resolve these issues, which is under action.

**Table 2.4** Performance of the CNN model results on test datasets.

| **Test sample** | **True count** | **Count prediction** | **Time (sec)** | **Class scores** | **Accuracy (%)** |
| --- | --- | --- | --- | --- | --- |
| | **HC** | **UHC** | | | |

| MSR1_001.jpg | 588 | 586 | 11.83 | 437 | 149 | 99.65 |
| MSR1_002.jpg | 534 | 526 | 8.99 | 473 | 53 | 98.68 |
| MSR1_003.jpg | 554 | 556 | 10.42 | 491 | 65 | 99.28 |
| MSR1_004.jpg | 539 | 528 | 9.81 | 501 | 27 | 97.95 |
| MSR1_005.jpg | 597 | 588 | 11.14 | 562 | 26 | 98.32 |

## 2.6 Conclusion

In this paper, CNN-based silkworm egg counting and classification model that overcomes many issues found with conventional image processing techniques is explained. The main contribution of this paper is in fourfolds. First, a method to generalize the method of capturing silkworm egg sheet data in a digital format using normal paper scanners rather than designing extra hardware, which eliminates the need for additional light sources to provide uniform illumination while recording data and maintain high repeatability.

Second, the scanned digital data can be transformed into standard size by using key markers stamped onto the egg sheets before scanning. This allows the user to resize the dimension of digital data and later use it in an image processing algorithm or CNN without introducing dimensionality error.

A dataset has been put together containing over 400K images representing different features of silkworm eggs. The CNN and other models that need a lot of training, testing and validation data can easily use this dataset to skip the data generation phase which is the third contribution.

Fourth, a CNN model has been trained using the dataset that is designed to predict the egg class and count the number of eggs per egg sheet. With over 97% accuracy the model outperforms many conventional approaches with only 4 hidden layers and a fully connected layer.

The model performs accurately in quantifying (counting) different breed silkworm eggs, but new datasets become necessary to predict the class labels for new silkworm breed for which the model is not trained. This is because HC class eggs have high pixel intensity throughout the egg surface while UHC has dark pixels at the center surrounded with high-value pixels for the egg breed used on our experiment. This color feature may not be the same as other breed silkworm eggs, and hence, additional data becomes important that can be fed into already trained CNN using transfer learning. Also, the egg location model performs well with new breed data, the training dataset to determining the class of eggs can be easily generated with minimal human effort.

## Acknowledgment

The authors would like to thank Smt. R. Latha S-B and Mr. P. B. Vijayakumar S-C of KSSRDI, KA, IN for providing silkworm egg sheets for this study.

## References

1. Xue, Y. and Ray, N., Cell Detection in Microscopy Images with Deep Convolutional Neural Network and Compressed Sensing, `CoRR`, abs/1708.03307, `arXiv preprint arXiv:1708.03307`, 2017.

2. Zieliński, B., Plichta, A., Misztal, K., Spurek, P., Brzychczy-Włoch, M., Ochońska, D., Deep learning approach to bacterial colony classification. `PLoS One`, 12, 9, e0184554, 2017.

3. Abe, M. and Nakayama, H., Deep learning for forecasting stock returns in the cross-section, in: `Lecture Notes in Computer Science (including subseries Lecture Notes in Artificial Intelligence and Lecture Notes in Bioinformatics)`, vol. 10937 LNAI, pp. 273–284, 2018.

4. Kumar, D.A., Silkworm Growth Monitoring Smart Sericulture System based on Internet of Things (IOT) and Image Processing. `Int. J. Comput. Appl`., 180, 18, 975–8887, 2018.

5. S.P., Rajanna, G.S., Chethan, D., Application of Image Analysis methods for Quantification of Fecundity in Silkworm Bombyx mori L, in: `International Sericulture Commission`, Research Papers, 2015 ([`www.inserco.org/en/previous_issue`](http://www.inserco.org/en/previous_issue)).

6. Kiratiratanapruk, K., Watcharapinchai, N., Methasate, I., Sinthupinyo, W., Silkworm eggs detection and classification using image analysis, in: `2014 International Computer Science and Engineering Conference, ICSEC 2014`, pp. 340–345, 2014.

7. Pandit, A., Rangole, J., Shastri, R., Deosarkar, S., Vision system for automatic counting of silkworm eggs, `2014 International Conference on Information Communication and Embedded Systems, ICICES 2014`, no. 978, pp. 1–5, 2015.

8. Kiratiratanapruk, K. and Sinthupinyo, W., Worm egg segmentation based centroid detection in low contrast image, in: `2012 International Symposium on Communications and Information Technologies, ISCIT 2012`, pp. 1139–1143, 2012.

9. Pathan, S., Harale, A., Student, P.G., A Method of Automatic Silkworm Eggs Counting System. `Int. J. Innovative Res. Comput. Commun. Eng`., 4, 12, 25, 2016.

10. K.P.R., Sanjeev Poojary, L., M.G.V., S.N.K., An Image Processing Algorithm for Silkworm Egg Counting. `Perspect. Commun. Embedded-Syst. Signal-Process. (PiCES)`, 1, 4, 2566–932, 2017.

11. Matas, J., Galambos, C., Kittler, J., Robust Detection of Lines Using the Progressive Probabilistic Hough Transform. `Comput. Vision Image Understanding`, 78, 1, 119–137, Apr. 2000.

12. Nikitha, R.N., Srinidhi, R.G., Harshith, R., Amar, T., Raghavendra, C.G., Reckoning the hatch rate of multivoltine silkworm eggs by differentiating yellow grains from white shells using blob analysis technique, in: `Advances in Intelligent Systems and Computing`, vol. 709, pp. 497–506, 2018.

13. F. und T. des L. N.-W. Ministerium für Innovation and Wissenschaft, Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks. `Advances in neural information processing systems`, 2015.

14. Özdener, A.E. and Rivkin, A., You Only Look Once: Unified, Real-Time Object Detection Joseph. `Drug Des. Devel. Ther`., abs/1506.02640, 11, 2827–2840, 2015.
