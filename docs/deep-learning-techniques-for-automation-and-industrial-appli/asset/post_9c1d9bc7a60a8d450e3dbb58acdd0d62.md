
![](img/0c56ac060cc6089fd33efc0e4aeb71a8_60_0.png)

Figure 3.6 Accuracy and loss graph: InceptionV3.

![](img/0c56ac060cc6089fd33efc0e4aeb71a8_60_1.png)

Figure 3.7 Accuracy and loss graph: VGG19.

## 3.4 Conclusion and Future Work

As we have witnessed, farmers in India are having a lot of problems with agricultural cultivation due to the country's growing population. In our study, we used the most widely grown crop leaves, such as mango and pomegranate, and we applied a convolutional neural network to determine whether or not each crop leaf had a disease. The technique of crop disease identification and classification was enhanced and suggested in this research, and tests were used to demonstrate the usefulness of the optimized model in identifying and categorizing plant diseases. Future work will attempt to provide preventive measures for each crop leaf disease, as this project has a lot of potential.

## References

- 1. Devaraj, A., Rathan, K., Jaahnavi, S., Indira, K., Identification of plant disease using image processing technique, in: 2019 International Conference on Communication and Signal Processing (ICCSP), IEEE, pp. 0749–0753, April 2019.
- 2. Chatterjee, J. M., Kumar, A., Rathore, P. S., & Jain, V. (Eds.), Internet of Things and Machine Learning in Agriculture: Technological Impacts and Challenges. Vol. 8, Walter de Gruyter GmbH & Co KG, 2021.
- 3. Saleem, M.H., Potgieter, J., Arif, K.M., Plant disease detection and classification by deep learning. Plants, 8, 11, 468, 2019.
- 4. Sun, G., Jia, X., Geng, T., Plant diseases recognition based on image processing technology. J. Electr. Comput. Eng., 2018, Article ID 6070129, 7, 2018, https://doi.org/10.1155/2018/6070129
- 5. Singh, V., Sharma, N., Singh, S., A review of imaging techniques for plant disease detection. Artif. Intell. Agric., 4, 229–242, 2020.
- 6. Singh, V. and Misra, A.K., Detection of plant leaf diseases using image segmentation and soft computing techniques. Inf. Process. Agric., 4, 2016.
- 7. Kumar, A., Chatterjee, J. M., Payal, M., Rathore, P. S., Revolutionizing the internet of things with swarm intelligence, in: System Assurances, pp. 403–436, Academic Press, 2022.
- 8. Al-Bashish, D., Braik, M., Bani-Ahmad, S., Detection and classification of leaf diseases using K-means-based segmentation and neural-networks-based classification. Inform. Technol. J., 10, 267–275, 2011.
- 9. Park, H., Eun, J.S., Kim, S.H., Image-based disease diagnosing and predicting of the crops through the deep learning mechanism, in: IEEE 2017 International Conference on Information and Communication Technology Convergence (ICTC), pp. 129–131, 2017.
- 10. Bhargava, N. et al., Texture recognition using Gabor filter for extracting feature vectors with the regression mining algorithm. Int. J. Risk Conting. Manage., 9, 3, 31–44, 2020.
- 11. Bhargava, N., Sharma, A. K., Kumar, A., Rathore, P. S., An adaptive method for edge preserving denoising. In 2017 2nd International Conference on Communication and Electronics Systems (ICCES), pp. 600–604, IEEE, 2017, October.
- 12. Shah, D., Trivedi, V., Sheth, V., Shah, A., Chauhan, U., ResTS: Residual deep interpretable architecture for plant disease detection. Inf. Process. Agric., 9, 2, 212–223, 2022.
- 13. Sasubilli, S.M., Kumar, A., Dutt, V., Improving health care by help of internet of things and big data analytics and cloud computing. *2020 International Conference on Advances in Computing and Communication Engineering (ICACCE)*, pp. 1–4, 2020.
- 14. Kotturu, P.K. and Kumar, A., Comparative study on machine learning models for early diagnosis of Alzheimer’s disease: Multi correlation method. *2020 5th International Conference on Communication and Electronics Systems (ICCES)*, pp. 778–783, 2020.
- 15. Vallabhajosyula, S., Sistla, V., Kolli, V.K.K., Transfer learning-based deep ensemble neural network for plant leaf disease detection. *J. Plant Dis. Prot.*, 129, 3, 545–558, 2022.
- 16. Sasubilli, S.M., Kumar, A., Dutt, V., Machine learning implementation on medical domain to identify disease insights using TMS. *2020 International Conference on Advances in Computing and Communication Engineering (ICACCE)*, pp. 1–4, 2020.
- 17. Sasubilli, S.M., Kumar, A., Dutt, V., Improving health care by help of internet of things and big data analytics and cloud computing. *2020 International Conference on Advances in Computing and Communication Engineering (ICACCE)*, pp. 1–4, 2020.

## 4.1 Introduction

Nowadays, satellite images provide us with an edge to explore the Earth’s surface in detail, and this is considerably important for earth observations. The number of satellites has increased in recent times, thereby enabling a drastic increase in the amount of available data. There are two types of satellites available: active and passive. Active satellites are those that modify the signal before transmitting it by using transponders and amplifiers [11]. Passive satellites are those that transmit the signal without any modification [12]. A satellite image has three types of resolution: spatial, spectral, and temporal. The increase in the availability of satellite data has attracted researchers to work in the satellite image domain. In recent years, the challenge of satellite picture categorization has increased quickly [2–4]. Numerous types of classification and other tasks are being carried out, such as forest-type classification and land use, land cover, and urban area development. Traditionally, classification was done using normal classifiers such as random forests and SVM with the help of machine learning algorithms. All these traditional approaches lack performance, and the results are not satisfactory. Hence, recently, deep learning-based approaches have been explored by various researchers to work on satellite images. The major advantage of using machine learning and deep learning is that they provide significant results with fewer data points and blurry images compared to the traditional approach [10]. The deep learning-based approach uses convolutional networks for feature extraction, which can be further used for classifying satellite images. A convolutional neural network (CNN) is a deep neural network that is suitable for image processing.

In this paper, we focused on satellite image classification using deep learning models and provided an experimental comparison of various deep learning models for the classification of satellite images. The goal of satellite image classification is to categorize satellite images into different semantic classes by looking at their layout and structural patterns. Deep learning-based algorithms extract information from images automatically and classify satellite images into various classes.

This paper focuses on the classification of satellite images into 21 different classes, namely agricultural, airplane, baseball diamond, overpass, parking lot, beach, dense residential, forest, motorway, golf course, harbor, intersection, buildings, chaparral, medium residential, mobile home park, river, runway, sparse residential, storage tanks and tennis court. The models used in the experimentation are VGG, ResNet, Inception, Xception, EfficientNet, MobileNet, and NasNet. The UC Merced dataset has been used for the evaluation of these algorithms [1–9].

## 4.2 Motivation and Contribution

Satellite data are rich in information. A single image consists of many information, such as geographical location (latitude and longitude) and their respective pixels. The machine learning models are good, but they lag behind in feature extraction, thus, resulting in poor performance. They do not give desirable results since satellite images contain much more information than ordinary images. Deep learning is more powerful than machine learning, but very few studies explore this kind of work in the satellite data field. Several models are present in deep learning models that can be used for satellite image classification, but picking the right model for the task is still a challenging problem. Therefore, in this paper, we compared different deep learning models applied to satellite data to determine which model performs best. We conducted a comparison of various deep learning models using the UC Merced dataset. A total of 30 models were trained, and this paper provides a detailed analysis to identify the best-performing models.

### 4.2.1 Related Work

In recent years, satellite images have become an emerging topic, and numerous algorithms have been proposed for the task, including the use of machine learning (ML) and data-driven approaches for satellite image classification. In recent past, it has been demonstrated that satellite images can be used to identify various objects on Earth. Various studies have been conducted on satellite images. A few of these are discussed below.

Mahmon et al. stated that classification depends on several factors, such as data, the number of classes, and the algorithm used [13, 14]. This article also examined several strategies for the categorization of satellite images with artificial neural networks (ANNs) based on the value of accuracy measurement. This study approached the best strategies to classify land use and land cover using several approaches to classification techniques, and the comparison of these techniques was also confirmed with the data. The final output, a land use/land cover (LU/LC) map of the research region, may be used for a number of fields, including deforestation, archaeology, weather forecasting, urban planning, development, and damage assessment.

Xia et al. [5] proposed a satellite image-based dataset for the classification of various objects. The dataset contained 10,000 images of different aerial scenes belonging to various classes, including airports, baseball fields, forests, meadows, parking lots, and more.
