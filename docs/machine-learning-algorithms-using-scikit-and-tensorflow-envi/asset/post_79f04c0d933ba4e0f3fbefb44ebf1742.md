
Figure 2. Workflow of the proposed system

![](img/20813928ec98c7f6fbdbab0d52bde2f1_139_0.png)

mental work in this section. There are a total of 5228 images, with 1626 confirmed as COVID-19 cases, 1802 categorized as normal, and 1800 classified as pneumonia.

## 4.2. Preprocessing

Participating in the process involved the development of a classifier model. The sample is isolated from the remaining dataset and sent to the preprocessing stage for additional analysis. When going through the preprocessing stage, it is crucial to consider a variety of factors. It is best to discard data samples that are scrappy or enigmatic. In order to obtain a genuine outcome, a substantial amount of data is essential. In the realm of medical image analysis, data scarcity can pose a significant challenge due to the expensive and time-consuming nature of annotating data.

- **Resize the Image:** Resizing an image involves altering its dimensions, either increasing or decreasing them, while preserving all original content. When we resize the image, its dimensions undergo a change, leading to alterations in both its size and quality.

- **Median Filter:** A nonlinear method for eliminating noise from photos is median filtering. Because of how well it keeps edges while minimizing noise, it is frequently utilized. It’s excellent at eliminating “salt and pepper” noises. The median filter works by iteratively going over each pixel in the picture and substituting the median value of neighbouring pixels for each value. The “window” refers to the neighbor pattern that advances pixel by pixel across the whole picture. The process of calculating the median involves first sorting all of the window’s pixel values into numerical order. Next, the pixel under consideration is swapped out with the pixel with the middle (median) value (Auckland, n.d.; Hasoon et al., 2021).

## 4.3. Feature Extraction

Once the X-ray images have been analyzed, the subsequent stage involves feature extraction. This process reduces the dimensionality of the raw data and transforms it into meaningful information for further processing. The purpose of feature extraction is to streamline the portrayal of an image by converting it into more significant data. Local Binary Pattern (LBP) is a popular image feature extraction operator that is utilised in a wide range of real-world applications. The LBP is a simple yet effective texture extraction operator. The LBP may be employed in sophisticated and real-time image processing applications due to its low computer complexity. It is a synthesis of structural and statistical models (Hasoon et al., 2021). LBP bitmaps are calculated using natural texture as the object. For each LBP bitmap, the histogram will be retrieved. Divide the data into two groups using this histogram as the sample pattern. The initial group will be employed as reference patterns, whereas the subsequent group will be utilized as testing patterns. By averaging numerous sample patterns, a reference pattern can be created. Once the reference patterns are generated, they are stored in the pattern database. In pattern classification, the role of the pattern classifier is to identify the minimum discrepancy between the testing pattern and the reference patterns stored in the database. The input pattern can be identified as belonging to that group if the minimum difference is reached.

## 4.4. Classification

This material is very useful for the researcher and opens up exciting and new opportunities in the field of research. A retention method is used to divide the dataset into training and test data in 80% of train set- 20% test set respectively. KNN, VGG19 and CNN classifiers are selected for classification. KNN is also known as a lazy learner algorithm because it does not learn immediately from the training set; instead, it stores the dataset and performs an operation on it during classification. This algorithm considers the similarity between new instances or data and available instances and places the new instance in a class similar to the existing class, and it may be used for both regression and classification. To determine the variance between the training and test instances, the KNN method employs the Euclidean distance standard. The “K” is the number of nearest neighbours who aid in predicting the test pattern class (Hasoon et al., 2021). With 19 connection layers—16 convolution layers and 3 fully connected levels—the VGG-19 is a deep learning neural network. The fully connected layers categorize the leaf pictures based on the attributes that the convolution layers have extracted from the input photos. Convolutional neural networks, or CNNs for short, are a class of deep learning algorithms used for image processing and analysis. To extract pertinent information from a picture, it does a number of mathematical operations on it, including pooling and convolutions.

## 5. RESULT

A range of performance criteria can be used to evaluate the suggested COVID-19 detection and classification methods. To control the presentation of the suggested structure, a confusion matrix is constructed. Accuracy, precision, recall, and F1-score may be used as performance measures to assess the classification model's performance.

Figure 3. Comparisons among performances of implemented classifiers

![](img/20813928ec98c7f6fbdbab0d52bde2f1_141_0.png)

Accuracy = \(\frac{(TP + TN)}{(TP + FN + TN + FP)} \times 100\) (2)

Precision = \(\frac{TP}{TP + FP}\) (3)

Recall = \(\frac{TP}{TP + FN}\) (4)

F1-score = \(\frac{2 \times (Precision + Recall)}{Precision + Recall}\) (5)

The TP correctly identified X-ray images can be represented by a model predicting positive and also true in the above formula. TN model implies negative and it is truly predicted. FP's model projected a positive outcome, but it turned out to be false. FN predicted a negative outcome, which turned out to be incorrect. These performance measures are suggested in Figure 3, comparisons are made.

## 6. CONCLUSION

Machine Learning and Deep learning are the exciting technologies that are being used in a broad range of sectors, including healthcare. There are several gaps in the literature study, which gives a comprehensive evaluation of different image preprocessing and machine-deep approaches for controlling the COVID-19 outbreak. The proposed model employs a number of techniques, including image pre-processing (such as image resizing, noise removal with median filter), feature extraction (LBP), ml-dl techniques (KNN and VGG19) and hybridization of LBP with CNN for improved results using the confusion matrix and got the highest score as 97.37% (LBP-CNN).

## 7. FUTURE SCOPE

With the help of this research work we will be able to accurately detect disease and able analyze the effectiveness of treatment procedures if require for effective care.

## REFERENCES

- Auckland. (n.d.). https://www.cs.auckland.ac.nz/courss/compsci373s1c/PatricesLectures/Image%20Filtering.pdf

- Benmalek, E., Elmhamdi, J., & Jilbab, A. (2021). Comparing CT scan and chest X-ray imaging for COVID-19 diagnosis. Biomedical Engineering Advances, 1, 100003. doi:10.1016/j.bea.2021.100003 PMID:34786568

- Daniel, C., Cenggoro, T. W., & Pardamean, B. (2023). A systematic literature review of machine learning application in COVID-19 medical image classification. Procedia Computer Science, 216, 749–756. doi:10.1016/j.procs.2022.12.192 PMID:36643182

- Hasoon, J. N., Fadel, A. H., Hameed, R. S., Mostafa, S. A., Khalaf, B. A., Mohammed, M. A., & Nedoma, J. (2021). COVID-19 anomaly detection and classification method based on supervised machine learning of chest X-ray images. Results in Physics, 31, 105045. doi:10.1016/j.rinp.2021.105045 PMID:34840938

- Li, G., Togo, R., Ogawa, T., & Haseyama, M. (2023). Boosting automatic COVID-19 detection performance with self-supervised learning and batch knowledge ensembling. Computers in Biology and Medicine, 158, 106877. doi:10.1016/j.compbiomed.2023.106877 PMID:37019015

- Shah, F. M., Joy, S. K. S., Ahmed, F., Hossain, T., Humaira, M., Ami, A. S., Paul, S., Jim, M. A. R. K., & Ahmed, S. (2021). A Comprehensive Survey of COVID-19 Detection Using Medical Images. SN Computer Science, 2(6), 434. doi:10.100742979-021-00823-1 PMID:34485924

- Shahin, O. R., Alshammari, H. H., Taloba, A. I., & El-Aziz, R. M. A. (2022). Machine Learning Approach for Autonomous Detection and Classification of COVID-19 Virus. Computers & Electrical Engineering: An International Journal, 101, 108055. doi:10.1016/j.compeleceng.2022.108055

- Xu, X., Jiang, X., Ma, C., Du, P., Li, X., Lv, S., Yu, L., Ni, Q., Chen, Y., Su, J., Lang, G., Li, Y., Zhao, H., Liu, J., Xu, K., Ruan, L., Sheng, J., Qiu, Y., Wu, W., ... Li, L. (2020). A Deep Learning System to Screen Novel Coronavirus Disease 2019 Pneumonia. Engineering (Beijing), 6(10), 1122–1129. doi:10.1016/j.eng.2020.04.010 PMID:32837749
