

## 2.5 Model validation and evaluation

Evaluate the trained model on a separate validation set to assess its performance. Accuracy, precision, recall, F1-score, and area under the receiver operating characteristic curve (AUC-ROC) are examples of common evaluation measures.

![](img/9eefc6d2972274efeb1680c6a31895e5_253_0.png)

Figure 1. System design for bone cancer detection (Gawade et al. 2023).

## 3 RESULTS & LITERATURE REVIEW

The suggested architecture is designed to employ supervised deep-learning techniques for model construction. Its architecture was more appropriate for osteosarcoma detection. The DenseNet201 model has an F1-score of 85.5% and an accuracy of 87.15%. v score, an accuracy of 84.38%, recall of 87.15%, and an AUC of 0.9093 of 1.907, meaning that the metrics were the lowest of all the tested models. are comparable to VGG16, however, the time factor causes the v-score to be low. With an F1-score of 89.35% and an accuracy of 90.36%, the ResNet101 model v score, an accuracy of 89.51%, recall of 89.59%, and an AUC of 0.9461 of 2.72, the greatest value about other models, the residual In comparison with different replicas, the neural System (ResNet101) performed excellent, taking the shortest amount of time to train and having the highest accuracy (Gawade et al. 2023).

![](img/9eefc6d2972274efeb1680c6a31895e5_253_1.png)

Figure 2. Validation of all models with accuracy (Gawade et al. 2023).

![](img/9eefc6d2972274efeb1680c6a31895e5_254_0.png)

Figure 3. Validation loss of all models (Gawade et al. 2023).

Table 1. Algorithms' performance using the dataset (Gawade et al. 2023).

| Parameters | VGG16 | VGG19 | DenseNet201 | ResNet101 |
| :--- | :--- | :--- | :--- | :--- |
| Accuracy Results | 86.6% | 89.4% | 87.2% | 90.6% |
| F1 Score Result | 85.5% | 88.3% | 85.5% | 89.3% |
| Precision Results | 84.3% | 87.7% | 84.3% | 89.5% |
| Recall score | 87.2% | 88.9% | 87.2% | 89.5% |
| AUC Results | 0.90 | 0.932 | 0.0 | 0.94 |

Table 2. Literature review of bone cancer.

| Sr No. | Authors | Disease Types | Techniques used | Data set | Result |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Gawade, S.Bhansali, A. Patil, k. (2023) | Bone Cancer | CNN((ResNet101, VGG16, VGG19) | X-Ray images | ResNet101 Highest Accuracy 90.36%). |
| 2 | Anisuzzaman, D. Hosein, B. Ling, T. Jake, L. (2021) | Osteosarcoma | CNN (Con-Volutional Neural Networks) VGG-19, Inception V3. | Histological Images(Osteosarcoma data-set) | With accuracy of 93.91% and 95.65% in multi-class and binary classifications, respectively, the, VGG19 model performed best. |
| 3 | Vandana, B. Sathyavathi, A. (2021) | Bone Cancer | Convolution Neural Network (CNN) | Images from histopathology. | Threatening, harmless, and ordinary and the achievement rate is 92%. |
| 4 | Madhuri, A. Narasimha, P. (2014) | Bone Cancer | K Means Clustering | MRI Images | Bone cancer detection with a 95 percent accuracy rate. |
| 5 | Nikita, J. Deepak, K. Ayush, K. (2020) | White Blood | Convolutional Neural Network (CNN) | Bone Marrow-Microscopic Images. | Determine the various types of cancer found in the bone marrow. |
| 6 | Sharma, A. Yadav, D. Garg, H. (2021) | Bone Cancer | Random Forest & SVM | X-ray Pictures. | For the categorization of malignant bones, the F1-score of 0.94 is superior to the F1-score of 0.88 in the work. RF 89% & SVM 92%. |
| 7 | Abhilash, S. Atul, P. (2020) | Bone Cancer | Image Segmentation | X-Ray & MRI. | Detects Osteosarcoma cancer present in bone. |
| 8 | Satheesh, B. Sathiyaprasad N. (2021) | Bone Cancer | KNN classifier. | X-rays and MRI. | Identifying the present or absent of a tumor or absent of a tumor in the input MRI and whether it has been diagnosed as benign or malignant after this |
| 9 | Jabber, J. Shankar, M. Rao, V. (2020) | Benign and malignant. | SVM & PNN | MRI Images | SVM with 92% accuracy is achieved. PNN accuracy 84%. |

So, we are currently conducting an inclusive study on the prediction of bone cancer utilizing Machine Learning and Deep Learning techniques. covers nine distinct publications on different types of bone cancer, including primary and secondary bone cancer. There are several methods for making predictions.

## 4 DATA SET

One kind of malignant tumor that develops in a bone is called osteosarcoma. Although any bone can experience it, long bones are more likely to do so. Osteosarcoma is most common in people between the ages of 10 and 25, particularly in adolescents, and it recurs in older adults over 60. This dataset contains images of the micro anatomy of osteosarcoma stained with hematoxylin and eosin (H and E). A team of clinical professionals from the University of Texas, Dallas oversaw the data collection process. Fifty patients receiving treatment at the Medical Center of Children in Dallas served as an acceptable sample for the creation of this dataset. The medical examiner selected 4 out of 50 patients based on the tumor samples’ dissimilarities following clinical surgery. The images were labeled with the three most common kinds of cancer: necrosis, viable tumor, and non-tumor. The clarification was done by two clinical scientists. This dataset consists of 1144 1024 x 1024 images with ten times the resolution.

## 5 CONCLUSION & FUTURE SCOPE

According to the study’s findings, Cancerous Tumor was identified by consuming deep learning-based replicas. Using transfer learning, Groups (DenseNet201), and (ResNet101) were linked with modified ANN layers on top of the (VGG16). The (ResNet101) model performed better in this study than the previously used image net models, with an accuracy rate of 90.36%. Future cancer identification may make use of additional replicas such as different available deep learning Models as they might be able to identify cancer more accurately.

## REFERENCES

A. A. et al., 2018. Feature extraction to detect Bone Cancer Using Image Processing. Research Journal of Pharmaceutical, Biological and Chemical, 8(3), pp. 434-442.

Avula, M., Lakkakula, N. P. & Raja, M. P., 2014. Bone Cancer Detection from MRI Scan Imagery Using Mean Pixel Intensity. Taipei, Taiwan, IEEE.
Bhukya, J. et al., 2020. SVM Model-based Computerized Bone Cancer Detection. Coimbatore, India, IEEE.
Gawade, S., Bhansali, A., Patil, K. & Shaikh, D., 2023. Application of the convolutional neural networks and supervised. elsevier, 2023(3), pp. 2772–4425.
Hela, B., Hela, M. & Kamel, H., 2018. Bone Cancer Diagnosis Using GGD Analysis. Yasmine Hammamet, Tunisia, IEEE.
K, S. et al., 2018. Screening and Identify the Bone Cancer/Tumor using Image Processing. Coimbatore, India, IEEE.
Kumar, S. & B, S., 2021. Bone cancer detection using feature extraction with classification using k-nearest neighbor and decision tree algorithm. Smart Intelligent Computing and Communication Technology, 4(10), pp. 347–353.
Papandrianos, N., Papageorgiou , E. & Anagnostis, A., 2020. Efficient bone metastasis diagnosis in bone scintigraphy using a fast convolutional neural network architecture. Multidisciplinary Digital Publishing Institute, 10(8), p. 532.
S, P. et al., 2021. An approach to detect and classify bone tumour using fast and robust. Annals of the Romanian Society for Cell Biology, 25(6), p. 13736–13741.
Sharma, A. et al., 2021. Bone cancer detection using feature extraction based machine. Computational and Mathematical Methods in Medicine, Volume 2021.
Shrivastava, D., Sanyal, S., Maji, A. K. & Kandar, D., 2020. Bone cancer detection using machine learning techniques. In: S. P. a. D. Bhatia, ed. Smart Healthcare for Disease Diagnosis and Prevention. India: Academic Press, pp. 175–183.
Shukla, A. and Patel, D., March 30, 2020. Bone cancer detection from x-ray and mri images through image segmentation techniques. International Journal of Recent Technology and Engineering (IJRTE), 8 (6), pp. 273–278.

## Optimized deep learning models based-sentiment analysis approach for identifying healthcare rumors over social media

Pramod Kumar
Computer Science and Technology, Ganga Institute of Technology and Management, Kablana, Jhajjar, Haryana, India

Ela Vashishtha
Lead Analytics, Texas Health Resources, Texas, USA

Faisal Yousef Alghayadh
Computer Science and Information Systems Department, College of Applied Sciences, AlMaarefa University, Riyadh, Saudi Arabia

Mohammed Wasim Bhatt
Model Institute of Engineering and Technology, Jammu, J&K, India

Suchitra Bala
ICT & Cognitive Systems, Sri Krishna Arts and Science College, India

Sreejitha T.S.
St. Marys College Thrissur, India

ABSTRACT: Research the mechanism of fake news refuting rumors in the real social network environment. Propose methods to evaluate the effect of rumor refuting and explore the factors that affect the impact of rumor refuting. Based on the current research results and assumptions, eight factors that affect the effect of rumor refuting are summed up, such as the proportion of the original fake news content. Experiments were conducted based on the rumor-refuting Weibo data. The experimental analysis showed that the proportion of the original fake news in the rumor-refuting information was negatively correlated with the rumor-refuting effect, and the explanation was positively correlated with the rumor-refuting effect suggestions for refuting rumors, including explaining why the original fake news is wrong to guiding social network fake news denying rumors.

### 1 INTRODUCTION

Necessary convenience, high dissemination and low social network threshold facilitated the widespread dissemination of fake news (Shrivastava et al. 2020). Consistent with trustworthy information, Fake news has the characteristics of fast dissemination, vast influence, and dissemination. The network topology and other features have caused significant social problems—negative impacts. Since the end of January 2020, fake news of pneumonia has spread widely on social networks for epidemic prevention workers. The orderly development has brought significant obstacles. Social network fake news (Matsumoto et al. 2021). Build a dissemination model for disinformation based on accurate data, but Most of these studies ignore the mechanism of refuting rumors and the mechanism of audience cognition. In psychology and sociology, the research on the tool of rumor refutation is more in-depth. (Yang 2021) analysis revealed the perceived reasons why fake news is difficult to refute. One of the factors is motivated reasoning; (Alkawaz et al. 2021) found a Targeted refutation of rumors that will negatively impact people; this effect is called the backfire effect of refuting rumors. In addition,

