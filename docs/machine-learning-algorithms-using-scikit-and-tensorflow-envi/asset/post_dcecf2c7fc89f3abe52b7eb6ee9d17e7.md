
Figure 3. Proposed framework for fusion of low-level features from the LBP and high-level features from the deep CNN

![](img/20813928ec98c7f6fbdbab0d52bde2f1_250_0.png)

Finally, TensorFlow, a popular open-source machine learning framework, is leveraged for building and training the CNN model, utilizing its rich set of functionalities such as defining neural network layers, optimizing the model with specific loss functions and metrics, and facilitating model compilation, training, and evaluation. Throughout the developmental process, various TensorFlow components, including layers like Conv2D, MaxPooling2D, Dense, Dropout, and BatchNormalization, are intricately integrated to construct a sophisticated CNN architecture tailored for cancer recognition tasks.

Moreover, Scikit-learn, a comprehensive machine learning library, is employed for crucial data pre-processing operations and performance evaluations. Tasks such as data splitting into training and testing sets, label encoding, and standardization of LBP features are efficiently executed using Scikit-learn's diverse functionalities. The library's metrics and evaluation tools, such as classification reports, confusion matrices, and ROC curves, contribute significantly to assessing the model's classification accuracy and visualizing its predictive capabilities.

The combined efforts of both TensorFlow and Scikit-learn in the model ensure a comprehensive approach to model development, training, and evaluation, thereby enhancing the accuracy and robustness of the cancer recognition system. This integration of two powerful libraries underscores the significance of leveraging diverse tools and techniques to achieve optimal results in complex machine learning tasks, ultimately paving the way for advancements in the field of cancer recognition and analysis. To validate the proposed approach, accuracy, precision, recall, and F1-measure are calculated as a part of a controlled experiment.

## 3.1 Dataset

Within the realm of medical imaging and breast cancer investigation, a mammography dataset typically encompasses a compilation of medical images referred to as mammograms. These images are specifically obtained using mammography, a specialized imaging method employing low-dose X-rays to visualize the internal structures of the breast. The images consist of benign and malignant breast masses; benign masses constitute non-cancerous lumps or growths within the breast tissue, resulting from a variety of factors including hormonal fluctuations, inflammation, and fibrocystic changes in breast tissue. While benign masses are usually harmless and do not necessitate treatment, they can sometimes cause discomfort or pain, requiring periodic monitoring. In the analysis of mammography images, distinguishing between benign and malignant masses is critical for precise diagnosis and effective treatment of breast cancer. Malignant masses represent cancerous lumps or growths within the breast tissue that can infiltrate nearby tissues and potentially metastasize to other body parts. In mammography image analysis, identifying and diagnosing malignant masses is crucial for early detection and intervention in breast cancer. Malignant masses can exhibit diverse characteristics in mammography images, including an irregular or spiky border, an irregular shape, or an uneven or non-uniform appearance. These masses may also display associated calcifications or regions of distortion within the surrounding breast tissue. Consequently, for the purposes of this investigation, mammographic images from Mendeley Data were utilized. The datasets employed for this research included the Mammographic Image Analysis Society database (MIAS) and the INbreast datasets. The MIAS database consists of digital mammograms widely used for research in mammography and breast cancer diagnosis. The INbreast dataset, on the other hand, is an openly accessible dataset utilized for the analysis of mammography images. The mammogram images from Mendeley Data underwent preprocessing using data augmentation and contrast-limited adaptive histogram equalization techniques. Subsequent to augmentation, the MIAS dataset contained 3816 images, while the INbreast dataset comprised 7632 images.

## 4. EXPERIMENTAL RESULTS AND DISCUSSION

In conducting this research, we employed the TensorFlow and Scikit-learn frameworks for data processing and in-depth analysis. The experimental setup involved utilizing an HP ProLiant DL380p Gen8 system configured with 20GB of RAM. This configuration was instrumental in executing the experiments aimed at evaluating the performance of the proposed hybrid model.

## 4.1 Experiment with MIAS Dataset

### Results

Two experiments were conducted using two distinct datasets of Mammography breast cancer images, namely the MIAS and the INbreast datasets. The initial experiment focused on the evaluation of the MIAS dataset, while the second experiment focused on the INbreast dataset. Figure 4 displays samples of the original and LBP images from the MIAS experiment, and further results obtained are presented in Table 1, which provides the classification report, and Table 2, which shows the overall accuracy and other relevant metrics. Additionally, Figure 5 depicts the confusion matrix, while Figure 6 illustrates the Receiver Operating Characteristic (ROC) curve. Figures 7 and 8 depict the training versus validation loss and the training versus validation accuracy, respectively.

Figure 2 displays the original breast cancer images alongside their corresponding Local Binary Pattern (LBP) images. Local Binary Pattern is a texture descriptor used for feature extraction in image analysis. In this context, the LBP images represent a transformed version of the original images, where texture patterns are highlighted to aid in the analysis and classification of breast cancer. This transformation allows for enhanced feature recognition, facilitating the identification of key characteristics for the

Figure 4. Showing the original breast cancer images and the equivalent LBP images

![](img/20813928ec98c7f6fbdbab0d52bde2f1_252_0.png)

Table 1. Classification report on MIAS dataset

| Class | Precision | Recall | F1-Score | Support |
|---|---|---|---|---|
| Benign Masses | 0.97 | 0.98 | 0.97 | 495 |
| Malignant Masses | 0.95 | 0.94 | 0.95 | 269 |
| Accuracy | | | 0.96 | 764 |
| macro avg | 0.96 | 0.96 | 0.96 | 764 |
| weighted avg | 0.96 | 0.96 | 0.96 | 764 |

classification and diagnosis of breast cancer. The comparison between the original and LBP images in Figure 2 provides valuable insights into the effectiveness of LBP in enhancing the discriminative features necessary for accurate classification and diagnosis in the context of breast cancer detection.

The results presented in Table 1 exhibit precision values of 0.97 for Benign Masses and 0.95 for Malignant Masses. Similarly, the recall values were 0.98 and 0.94 for Benign and Malignant Masses, respectively. These high precision and recall scores are indicative of the model's strong performance in classifying the two classes within the MIAS dataset. Moreover, the F1-scores for both classes were 0.97 and 0.95, demonstrating the model's robustness in capturing the balance between precision and recall.

The overall accuracy achieved was 0.96, underscoring the model's ability to effectively classify both Benign and Malignant Masses within the MIAS dataset.

The evaluation of the hybrid model on the MIAS dataset, as revealed in Table 2, shows an impressive set of performance metrics, showcasing the model's efficacy in accurately classifying both benign and malignant masses within breast cancer images. The metrics indicated the model's overall proficiency in capturing and categorizing various instances within the dataset.

The accuracy metric, which stood at 0.96, demonstrated that the hybrid model correctly classified approximately 96% of the images in the dataset. This high accuracy score emphasized the model's ability to make precise classifications, showcasing its reliability in real-world applications.

Table 2. Performance metrics evaluation

| Accuracy | Precision | Recall | F1-Score | Kappa | FNR | Sensitivity |
|---|---|---|---|---|---|---|
| 0.96 | 0.96 | 0.96 | 0.96 | 0.9105 | 0.0706 | 0.9526 |
