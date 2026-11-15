
## 7.5 Proposed Model of Image Forgery Detection, Results and Discussion

The flow chart of the novel CNN model for image forgery detection is revealed in Figure 7.4. The model consists of the multilayer ConvNet with more than one convolution, ReLU and pooling layers. The proposed model is trained with a Kaggle dataset named CASIA1. The CASIA1 is further divided into two parts: dataset 1 and dataset 2. During the testing phase, the input layer has been fed with image with the size of 256 × 256 × 3. The image goes under different layers of multilayer ConvNet. This model uses “ReLU” as an activation function and max pooling as pooling activity. In the output layer to acquire the binary decision, the image is forged and the simple activation function “sigmoid” is used. After obtaining the binary output, if the output is “1” the image is forged, otherwise a normal image. On training the network with two datasets obtained from Kaggle website (CASIA1), the graphs of loss functions (LF) and accuracy are described below for both training and validation. The network training and validation has been performed with Google Colab notebook. Figure 7.5 shows training loss and accuracy for dataset 1. In Figure 7.5, the Y-axis represents the normalized accuracy and X-axis defines number of epochs.

From Figure 7.5 it can be deduced that the proposed model has achieved around 99% accuracy during the training process and around 91% accuracy during validation process. The complete simulation models have been tested for 100 epochs. The outcomes of the dataset 2 with respect to loss function and accuracy has been presented in Figure 7.6. The simulation setup for dataset 2 is the same as discussed in the earlier case. With dataset 2 also the proposed model shows the stable performance with the image forgery detection accuracy of around 87%. Thus, the simulation results validating the proposed model for image forgery detection has an accuracy of around 90%.

For the proposed ConvNet model, the confusion matrix of test dataset 1 and dataset 2 is represented by Figure 7.7 and Figure 7.8, respectively.

![](img/d2107fc60629942e7da5355e47fcc33d_132_0.png)

Figure 7.4 Flow chart of novel CNN model.

![](img/d2107fc60629942e7da5355e47fcc33d_133_0.png)

Figure 7.5 Training losses and accuracy for dataset 1.

![](img/d2107fc60629942e7da5355e47fcc33d_134_0.png)

Figure 7.6 Training losses and accuracy for dataset 2.

| | |
|---|---|
| 197 | 3 |
| 43 | 257 |

Figure 7.7 Confusion matrix of dataset 1.

| | |
|---|---|
| 179 | 21 |
| 43 | 257 |

Figure 7.8 Confusion matrix of dataset 2.

Accuracy of the proposed model: As per the confusion matrix the normalized accuracy of ConvNet model is represented as follows:

```
Accuracy = (TP + TN)/(TP + TN + FP + FN)
```

The proposed model achieves 0.908 for dataset 1 which implies the model is approx. 91% accurate. For dataset 2 it is around 0.872 which implies the model is approximately 87% accurate.

Precision: The precision of a system is given as follows:

Precision = TP/(TP + FP)

The model presented in this work shows precision of 0.985 for dataset 1, which is truly acceptable and 0.895 for dataset 2, which is really acceptable.

Recall (Sensitivity): The recall of the system can be given by:

Recall = TP/(TP + FN)

The proposed model has a recall of 0.82 for dataset 1 and 0.80 for dataset 2 which is useful for this model.

F1 score: F1 Score is the weighted average of precision and recall and given by:

F1 Score = 2 × (recall × precision)/(recall + precision)

For the model presented here, the F1 score is 0.89 for dataset 1 and 0.84 for dataset 2.

## 7.6 Conclusion

In this research work, a novel CNN model along with error level analysis has been presented for image forgery detection. The suggested model has been validated with Kaggle's CASIA1 dataset. It has been found that the model performs with 91% accuracy for dataset 1 and around 87% accuracy for dataset 2. The detailed efficacy of the system is measured based on the confusion matrix for both the datasets. It is concluded that the system has a normalized precision of 0.98 and 0.89 for dataset 1 and dataset 2, respectively. Further, the proposed model is tested for recall and F1 score. For all the performance major criteria, performance of the model was found satisfactory. On the basis of the proposed novel model an android application can be developed in the near future. The application will determine whether the particular image is digitally altered/edited or not.

## 7.7 Future Research Directions

ICT along with cloud computing techniques ensures a robust scheme for machine learning (ML) and deep learning (DL) skills. Recently researchers investigated the 5G system as a candidate to offer groundwork for intelligent wireless networks to deal with congregated claims. ML-centered signal processing algorithms can pave the way to the progress of future intelligent wireless networks (B5G). DL typically comprises two phases, viz. training and testing. In practical application of real communications systems only the testing phase is useful. The training phase is customarily finished offline. A trained DL model can thus accomplish many objectives lacking the requirement for retraining. In this regard, we can use the proposed CNN algorithm with some modifications.

The implementation of CNN in Automatic modulation classification (AMC) has revealed hopeful accuracy. AMC is the method of categorizing the modulation pattern of a signal and is an essential method of non-cooperative communication. By using time-frequency channeled input to CNN, an enhancement of feature dimension will occur for CNN input. Henceforth the lost info like phase or frequency deviation can be simply caught in energy variation of time-frequency map. Hence the CNN method proposed here can be applied in AMC for enhancing the classification capability.

## References

- 1. Madhusmita Mishra; LDPC Codes and Digital Forensics – A Perspective Approach. IETE Journal of Research 2019, pp. 1–8.
- 2. S. B. Basavarajappa and S. Sathyanarayana; Digital image forgery detection techniques: a survey. ACCENTS Transactions on Information Security 2016; pp. 22–31.
- 3. H. Farid; Image forgery detection. IEEE Signal Processing Magazine 2009; pp. 16–25.
- 4. A Dureja; P Pahwa; Image Retrieval Techniques: A survey. International Journal of Engineering & Technology. 2018, pp. 215–219.
- 5. A Krizhevsky; I Sutskever; G E Hinton; Imagenet classification with deep convolutional neural networks. Advances in Neural Information Processing Systems. 2012, pp. 1097–1105.
- 6. P Mishra; N Mishra; S Sharma; R Patel; Region duplication forgery detection technique based on SURF and HAC. Scientific World Journal. 2013.
- 7. A C Popescu; H. Farid; Exposing digital forgeries in colour filter array interpolated images. 2005, pp. 3948–3959.
- 8. J Chen; X Kang; Y Liu; Z J Wang; Median filtering forensics based on convolutional neural networks. IEEE Signal Processing Letters. 2015, pp. 1849–1853.
- 9. M D Ansari; S P Ghera; V Tyagi; Pixel-Based Image Forgery Detection: A Review. IETE J Education. 2014, pp. 40–46.
- 10. N. Krawetz; A picture’s worth… Digital Image Analysis and Forensics. Hacker Factor Solutions. 2007.
- 11. Birajdar GK; Mankar VH; Digital image forgery detection using passive techniques: A survey, Digital Investigation 2013, pp. 226–245.
- 12. Gu J; Wang Z; Kuen J; Ma L; Shahroudy A; Shuai B et al.; Recent advances in convolutional neural networks. Pattern Recognition 2018, pp. 354–377.
- 13. Liu S; Deng W; Very deep convolutional neural network based image classification using small training sample size. 3rd IAPR Asian Conference on Pattern Recognition (ACPR) 2015.
- 14. Han H; Li Y; Zhu, X.; Convolutional neural network learning for generic data classification. Information Sciences 2019, pp. 448–465.
- 15. D M Uliyan; H A Jalab; A W A Wahab; P Shivakumara; S Sadeghi; A novel forged blurred regional detection system for image forensic applications”, Expert Systems with Applications 2016, pp. 1–10.
- 16. S Walia; K Kumar; Digital image forgery detection: a systematic scrutiny. Australian Journal of Forensic Sciences 2018, pp. 1–39.
- 17. J Zhang; W Zhu; B Li; W Hu; J Yang; Image copy detection based on convolutional neural networks, Chinese Conference on Pattern Recognition 2016, pp. 111–121.
- 18. Y Zhang; J Goh; L L Win; V L Thing; Image Region Forgery Detection: A Deep Learning Approach. Proceedings of the Singapore Cyber-Security Conference (SG-CRC). 2016, pp. 1–11.
- 19. J Zhou; J Ni; Y Rao; Block-Based Convolutional Neural Network for Image Forgery Detection. International Workshop on Digital Watermarking. 2017, pp. 65–76.
- 20. Doegar Amit; Dutta Maitreyee; Gaurav Kumar; CNN Based Image Forgery Detection Using Pre-trained AlexNet Model. International Journal of Computational Intelligence & IoT. 2019.
- 21. C. N. Bharti; P. Tandel; A survey of image forgery detection techniques. International Conference on Wireless Communications, Signal Processing and Networking (WiSPNET). IEEE. 2016, pp. 877–881.
- 22. Factor H Foto; Forensics Online for ELA. 2012.
- 23. J Chen; X Kang; Y Liu; Z J Wang; Median filtering forensics based on convolutional neural networks. IEEE Signal Processing Letters. 2015, pp. 1849–1853.
- 24. M D Ansari; S P Ghera; V Tyagi; Pixel-Based Image Forgery Detection: A Review. IETE J Education. 2014. pp. 40–46.
- 25. Yan Zhao et al.; Digital Image Manipulation Forensics. Technical Report No. UCB/EECS-2015-85. 2015.
- 26. Birajdar GK; Mankar VH; Digital image forgery detection using passive techniques: A survey. Digital Investigation. 2013. pp. 226–245.
