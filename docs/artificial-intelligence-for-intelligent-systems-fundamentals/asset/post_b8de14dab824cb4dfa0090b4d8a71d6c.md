
# A step toward the detection of alzheimer's disease 263

## 13.3 METHODOLOGY

We integrated the probability forecast or numerical prediction of four machine learning models, combining them or utilizing the most common observation between models to arrive at a final prediction. A model ensemble is created by fitting four models, making predictions using each of them, and merging the results. It uses the test data performance to produce an ideal weighted average of the models, which is referred to as an ensemble. We fit an ensemble model by simply adding algorithms to the existing models.

### 13.3.1 Dataset

The dataset is separated into two files: training and testing, each of which contains approximately 5,000 photos, each of which is classified according to the severity of Alzheimer's illness. The training and testing dataset consists of four classes that indicate four stages of AD, as depicted in Table 13.1.

### 13.3.2 Ensemble method

Assembling is a term that is frequently seen in machine learning. This method serves as the foundation for a variety of algorithms. To name a few of the most well-known, random forests utilize a technique where a variable number of decision trees are integrated into one operation. An ensemble can be thought of as a learning strategy in which numerous models are combined in instruction to solve a problem of interest. Because an ensemble tends to perform better than a single individual, this is complete to recover simplification ability. The variety of ways in which an ensemble can be performed knows no bounds. The same can be said for the number of models evaluated as well the sorts of models analyzed. Keep in mind that choosing components with low bias and high variance is a good habit to develop. This is achieved by simply selecting models with a diverse structure and format. We demonstrate how the ensemble process is used in the neural network area. For greater clarity, we demonstrate alternative approaches to efficiently combining DL architectures. A good example is the image classification domain, where it is typical to encounter models with extremely deep learning capabilities. The same thinking and approach can be pragmatic to a variety of other applications with relative ease. Figure 13.1 highlights the complete overview of the ensemble method used for this.

Table 13.1 Dataset description

| AD Stages | Training | Testing |
|---|---|---|
| Mild Dement | 717 | 179 |
| Moderate Dement | 52 | 12 |
| Non-dement | 2,560 | 640 |
| Very Mild Dement | 1,792 | 448 |

264 Artificial intelligence for intelligent systems

![](img/8c7c0992f9872f35977e949607bd4072_294_0.png)

Figure 13.1 Proposed ensemble model's graphic representation.

There are three network classifiers as illustrated in the above diagram, each of which is integrated into a different method at the top of the hierarchy. This example demonstrates how to operate an ensemble of three distinct classifiers. They are pretrained models that have been trained on a dataset, which we will employ in our task. We can achieve better results with transfer learning precisely because it allows us to initialize our new train in the correct direction by modifying the information we have already acquired. This is feasible by fine-tuning the operation based on our facts. Specifically, we are operating in the ensemble mode, and we are fine-tuning our three ensemble components as we are merging them. In all the approaches discussed, we run the ensemble using the base models VGG19, ResNet-50, and DenseNet-121. We fine-tune, allowing them to retrain on their respective last convolutional blocks of our operation. The ensemble is only capable of operating in two dimensions. We make the transition from 3D to 2D operation global pooling. Dense layers with fixed dimensions are used to equalize dimensionalities across all the networks that are sending the pooling outputs through them.

## 13.4 RESULTS AND DISCUSSION

The proposed diagnosis model was in comparison to an ensemble model that was tuned to fit 3D brain MRI data, and the results were inconclusive. The results showed that the proposed AD diagnosis model was a successful method of diagnosis, including accuracy, precision, recall, and F1-score, among other things, and found them to be useful. The dataset for magnetic resonance resonances 6,400 data samples. We partitioned the dataset into two parts: a training dataset and a test dataset, with an 80%:20% split between the two portions. It was decided to create a validation dataset using data from the training dataset, which accounted for around 20% of the entire dataset. The training with a mini-batch size of 64 was used as part of the optimization process.

A step toward the detection of alzheimer's disease 265

![](img/8c7c0992f9872f35977e949607bd4072_295_0.png)

Figure 13.2 Training and validation loss and accuracy.

We used three different basic models. ResNet-50, DenseNet-121, and VGG19 are the three networks. Using the stacking approach, we put all these models together in one place. We ran the main model, as well as its majority voting and stacking-based ensemble, in parallel. The precision of the proposed model is 96%, which is 95%, the F-score is 94%, and the total accuracy of the model is 90.15% [Note: OCR likely contains a typo for VGG19, but keeping VGG119/VGG19 context]. While the model's performance for the categorization of non-demented individuals is adequate, it has much scope to improve when it comes to diagnosing demented individuals. It is feasible that training the proposed model on a dataset that contains a greater number of demented patients will aid in overcoming this limitation of the dataset. As evidenced by great results in the classification of different stages of AD when compared to existing baseline models, the proposed model offers hope in the fight against AD. Figure 13.2 shows the graphical representation of training and validation accuracy along with training and validation loss.

## 13.5 CONCLUSION

AD is a progressive neurological brain illness that develops from birth. When AD is detected early, it can assist in avoiding further damage to the brain tissues and aid in the administration of appropriate treatment. A combination of algorithms is used to obtain higher prediction accuracy than any of the algorithms used individually in the ensemble learning process. Because of the increasing popularity of in-depth learning technologies, researchers have begun combining various technologies for a variety of different applications. In this study, we suggested a technique based on profound learning as a method for integrating algorithms for the categorization of AD, which was later refined and published. We put up three different models. ResNet-50, DenseNet-121, and VGG19 are models that have not previously been employed as part of an ensemble model. When merging various basic learning models for final MRI image classification, the usefulness of the ensemble approaches, as majority voting and stacking, is investigated for their efficiency. Regard correction rates for Alzheimer's detection, the ensemble classifier produces the best results, with the precision of the proposed model being 96%, recall being 95%, F-score being 94%, and overall accuracy of the model being 90.15%. The results also show that the ensemble classifier outperforms the single learning model by a margin, suggesting that the proposed approach is both effective and efficient. In the future, we plan to incorporate multimodalities into the ensemble model, as well as improve the overall performance of the model.

## REFERENCES

- [1] J. E. Galvin et al., “Early stages of Alzheimer’s disease: Evolving the care team for optimal patient management,” Frontiers in Neurology, vol. 11, p. 59232, 2021.
- [2] J. Rasmussen and H. Langerman, “Alzheimer’s disease-why we need early diagnosis,” Degenerative and Neuromuscular, pp. 123–130, 2019.
- [3] H. Chen, Y. He, J. Ji, and Y. Shi, “A machine learning method for identifying gene pairs in Alzheimer’s disease,” Frontiers in Neurology, vol. 10, p. 1162, 2019.
- [4] P. H. Nguyen et al., “Amyloid oligos: A joint experimental/computational perspective on Alzheimer’s disease, Parkinson’s disease, type II diabetes, and atrophy lateral,” Chemical Reviews, vol. 121, no. 4, pp. 2545–2647, 2021.
- [5] P. Palimkar, R. N. Shaw, and Ghosh, “Machine learning technique to predict diabetes disease: Random forest classifier,” in Advanced Computing and Intelligent Technologies: Proceedings of ICACIT 2021, 2022: Springer,
- [6] W. Huang et al., “Railway dangerous goods transportation system risk identification: Comparisons between SVM, PSO-SVM, GA-SVM and GS-SVM,” Soft Soft, vol. 109, p. 107541, 2021.
- [7] A. Mosavi, F. Sajedi Hosseini, B. Choubin, M. Goodarzi, A. Dineva, and E. Rafiei Sardooi, “Ensemble boosting and bagging machine learning models for groundwater potential prediction,” Water Resources Management, vol. 35, pp. 23–37, 2021.
- [8] N. Yamanakkanavar, Y. Choi, and B. Lee, “MRI segmentation and classification of human brain using deep learning for diagnosis of Alzheimer’s disease: A survey,” Sensors, vol. 20, no. 11, p. 3243, 2020.
- [9] G. Zhang, Y. Liu, and X. Jin, “A survey of autoencoder-based recommender systems,” Frontiers of Computer Science, vol. 1, pp. 430–450, 2020.
- [10] Q. Dong et al., “Modeling hierarchical brain networks via volumetric sparse belief network,” IEEE Transactions on Biomedical Engineering, vol. 67, no. 6, pp. 1739–1748, 2019.
