
### Figure 6. ResNet-50 confusion matrix

![](img/20813928ec98c7f6fbdbab0d52bde2f1_124_0.png)

### Table 4. Detail analysis for ResNet-50 model by class

| Class | Recall | Precision | F-Measure | TPR | FPR |
|---|---|---|---|---|---|
| Normal | 77.7% | 83.6% | 80.5% | 77.7% | 22.3% |
| Rust high severity | 79.8% | 83.7% | 81.7% | 79.8% | 20.2% |
| Rust Medium severity | 87.7% | 83.7% | 85.6% | 87.7% | 12.3% |
| Spot high severity | 85.9% | 84% | 84.9% | 85.9% | 14.1% |
| Spot Medium severity | 86.5% | 83.6% | 85% | 86.5% | 13.5% |
| Spot Low severity | 80.1% | 86.1% | 82.9% | 80.1% | 19.9% |
| Weighted average | 84.2% | 84.1% | 84.2% | 84.2% | 15.8% |

## 4.2 VGG-19

It has 19 layers including convolutional layers, pooling layer, and three fully connected layers with three blocks and two of them with 4096 neurons and 1000 neurons which is the output of the class probabilities. Besides, this state-of-art architecture, hyper-parameters, and parameters like the number of filters, filter size, stride, and padding were taken as it is with the default value to train the network. However, the last layers of this network were modified as per the number of the class in this study.

### Figure 7. VGG-19 confusion matrix

![](img/20813928ec98c7f6fbdbab0d52bde2f1_125_0.png)

For this experiment, two test options were tested during training the network by splitting the collected dataset into 80% of the images for training and 20% for testing, 70% of the dataset was assigned for training and 30% of the dataset for testing. Hence, it achieves 90% and 87.3% respectively, and the first test option is selected for detail analysis. So, the following confusion matrix shows the performance of the model.

The researcher has used a confusion matrix to show the experimental results of the developed classification model of coffee leaf diseases. This experiment was conducted by manually splitting the dataset into training and testing. Therefore, out of the 6000 total images, 4800 (80%) of the images were used as a training dataset and the remaining, 1200 (20%) of the images were used as a testing dataset. Therefore, this state-of-art algorithms called VGG-19 scored an accuracy out of 1200 total number of testing images 1,080 (90%) of them were classified correctly and the remaining 120 (10%) testing images were incorrectly classified. Based on all test option results, the first test option has selected for detailed analysis and is presented below in Table.

For this experiment, the researcher has tried to observe the recall, precision, and F1-measure value for better understanding and analyzing of the result. Precision indicates the ratio of properly predicted true classifications to the total predicted true classifications. Recall indicates the properly predicted true classifications of all classifications of the actual class.

### Table 5. Detailed accuracy by class for VGG-19

| Class | Recall | Precision | F-Measure | TPR | FPR |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Normal | 98.8% | 90.8% | 94.6% | 98.8% | 1.2% |
| Rust high severity | 87.3% | 91.5% | 89.3% | 87.3% | 12.7% |
| Rust Medium severity | 90% | 91.6% | 90.7% | 90% | 10% |
| Rust Low severity | 92.9% | 91.3% | 92% | 92.9% | 7.1% |
| Spot high severity | 87.7% | 90% | 88.8% | 87.7% | 12.3% |
| Spot Medium severity | 87.1% | 88% | 87.5% | 87.1% | 12.9% |
| Spot Low severity | 87.7% | 88% | 87.8% | 87.7% | 12.3% |
| Weighted average | 90.2% | 90.17% | 90.1% | 90.2% | 10% |

The experimental result shows that, the developed classifier model using residual network-50 with 80% for training and 20% for testing is 86% accuracy, and the remaining 14% error which is 1,032 records correctly classified, the remaining 168 records are classified incorrectly.

Besides, this pre-trained model also tested the result by 70% for training and 30% for testing, it shows that from 1800 records 1404 records are classified correctly, and the remaining 396 records are incorrectly classified, so it performs 78% accuracy.

Moreover, the researcher have tried to developed the model by using whole extracted features in VGG-19 Pretrained model, via different test option, the first test option is assigned 80% for training and 20% for testing, the result depicts that 960 records are correctly classified, and 240 records are incorrectly classified. Furthermore, this model also applied to develop the model by assigned 70% for training and 30% for testing, and the result is 75%. Generally, the following Figure shows an experimental Analysis using pre-trained model with whole attributes.

Figure 2 shows that the comparison performance of the developed model using both residual network-50 and visual geometry group(VGG-19) via different test options, accordingly, residual network Pre-trained model achieves the best accuracy than visual geometry group having 19 layers in the selected attributes.

The experiment also extended to develop the classifier model using these pre-trained model with selected attributes. Towards selecting the selects an attributes the researcher has information Gain ratio with ratio of 0.5 Energy, Skewness, Correlation, kurtosis, Homogeneity features are selected. The following Figures are depicted that an experiment result with these selected attributes. Additionally, an experiment is done the selected attributes, and the selected attributes is implemented by the pre-trained model and from the scratch namely ResNet50 and VGG-19 by assigning 80% for Training and the remaining 20% for testing, accordingly 91%, 90%, 80% achieved from each model respectively.

An experiment also extended without extracting the necessary features from the given images, in this scenarios, the only thing that we have done is download the pre-trained weight and such as ResNet50 and VGG-19, developing the network from the scratch having 6 layers and compare the performance of this classifier. Accordingly, ResNet-50 have achieved the 98%, and VGG-19 have achieved 94%, from the scratch is achieved 91%, diagrammatically, it seems like the following.

Figure 7 shows that convolutional neural network from

### Figure 8. Pre-trained model with whole attributes

![](img/20813928ec98c7f6fbdbab0d52bde2f1_127_0.png)

### Figure 9. Pre-trained with whole attributes

![](img/20813928ec98c7f6fbdbab0d52bde2f1_127_1.png)

## 5. CONCLUSION AND FUTURE WORKS

This research is mainly focused on developing a classifier model that can be able to detect and recognize a given coffee leaf images and classify as Healthy, Rust with high severity, Middle severity, Low severity, besides, brown spot with high severity, middle Severity, low severity, towards developing this the required data is collected from the south nation and nationalities of people and different preprocessing tasks are applied on the collected images towards making the data more smooth and clean for the actual classification, Finally, convolutions neural network approach such as pre-trained model and training from the scratch are applied by default test option that means assigning 80% for training and the remaining 20% for testing purpose.

Besides, experiments are tested by extracting the necessary features from the given images and given to the convolutional neural network and with extracting the necessary features from the given coffee image that means using convolutional neural network for both feature extraction and classification. Finally, the developed classifier model can be able classify the diseases 98% accuracy by ResNet50.

In the future, recognising a given images and classifying based on the nutrient deficiency and other class label also future research direction.

## ACKNOWLEDGMENT

This research work is supported by Research and Community Service Vice President Office, Wolaita Sodo University, Ethiopia.

## REFERENCES

Al-Hiary, H., Bani-Ahmad, S., Reyalat, M., Braik, M., & Alrahneh, Z. (2011). Fast and accurate detection and classification of plant diseases. International Journal of Computer Applications, 17(1), 31–38. doi:10.5120/2183-2754

Albawi, S., Mohammed, T. A., & Al-Zawi, S. (2017). Understanding of a convolutional neural network. 2017 International Conference on Engineering and Technology (ICET), 1–6. doi:10.1109/ICEngTechnol.2017.8308186

Alemu, K., Adugna, G., Lemessa, F., & Muleta, D. (2016). Current status of coffee berry disease (colletotrichum kahawae waller & bridge) in Ethiopia. Archiv für Phytopathologie und Pflanzenschutz, 49(17-18), 421–433. doi:10.1080/03235408.2016.1228736

Bashir, S., & Sharma, N. (2012). Remote area plant disease detection using image processing. IOSR Journal of Electronics and Communication Engineering, 2(6), 31–34. doi:10.9790/2834-0263134

Esgario, J. G., Krohling, R. A., & Ventura, J. A. (2020). Deep learning for classification and severity estimation of coffee leaf biotic stress. Computers and Electronics in Agriculture, 169, 105162. doi:10.1016/j.compag.2019.105162

Guo & Guo. (2017). Deep learning for visual understanding. Academic Press.

Kumar, M., Gupta, P., & Madhav, P. (2020). Disease detection in coffee plants using convolutional neural network. 2020 5th International Conference on Communication and Electronics Systems (ICCES), 755–760. 10.1109/ICCES48766.2020.9138000

Lewis, K. P., & Espineli, J. D. (2020). Classification and detection of nutritional deficiencies in coffee plants using image processing and convolutional neural network (CNN). International Journal of Scientific and Technology Research, 9(4), 2076–2081.

Manso, G. L., Knidel, H., Krohling, R. A., & Ventura, J. A. (2019). A smartphone application to detection and classification of coffee leaf miner and coffee leaf rust. arXiv preprint arXiv:1904.00742.
