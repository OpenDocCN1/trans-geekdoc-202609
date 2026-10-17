
**Table 4**

Working condition recognition accuracies of the 4S-TFSM-CNN with different numbers of DCs.

| Number of DCs | *l* = 2 | *l* = 4 | *l* = 6 | *l* = 8 | *l* = 10 |
|---|---:|---:|---:|---:|---:|
| Accuracy | 98.12% ± 0.81% | 98.48% ± 0.72% | 97.71% ± 0.89% | 98.07% ± 0.78% | 97.83% ± 0.91% |

![](img/63ea25f228d3f03c8fce71d94548c8eb_8_0.png)

**Fig. 7.** Training and test accuracies of the 4S-TFSM-CNN with 4 DCs.

**Table 5**

The accuracy of working condition recognition for different TFSMs with 4 DCs.

| Method | 1S-TFSM-CNN | 2S-TFSM-CNN | 4S-TFSM-CNN | 8S-TFSM-CNN |
|---|---:|---:|---:|---:|
| Accuracy | 95.65% ± 1.29% | 98.39% ± 0.76% | 98.48% ± 0.72% | 97.01% ± 1.04% |

4S-TFSM-CNN method. Moreover, the classification accuracies of RF, SVM, RNN, LSTM, GRU and CNN using 4S-TFS as input data outperformed those of image- and data-based classification results, which illustrates that the 4S-TFS feature extraction for a single DC contributes to the performance improvement of working condition recognition. In addition, the classification results of 4S-TFSM as input data when using SVM, RNN, LSTM and CNN as classifiers also outperformed those of the other three data as input, indicating that feature fusion of multiple DCs can reduce data heterogeneity and improve the working condition recognition accuracy of oil wells.

**Table 6**

The architectures for image-CNN, data-based-CNN and 4S-TFS-CNN.

| Layer | Type | Dropout | Image-CNN: Feature maps | Image-CNN: Filter size | Data-based-CNN: Feature maps | Data-based-CNN: Filter size | 4S-TFS-CNN: Feature maps | 4S-TFS-CNN: Filter size |
|---:|---|---:|---|---|---|---|---|---|
| 0 | Input | – | 64 × 64 × 1 | – | 2 × 200 × 1 | – | 4 × 23 × 1 | – |
| 1 | Conv 1 | – | 64 × 64 × 32 | 3 × 3 | 2 × 200 × 32 | 1 × 3 | 4 × 23 × 32 | 1 × 3 |
| 2 | Pool 1 | – | 32 × 32 × 32 | 2 × 2 | 2 × 100 × 32 | 1 × 2 | – | – |
| 3 | Conv 2 | – | 32 × 32 × 64 | 3 × 3 | 2 × 100 × 64 | 1 × 3 | 4 × 23 × 64 | 1 × 3 |
| 4 | Pool 2 | – | 16 × 16 × 64 | 2 × 2 | 2 × 50 × 64 | 1 × 2 | 4 × 12 × 64 | 1 × 2 |
| 5 | Conv 3 | – | 16 × 16 × 128 | 3 × 3 | 2 × 50 × 128 | 1 × 3 | 4 × 12 × 128 | 1 × 3 |
| 6 | Pool 3 | – | – | – | 2 × 25 × 128 | 1 × 2 | – | – |
| 7 | Conv 4 | – | 16 × 16 × 128 | 3 × 3 | 2 × 25 × 128 | 1 × 3 | 4 × 12 × 128 | 1 × 3 |
| 8 | Pool 4 | – | 8 × 8 × 128 | 2 × 2 | 2 × 13 × 128 | 1 × 2 | 4 × 6 × 128 | 1 × 2 |
| 9 | FC 1 | 0.1 | 1 × 1 × 1024 | – | 1 × 1 × 1024 | – | 1 × 1 × 1024 | – |
| 10 | FC 2 | 0.1 | 1 × 1 × 512 | – | 1 × 1 × 512 | – | 1 × 1 × 512 | – |
| 11 | FC 3 | 0.1 | 1 × 1 × 8 | – | 1 × 1 × 8 | – | 1 × 1 × 8 | – |

![](img/63ea25f228d3f03c8fce71d94548c8eb_8_1.png)

**Fig. 8.** Training and test accuracies of image-CNN, data-based-CNN and 4S-TFSM-CNN with different training steps.

Table 7
Working condition recognition accuracies based on different methods.

| Method | Image-CNN | Data-based-CNN | 4S-TFS-CNN | 4S-TFSM-CNN |
|---|---|---|---|---|
| Accuracy | 96.83% ± 1.08% | 97.39% ± 0.99% | 97.53% ± 0.91% | 98.48% ± 0.72% |

Table 8
CNN algorithm indicators.

| Method | Image-CNN | Data-based-CNN | 4S-TFS-CNN | 4S-TFSM-CNN |
|---|---|---|---|---|
| Feature map size | 64 × 64 × 1 | 2 × 200 × 1 | 4 × 23 × 1 | 23 × 23 × 4 |
| Param, MB | 10.21 | 4.12 | 3.78 | 6.03 |
| FLOPs, GB | 43.97 | 5.21 | 4.00 | 24.35 |
| Training time, min | 162.15 | 21.83 | 7.32 | 99.02 |

Table 9
Overall prediction accuracy of the methods.

| Feature | RF | k-NN | SVM | RNN | LSTM | GRU | CNN |
|---|---|---|---|---|---|---|---|
| Image | 92.59% | 96.89% | 93.79% | 87.40% | 95.17% | 94.59% | 96.83% |
| Data-based | 96.02% | 96.99% | 97.70% | 93.31% | 96.67% | 96.69% | 97.39% |
| 4S-TFS | 97.94% | 96.99% | 97.74% | 96.89% | 97.87% | 98.07% | 97.53% |
| 4S-TFSM | 96.57% | 96.02% | 97.90% | 97.27% | 98.00% | 97.57% | 98.48% |

What exactly is the reason for the difference in recognition accuracy? Which types of working conditions are more difficult to distinguish? We visualize the dataset to better understand the data structure. The t-distributed stochastic neighbor embedding (t-SNE) methodology is a recently developed dimensionality reduction method that is frequently used to visualize data. t-SNE can integrate high-dimensional data in two- or three-dimensional space, allowing related objects in the high-dimensional space to approach each other in the low-dimensional space (Zhao et al., 2017). Fig. 9 shows the scatter plot of the sample data after it has been embedded in two-dimensional space.

The data in categories 1 (SVL), 2 (NOC), and 6 (TVL) are depicted as reasonably independent clusters in Fig. 9, which means that these categories may be relatively easy to identify and classify. Other types of samples, become entangled and mixed together, making it impossible to distinguish between them. For example, category 0 (ILS) and category 3 (GIF) are almost indistinguishable in

![](img/63ea25f228d3f03c8fce71d94548c8eb_9_0.png)

Fig. 9. t-SNE embedding in 2D space.

the plot because their corresponding DCs are highly similar, while category 5 (UPB) is scattered throughout the plot.

Fig. 10 shows the confusion matrix derived on the test dataset using the four data processing approaches, image-CNN, data-based-CNN, 4S-TFS-CNN, and 4S-TFSM-CNN. We can clearly observe that the vast majority of samples lie on the diagonal. It is straightforward to observe from the diagonal of the four confusion matrices that category 0 (ILS), category 3 (GIF), category 4 (OPL), and category 5 (UPB) are the four most difficult categories to distinguish from each other, as these four working conditions have the lowest classification accuracies. This is consistent with the results of the t-SNE visualization discussed in Fig. 9. The recognition accuracy of 4S-TFSM-CNN is also higher than the remaining three schemes in the four most difficult to distinguish categories, indicating that the 4S-TFSM feature-extraction approach can weaken the heterogeneity of the data and significantly affect the diagnosis performance.

The heterogeneity induced by the varied distributions of data between distinct classes, as illustrated in Fig. 10, is an important factor limiting the recognition accuracy of our model. Here, instead of using individual datasets as direct inputs, we use a simple synthetic feature-extraction method, i.e., a feature-extraction technique that synthesizes multiple datasets.

The idea is to “synthesize” training samples from real samples that are more suitable for deep learning to complete the classification task by extracting time-frequency features from the feature space of original dataset for normalization and matrix operations. In addition, despite the high accuracy of 98.48%, we evaluate the incorrectly classified samples from a probabilistic perspective to assess the performance of the 4S-TFSM-CNN. We infer that some misclassifications, such as category 5 (UPB) in Fig. 10, are attributable to label ambiguity. For these samples, it may be difficult to identify clear fault types, even for human experts, or the samples might contain multiple fault types at the same time, thus introducing some label noise throughout the dataset.

In terms of training efficiency, CNNs may require more training time than typical machine learning methods (e.g., RF, k-NN and SVM) due to their processes of learning features. However, traditional machine learning methods are not friendly in the case of large quantities of data. Fortunately, once trained, the network can be recovered and utilized for model prediction multiple times, and the training time of our proposed 4S-TFSM-CNN technique is substantially faster than that of image-CNN. Therefore, the 4S-TFSM-CNN-based approach is efficient and feasible in real-world oil well working condition recognition.

![](img/63ea25f228d3f03c8fce71d94548c8eb_10_0.png)

**Fig. 10.** The confusion matrix for the prediction under different methods. The numbers on the diagonal line represent the probability of correctly categorized samples, while the numbers on the nondiagonal line represent the probability of incorrectly classified samples. For clarity, we retain three decimal places, and the misclassification probabilities below 0.005 are not shown on the confusion matrix.

Considering the computational complexity of neural networks, a 4-layer CNN is used in this paper, although the accuracy of working condition recognition may be higher as the number of neural network layers increases. The DC data are generated with time series, and in future work, we will also consider temporal convolutional networks (TCNs), which can use convolutional features while considering temporal information.

## 5. Conclusions

In this paper, a 4S-TFSM-based feature-extraction technique for oil well DCs is proposed, and a specifically designed CNN is employed to achieve oil well working condition recognition. The technique uses 4S-TFS to extract DC features, which can effectively improve the recognition accuracy of oil well conditions while reducing the computational cost. Subsequently, 4S-TFSM is constructed by relative normalization and matrix calculation to enhance the feature differences between various types of working conditions and suppress the data heterogeneity problem. Finally, a special CNN is designed to automatically select 4S-TFSM features that are sensitive to working condition categories to achieve high-accuracy identification of oil well working conditions. Experimental results with a large amount of real oil well data in a field demonstrate the effectiveness of the proposed method.

Considering the computational complexity of neural networks, a 4-layer CNN is used in this paper, although the accuracy of working condition recognition may be higher as the number of neural network layers increases. The DC data are generated with time series, and in future work, we will also consider temporal convolutional networks (TCNs), which can use convolutional features

## Declaration of interest

The authors declare that they have no known competing financial interests or personal relationships that could have appeared to influence the work reported in this paper.

## Acknowledgements

We would like to thank the associate editor and the reviewers for their constructive comments. This work was supported in part by the National Natural Science Foundation of China under Grant 62203234; in part by the State Key Laboratory of Robotics of China under Grant 2023-Z03; in part by the Natural Science Foundation of Liaoning Province under Grant 2023-BS-025; and in part by the Research Program of Liaoning Liaohe Laboratory under Grant LLL23ZZ-02-02.

## A. Appendix

### 1.1. Parameter setting of RF

We mainly consider the effects of n_estimators, min_samples_split, max_depth, max_features, and min_samples_leaf on the performance of RF classification, and use GridSearchCV to automate the search for the above parameters. The parameters are set as shown in Table A1.
