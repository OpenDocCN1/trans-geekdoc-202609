
## 5.3.4.2 Transform

Discrete wavelet transform (DWT) is a signal processing technique that has been used in various applications, including image and signal processing, pattern recognition, and ML.

In recent years, DWT has been applied in the field of plant disease detection and classification. The basic idea behind using DWT for plant disease detection is the manifestation of patterns of variation in plant texture and color, which can be captured and analyzed using wavelet coefficients.

Discrete wavelet transform decomposes an image into different frequency bands, and the wavelet coefficients of each band represent the image information at that particular frequency scale. By analyzing the wavelet coefficients, it is possible to identify the texture and color patterns associated with particular plant diseases.

To use DWT for plant disease detection, the first step is to acquire high-resolution images of plants. These images can be acquired using various imaging techniques, such as digital cameras or hyperspectral imaging.

Once the images are acquired, they are preprocessed, and the model can be used to make predictions. The image is decomposed into different frequency bands using a wavelet basis function, and the wavelet coefficients of each band are calculated, as shown in Figure 5.3.

## 5.3.4.3 Classifier

Plant disease prediction using convolutional neural networks (CNNs) is a promising approach for accurately identifying and classifying diseases in plants. Convolutional neural networks are a type of deep learning algorithms that are particularly effective at processing and analyzing images, making them well-suited for identifying plant diseases based on visual symptoms, as shown in Figure 5.4.

To build a plant disease prediction model using CNNs, a dataset of images of healthy and diseased plants is required. These images are split into training, validation, and test sets.

- The CNN is trained on the training set using backpropagation, which involves adjusting the weights of the network to minimize the difference between the real and expected labels. The validation set is used to assess the model's performance during training, whereas the testing set is used to assess the overall accuracy of the model.
- The CNN model typically consists of several convolutional layers that classify the images into many disease groups by extracting characteristics from the input images and numerous fully connected layers. Data augmentation techniques, such as rotation, flipping, and cropping, can be used to enhance the model and increase the size of the training set.

Overall, predictions of plant diseases using CNNs have been encouraging and have the potential to significantly increase the effectiveness and precision of disease recognition and control in agriculture, as shown in Figure 5.5.

![](img/66ecdb8eb8654ae1c99705e55a45a836_114_0.png)

**FIGURE 5.3** DWT Transformed Image.

![](img/66ecdb8eb8654ae1c99705e55a45a836_114_1.png)

**FIGURE 5.4** CNN Algorithm.

*Source:* Khang (2021)

```
training started...Wait for 200 seconds...
training started...
Elapsed time is 2.033151 seconds.
Elapsed time is 2.239313 seconds.
...training finished.
testing started....
test error is
Elapsed time is 1.085832 seconds.
CNN Accuracy = 99.0909
CNN Precision = 0.9913
CNN Sensitivity = 0.99091
CNN Specificity = 0.99773
```

```
confmatrix =
```

| 22 | 1 | 0 | 0 | 0 |
| 0 | 21 | 0 | 0 | 0 |
| 0 | 0 | 22 | 0 | 0 |
| 0 | 0 | 0 | 22 | 0 |
| 0 | 0 | 0 | 0 | 22 |

FIGURE 5.5 CNN Accuracy Result.

## 5.3.5 IRRIGATION SYSTEM

Traditional agriculture is the cornerstone of global development. Despite this, because of the population’s exponential growth and increasing consumption, farmers need water to irrigate the land.

Because of the scarcity of this resource, farmers need a solution that changes the way they operate. To keep up with and meet demand, new technology has been implemented, giving rise to the concept of “Farm 4.0”.

The irrigation method suggested in this study is clever, adaptable, and low in cost and usage. This smart agriculture strategy is based on ML algorithms. To achieve this, we used a set of sensors (soil, humidity, temperature, and rain), which were placed in an environment that promoted better plant growth for months.

We then used the Node-RED platform and MongoDB to collect data based on the acquisition map from these sensors. Based on our data, we used a variety of models, including k-nearest neighbor (KNN), logistic regression, neural networks, SVM, and naive Bayes (Khang et al., 2022b).

In comparison with other models, the findings demonstrated that KNNs perform better, with a recognition rate of 98.3% and an RMSE of 0.12.

Finally, to provide better visualization and oversight of our surroundings, we offered a web application that combined various data produced by the sensors with forecasts from our model.

![](img/66ecdb8eb8654ae1c99705e55a45a836_117_0.png)

**FIGURE 5.6** Irrigation Model.

## 5.5 RECOMMENDATION

Future studies could employ ensemble ML on the entire training set to juxtapose results with a study based on feature selection (Rana et al., 2021).

In addition, the out-of-sample data sampling approach can be further used to evaluate the performance of the predictive models in comparison with the in-sample approach presented in this chapter.

## REFERENCES

Bharath S., Yeshwanth S., Yashas B. L., Vidyaranya R. J., “Comparative analysis of machine learning algorithms in the study of crop and crop yield prediction,” IJERTCONV8IS14008, NCETESFT – 2020 (Volume 8 – Issue 14). www.academia.edu/download/64341632/comparative-analysis-of-machine-IJERTCONV8IS14008.pdf

Khang A., (2021). “Material4Studies,” Material of Computer Science, Artificial Intelligence, Data Science, IoT, Blockchain, Cloud, Metaverse, Cybersecurity for Studies. www.researchgate.net/publication/370156102_Material4Studies

Khang A., Gupta S. K., Rani S., Karras D. A., (Eds.). (2023a). Smart Cities: IoT Technologies, Big Data Solutions, Cloud Platforms, and Cybersecurity Techniques. CRC Press. https://doi.org/10.1201/9781003376064

Khanh H. H., Khang A., (2021). "The role of artificial intelligence in blockchain applications," Reinventing Manufacturing and Business Processes through Artificial Intelligence, 2(20-40) (CRC Press). https://doi.org/10.1201/9781003145011-2

Konstantinos P. F., (2018). "Deep learning models for plant disease detection and diagnosis," Computers and Electronics in Agriculture, 145, 311-318. www.sciencedirect.com/science/article/pii/S0168169917311742

Liu J., Wang X., (2021). "Plant diseases and pests detection based on deep learning: A review," Plant Methods, 17, 22. https://doi.org/10.1186/s13007-021-00722-9.

Majji V. A., Kumaravelan G., (2021). "A review of machine learning approaches in plant leaf disease detection and classification," Third International Conference on Intelligent Communication Technologies and Virtual Mobile Networks (ICICV). https://ieeexplore.ieee.org/abstract/document/9388488/

Meriç Ç., Selami B., (2022). "Smart irrigation systems using machine learning and control theory," The Digital Agricultural Revolution: Innovations and Challenges in Agriculture through Technology Disruptions, Chapter 3. https://doi.org/10.1002/9781119823469

Niketa G., Owaiz P., (2016). "Rice crop yield prediction using artificial neural networks," IEEE Technological Innovations in ICT for Agriculture and Rural Development (TIAR). https://doi.org/10.1109/TIAR.2016.7801222.

Ramesh K., Rudra K., (2021). "Crop yield prediction using machine learning algorithm," 5th International Conference on Intelligent Computing and Control Systems (ICICCS). https://doi.org/10.1109/ICICCS51141.2021.9432236.

Rana G., Khang A., Sharma R., Goel A. K., Dubey A. K., (Eds.). (2021). Reinventing Manufacturing and Business Processes through Artificial Intelligence. CRC Press. https://doi.org/10.1201/9781003145011

Rani S., Bhambri P., Kataria A., Khang A., (Dec 30, 2022). "Smart city ecosystem: Concept, sustainability, design principles and technologies," In AI-Centric Smart City Ecosystems: Technologies, Design and Implementation, Vol. 1, No. 20 (1st ed.). CRC Press. https://doi.org/10.1201/9781003252542-1

Saeed K., Lizhi W., (2019). "Crop yield prediction using deep neural networks," Original Research Article, Frontiers in Plant Science. www.frontiersin.org/articles/10.3389/fpls.2019.00621/full

Sandeep K., Arpit J., Anand Prakash S., Satyendr S., et al., "A comparative analysis of machine learning algorithms for detection of organic and nonorganic cotton diseases," Mathematical Problems in Engineering, 2021, Article ID 1790171. https://doi.org/10.1155/2021/1790171

Shruthi U., Nagaveni V., Raghavendra B. K., (2019). "A review on machine learning classification techniques for plant disease detection," 5th International Conference on Advanced Computing & Communication Systems (ICACCS). https://ieeexplore.ieee.org/abstract/document/8728415/

Tace Y., Tabaa M., Elfilali S., Leghris C., Bensag Hassna B., Renault E., (2022). "Smart irrigation system based on IoT and machine learning," Energy Reports, 8(Suppl. 9), 1025-036. www.sciencedirect.com/science/article/pii/S2352484722013543

Vallejo-Gómez D., Marisol O., Hincapié C., (2023). "Smart irrigation systems in agriculture: A systematic review," Special Issue Proposal Application, 13(2), 342. https://doi.org/10.3390/agronomy1302034225

Van Klompenburg T., Kassahun A., Catal C., (2020). "Crop yield prediction using machine learning: A systematic literature review," Computers and Electronics in Agriculture, 177, 105709. www.sciencedirect.com/science/article/pii/S0168169920302301
