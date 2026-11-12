
It is extremely flexible as it allows the user to define the number of desired clusters and can be integrated with other techniques, such as geographical information, to improve segmentation (Figure 13.5).

![](img/e7e1b4040cce350b0d1520d1f0df754d_237_0.png)

FIGURE 13.5 Fuzzy c-mean segmentation.

Overall, FCM is a powerful and widely used algorithm for image segmentation that offers flexibility and robustness in handling complex image data.

### 13.4.5 TRAINING MODEL

This project was completed utilizing ResNet-50 as a training model. ResNet-50 is a deep neural network architecture that has garnered popularity in computer vision tasks since Microsoft Research Asia's introduction of it in 2015.

This 50-layer architecture is a variant of the ResNet family of neural networks, which is well-known for tackling the problem of vanishing gradients by introducing the skip connection model. By enabling information to flow from earlier to later network layers, these skip connections help preserve essential features and reduce the impact of vanishing gradients.

ResNet-50 has achieved cutting-edge performance on a variety of benchmark datasets, including ImageNet, COCO, and PASCAL VOC, making it a popular choice for image classification, object recognition, and segmentation applications. Furthermore, the ResNet-50 architecture is extensively used for transfer learning, which involves applying pretrained models to new datasets with less training data to train them.

In conclusion, ResNet-50 is an important advancement in the field of deep learning. It offers an efficient method for the training of very deep neural networks and accomplishes remarkable outcomes across a variety of different existing computer vision tasks (Figure 13.6).

![](img/e7e1b4040cce350b0d1520d1f0df754d_238_0.png)

FIGURE 13.6 Architecture of ResNet-50.

## 13.4 RESULT AND DISCUSSION

The training and validation loss and accuracy of every epoch is given below.

| Epoch | Training Loss | Training Accuracy | Validation Loss | Validation Accuracy |
|---|---|---|---|---|
| I | 1.3198 | 0.9680 | 1.3290 | 0.9688 |
| II | 0.2265 | 0.9946 | 0.1878 | 0.9939 |
| III | 0.0809 | 0.9975 | 1.1236 | 0.9827 |
| IV | 0.1360 | 0.9957 | 1.3337 | 0.9653 |
| V | 0.0672 | 0.9975 | 0.2728 | 0.9913 |
| VI | 0.0312 | 0.9984 | 0.6057 | 0.9896 |
| VII | 0.0334 | 0.9988 | 0.1432 | 0.9948 |
| VIII | 0.0169 | 0.9990 | 0.2503 | 0.9913 |
| IX | 0.0169 | 0.9992 | 0.2863 | 0.9939 |
| X | 0.0105 | 0.9994 | 0.2636 | 0.9887 |
| XI | 0.0467 | 0.9979 | 0.4122 | 0.9801 |
| XII | 0.0045 | 0.9994 | 0.5453 | 0.9896 |
| XIII | 0.1585 | 0.9840 | 0.2636 | 0.9853 |
| XIV | 0.0899 | 0.9963 | 0.1852 | 0.9939 |
| XV | 0.0621 | 0.9957 | 1.3052 | 0.9809 |
| XVI | 0.0898 | 0.9973 | 0.7436 | 0.9740 |
| XVII | 0.0141 | 0.9988 | 0.5381 | 0.9887 |

After training the model, we tested it on a training dataset of 923 images and it detects people with mask and without mask with accuracy of 99.56 (Figure 13.7).

```
test_loss,test_acc=model.evaluate(test_generator,verbose=2)
print("\n test accuracy:",test_acc)
923/923 - 136s - loss: 0.1192 - accuracy: 0.9957 - 136s/epoch - 148ms/step
test accuracy: 0.9956663250923157
```

FIGURE 13.7 Accuracy analysis of model.

Our model is capable of detecting the people with and without mask with better accuracy (Figure 13.8).

![](img/e7e1b4040cce350b0d1520d1f0df754d_239_0.png)

FIGURE 13.8 Result.

## 13.5 CONCLUSION

This work concludes with a deep learning and image processing face mask detection method.

CNNs extract and classify features, while image processing detects masks. A massive dataset of pictures with and without masks tested the strategy.

The described method accurately detects face masks with few false positives. The device's real-time detection is ideal for airports, hospitals, and other mask-wearing environments.

This research increases computer vision and pattern recognition and combats infectious diseases like COVID-19 with an automatic and reliable face mask detection system. The strategy could increase public health and mask-wearing compliance, boosting safety and well-being.

Masks worn incorrectly or partially covered may cause false negatives with the suggested approach. Research could improve the algorithm's robustness. Using the suggested technology requires considering privacy, ethics, and human factors.

In conclusion, deep learning and image processing algorithms can detect face masks, and further research could affect public health and safety.

## KEYWORDS

- COVID-19
- bilinear interpolation
- face mask bilateral
- filter
- fuzzy c-mean segmentation
- deep learning
- ResNet-50

## REFERENCES

- 1. Wang Z, Wang G, Huang B, Xiong Z, Hong Q, Wu H, Yi P, et al. Masked face recognition dataset and application. arXiv preprint arXiv:2003.09093 (2020).
- 2. Yuheng S, Hao Y. Image segmentation algorithms overview. arXiv preprint arXiv:1707.02051 (2017).
- 3. Selvakumar J, Lakshmi A, Arivoli T. Brain tumor segmentation and its area calculation in brain MR images using K-mean clustering and Fuzzy C-mean algorithm. In: IEEE-International Conference on Advances in Engineering, Science and Management (ICAESM-2012). IEEE, 2012, pp. 186–190.
- 4. Meivel S, Sindhwani N, Anand R, Pandey D, Alnuaim AA, Altheneyasan AS, Jabarulla MY, Lelisho ME. Mask detection and social distance identification using internet of things and faster R-CNN algorithm. Computational Intelligence and Neuroscience. 2022;2022:2103975.
- 5. Ren S, et al. Faster R-CNN: Towards real-time object detection with region proposal networks. In: Advances in Neural Information Processing Systems. 2015, Vol. 28.
- 6. Shiekh B. Face mask dataset, version 1; September 2022. https://www.kaggle.com/datasets/ashishjangra27/face-mask-12k-images-dataset (accessed Mar. 22, 2023).
- 7. Chakraborty A. Face mask detection data, version 1; 2019. https://www.kaggle.com/datasets/aneerbanchakraborty/face-mask-detection-data/code (accessed Mar. 14, 2023).
- 8. https://github.com/cabani/MaskedFace-Net
- 9. Jangra A. Face mask detection ~12K images dataset, version 1; 2020. https://www.kaggle.com/datasets/shiekhburhan/face-mask-dataset (accessed March 20, 2023).

![](img/e7e1b4040cce350b0d1520d1f0df754d_242_0.png)

Taylor & Francis
Taylor & Francis Group
http://taylorandfrancis.com

## Index

- A
- Accidents/incidents/near-misses, 174
  - reports, 174
- AdaBoost, 56
- Adaptive gradient boost (AB), 3, 6
- Adjusted geometric mean (AGm), 10
- Advanced encryption standard (AES), 132
- Amazon Echo, 92
- Apache Clinical Text Analysis, 57
- Apple Siri, 151
- Artificial intelligence (AI) computing, 52, 128
- access to healthcare, 95–96
- accuracy of diagnoses, 147
- administrative applications, 88
- anytime access, 93
- automated medical practice, 95
- benefits, 93–99
- cost effectiveness, 96
- data availability, issue of, 100
- Deep Blue, 84
- democratization of knowledge, 94
- development of smart prosthetics, 98–99
- diagnosis and treatment applications, 87–88
- discriminant examination, 98
- driven automation, 141
- facilitating medical diagnostics, 88–89
- in healthcare, 85–87, 128, 132
- healthcare bots, 93
- in healthcare marketing, 89–90
- hybrid AI systems, 147
- in identification of disease risks, 96
- image analysis, 94
- in learning and problem-solving, 84–85
- in medical procedure, 98
- medical tools, 84
- natural language processing (NLP), 86
- nirvana fallacy, 101
- patient–physician relations and, 101–102
- privacy concerns, 100
- professional realignment, 101
- in reducing medication nonadherence, 90–91
- resource allocation and management, 95
- risk of injuries and errors, 99, 102
- risks of bias and disparity, 100–101
- rule-based expert systems, 87
- social prejudices, problem of, 102–103
- unemployment, issue of, 102
- virtual health assistants (VHAs), 91–93
- Artificial neural networks, 97
- Augmented reality (AR), 142, 147
- AutoDock, 117
- AutoDockVina, 117
- Automated calling systems, 92
- Axitinib, 118
- B
- Bagging RF, 56
- Balanced random forest (BRF), 9
- Band-limited phase-only correlation (BLPOC), 196
- Bernoulli naive Bayes (BNB), 3, 5–6
- Biometric system basic block diagram, 198
  - data acquisition, 198
  - database, 199
  - feature extraction, 198–199
  - matching, 199
  - preprocessing algorithm, 198
- Blockchain system, 142, 153
  - smart contracts, 132
- Bow-tie-based risk assessment method, 174
  - data preprocessing, 177–178
  - data visualization, 182–183, 186
  - integrating NLP, 176
  - for leaked gas event, 185
  - levels of failure, 183
  - root causation, 186
  - for slipped event, 185
