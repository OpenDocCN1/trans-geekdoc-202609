
# Text Separation From Document Images

Figure 16. (a) Quantitative Analysis and (b) Training and Validation Loss of U-Net

![](img/c5cbbc72cd5e7b9be32079eac36d685c_326_0.png)

Figure 17. (a) Low-level feature map of the model, (b) Mid-level feature map

![](img/c5cbbc72cd5e7b9be32079eac36d685c_326_1.png)

Figure 18. (a) High-level feature map of the model, (b) Segmented output

![](img/c5cbbc72cd5e7b9be32079eac36d685c_326_2.png)

Figure 19. (a) Quantitative Analysis and (b) Training and Validation Loss of ResU-Net

![](img/c5cbbc72cd5e7b9be32079eac36d685c_327_0.png)

### c. Results of U-Net and ResU-Net Results on test data

Table 1 shows the quantitative analysis on both deep models (U-Net and ResU-Net) which were finuned on the document test dataset. The results of ResU-Net are better than U-Net due to the presence of the residual connections in.

Table 1. Comparative results of text segmentation of Devnagari scanned images on U-Net and ResU-Net model

| Parameters | U-Net | ResU-Net |
|---|---|---|
| Accuracy | 0.9763 | 95.031% | 98.802% |
| Precision | | 94.729% | 98.480% |
| Recall | | 80.4912% | 83.220% |
| F1-Score | | 86.106% | 90.032% |

# SUMMARY (COMPARISON OF TRADITIONAL TECHNIQUES WITH THE DEEP LEARNING APPROACH)

Conventional or traditional image processing requires the features that need to be classified to be hand-coded. The image needs to be analysed at every step in traditional methods of image processing. Pre-processing, transformations, and identification of filters are some necessary steps to apply the input to find the features. As discussed in the chapter, text extraction using traditional image processing methods includes pre-processing, block extraction, perimeter detection, and text extraction. On the other hand, deep learning learns the features while training the models. The network is very deep and is made up of a large number of layers of neurons. Each layer has features extracted at the output of the layers. Different deep learning models have proven to give state-of-the-art results. The collection of the dataset for training the model is extensive and requires more powerful machines to train the model. It provides excellent results when the dataset is large. Conventional image processing is still used when the dataset is not vast. Transfer learning transfers knowledge from one model to another, similar to what a human does when learning some task. Thus, it makes deep learning accurate results and solves the more complex tasks.

Despite various advantages of deep learning, it suffers from disadvantages too. Deep learning is data-hungry. The dataset used in the chapters are created by the author, which requires human efforts. Again, the deep networks are costly during training, as they require expensive GPUs for implementation. The selection of the network is also a cumbersome task. There is no standard theory available to select the appropriate network. Deep learning requires knowledge of topology, and training methods for designing and selecting any network.

# CONCLUSION

Research in the field of text extraction from document images is explored in this chapter. Traditional image processing and deep learning methods using transfer learning (fine-tuning the base model) for Devnagari text separation are explored. From the literature survey, it is evident that there are four types of approaches for segmenting text: top-bottom, bottom-up, hybrid, and deep learning.

For conventional methods, the features need to be hand-coded which is required for text extraction, while in the deep learning approach, the features are automated. The deep learning gives better accuracy over conventional methods. A transfer learning method of fine-tuning the base model (U-Net and ResU-Net) improves the result. U-Net network yields 95% segmentation accuracy on data while ResU-Net gets 98% accuracy. The higher efficiency of the ResU-Net is due to the presence of residual connections present in the network. Further, word and line segmentation can be added to the proposed model for Optical Character Recognition. Accuracy of the proposed model for Devnagari text segmentation can be further improved by designing new deep network models.

# REFERENCES

Ashfine Amidi and Shervine Amidi. (2018). Deep learning cheatsheet [CS 229 - Machine Learning], Retrieved from https://stanford.edu/shervine/teaching/cs-229/cheatsheet-deep-learning

Amin, A., & Shiu, R. (2001). Page segmentation and classification using bottom-up approach. International Journal of Image and Graphics, 1(02), 345–361. doi:10.1142/S0219467810002219

Antonacopoulos, A., & Richards, R. T. (1995). Segmentation and classification of document images. Academic Press.

Badrinarayan, V., Kendall, A., & Cipolla, R. (2017). Segnet: A deep convolutional encoder-decoder architecture for image segmentation. Transactions on Pattern Analysis and Machine Intelligence, 39(12), 2481–2495. doi:10.1109/TPAMI.2016.264615 PMID:28060704

Belabid, A., & Belaid, A. (2018). Line and Word Segmentation of handwritten documents. Neural Networks.

Boulid, Y., Souhar, A., & Elkattan, M. (2015, December). Arabic text extraction based on connected component analysis from a multi agent perspective. In 2015 15th International Conference on Systems Design and Applications (ISDA) (pp. 80-87). 10.1109/ISDA.2015.748920

Bourbakis, N. G. (1996, November). A methodology of segmenting text using OCR. In Proceedings International Symposium on Intelligence (pp. 311-317). 10.1109/IISYS.1996.565084

Chen, K., Sekret, M., Miwicki, M., Hennebert, J., & Ingrid, R. (2015). Page segmentation of historical document with convolutional autoencoders. In 2015 13th International Conference on Document Analysis and Recognition (ICDAR) (pp. 1011-1015).

Dai, J., He, K., & Sun, J. (2016). Instance-aware semantic segmentation via multi-task cascades. In IEEE Conference on Computer Vision and Pattern Recognition (pp. 3150-3158). 10.1109/CVPR.2016.343

Duan, L., Yuan, B., Wu, C., Li, J., & Guo, Q. (2015). Text-image indexing based on extreme machine learning. In ELM (vol. 2, pp. 299-307). Springer. 10.1007/978-3-319-14066-7

Fan, K. C., Wang, L. S., & Wang, Y. K. (1995). Segmentation of mixed text/graphics documents. Pattern Recognition Letters, 15(2), 1201–1209. doi:10.1016/0167-8655(94)9011

Fan, K. C., Wang, L. S., & Wang, Y. K. (1995). Page segmentation and identification for intelligent signal processing. Signal Processing, 45(3), 329–346. doi:10.1016/0165-1684(95)0006-H

He, K., Zhang, X., Ren, S., & Sun, J. (2016, October). Identity mappings in deep residual networks. European conference on vision (pp. 630-645).

Katy, Y. (2019). DNN Processing for Image, Audio, and Video. O'Reilly Media, Inc.

rizsky, A., Nayef, N., Visani, M., Ojizer, J. M., & Tran, C. (2015). Image classification with deep convolutional neural networks. In Advances in neural processing systems (pp. 1097-1105).

Le, V. P., Nayef, N., Visani, M., Ojizer, J. M. (2015). Text and non-segmentation based on connected component features. In 2015 13th International Conference on Document Analysis and Recognition (ICDAR) (pp. 1096-1100). 10.1109/ICDAR.2015.7339330

Lee, K. H., Choy, Y. C., & Cho, S. B. (2000). Geometric structure analysis of document images: A knowledge-based approach. Transactions on Pattern Analysis and Machine Intelligence, 22(11), 1224–1240. doi:10.1109/34-88808

Long, J., Shelhamer, E., & Darrell, T. (2015). Fully convolutional networks for semantic segmentation. Proceedings of the IEEE conference on computer vision and pattern recognition (pp. 3431-3440)..

MATLAB and Statistics Toolbox Release. (2018b). Natick, MA: The MathWorks, Inc.

Mitchell, P. E., & Yan, H. (2001). Newspaper document analysis featuring connected line segmentation. In Proceedings of Sixth International Conference on Document Analysis and Recognition (pp. 1181-1185). 10.1109/ICDAR.2001.953971

Nagy, G., & Seth, S. C. (1984). Hierarchical representation of optically scanned documents. Academic Press.

Nandedekar, A. V., Mukhopadhyay, J., & Rural, S, (2015, August). Text-graphics separation to detect logo and stamp from document images: a spectral approach. In 2015 13th International Conference on Document Analysis and Recognition (ICDAR) (pp. 571-575). IEEE.

Oliveira, S. A., Seguin, B., & Kaplan, F. (2018, August), dbSegment: A generic deep-learning approach for document segmentation. In 2018 16th International Conference on Frontiers in Handwriting Recognition (ICFHR) (pp. 7-12). IEEE.

Oyedun, O. K., & Kashman, A. (2016). Document segmentation using textual features and feedforward neural network. Applied Intelligence, 45(1),198-212. doi:10.1007/s11701-015-3400-2
