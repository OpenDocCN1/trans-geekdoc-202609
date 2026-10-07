
## 34 Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

![](img/f29bba55de4872c43f26af4667e705f2_44_0.png)

![](img/f29bba55de4872c43f26af4667e705f2_44_1.png)

FIGURE 2.5 Studies on denoising coding and dropout.

when the dropout rate was more than 0.3. This indicated that dropout can improve the performance of the DNN, but too much dropout may lead to loss of some important neurons for feature representation. Based on results shown in Figure 2.5, it can be concluded that the SAE-based DNN approach presented in this study can realize the induction motor fault diagnosis and have a good classification accuracy of about 96% at least.

## Autoencoders for Intelligent Fault Diagnosis ■35

![](img/f29bba55de4872c43f26af4667e705f2_45_0.png)

FIGURE 2.6 Comparison of two methods.

To verify the performance of the presented approach that combines the sparse coding with denoising coding in the AE to learn features for the DNN and utilizes the “dropout” technique to overcome overfitting during the training process, a comparison study was then carried out, where traditional SAE was used as the baseline. The classification performance under different labeled training data sets were investigated, where the size of training data changed from 80 to 400 with a step size of 80. The results are shown in [Figure 2.6].

It be seen that the presented approach has shown better performance than the SAE alone. In the performance improvement achieved by the proposed approach for a small training data size is more significant than the one for a large training size, which verifies the robustness of the proposed approach. It may be that corruptions of input samples can be regarded as expanding data sets artificially. Furthermore, dropout can improve the performance of the DNN by preventing complex co-adaptations between the hidden neurons, especially for small training data size.

Comprehensive comparison results of the classification performance are shown in [Table 2.3]. It can be observed that the proposed SAE-based DNN framework achieves the best performance in all scenarios.

For the three neural network models without SAE, the best is one network with two layers. This observation can be explained by the fact that the increased number of layers contributes to the learning capability of the neural network. However, NN(600–100) still performs worse than the proposed approach with one layer. This verifies the effectiveness of the SAE. The robust feature learned by the SAE can contribute to performance improvement of the following DNN.

Then, the proposed approach is also compared with two classifiers built on the top of the SAE. Different from the proposed approach, SVM and LR cannot fine-tune the features learned by the SAE. This difference may explain their incomparable performance.

## Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

TABLE 2.3 Comprehensive Comparison of Classification Accuracy
| Classifier | Health | BRB | BRM | RMAM | SSTM | UBM | Average |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| NN(100) | 78.00 | 92.50 | 70.40 | 81.70 | 87.40 | 70.25 | 80.04 |
| NN(600) | 74.00 | 97.50 | 73.50 | 71.00 | 95.00 | 35.00 | 74.33 |
| NN(600-100) | 88.78 | 99.56 | 100.00 | 99.94 | 92.72 | 97.33 | 96.39 |
| SVM | 92.50 | 96.50 | 100.00 | 100.00 | 91.00 | 96.50 | 96.42 |
| LR | 83.50 | 94.00 | 100.00 | 100.00 | 81.50 | 97.50 | 92.75 |
| DNN | 92.68 | 99.91 | 100.00 | 100.00 | 93.30 | 95.55 | 97.61 |

It can be seen in Table 2.3 that both SVM and LR classifiers can classify the features learned by the SAE well into the corresponding fault categories and classification accuracy for either of them much higher than the neural network with one hidden layer. The result consists with the fact that the SAE can learn effective features for the fault diagnosis.

In practice, the quality of the vibration data measured from the induction motor will be affected by environmental factors. Thus it is necessary to perform stability analysis of the SAE-based DNN for dealing with data disturbance. Partial corruption at different levels to the data was added into the input of both the neural networks and the SAE-based DNN, and their influence on the classification accuracy is shown in Figure 2.7. When the degree of the data corruption increased from 0% to 40%, even though the performance of the SAE-based DNN decreases, the overall classification accuracy is still greater than 90%. In comparison, the performance of the neural networks decreases significantly, i.e., from 96.58% to 76.58% for the neural network with two layers, and from 73.33% to 52.25% for the neural network with one hidden layer, reflecting that the SAE-based DNN possesses good stability against disturbance for induction motor fault diagnosis. To demonstrate that the proposed approach is to learn effective and discriminative representations for vibration signals, the raw features, the features learned by the SAE and the features fine-tuned by the DNN are all visualized via a technique

![](img/f29bba55de4872c43f26af4667e705f2_46_0.png)

FIGURE 2.7 Histogram of classification accuracy with "noise" in input data.

![](img/f29bba55de4872c43f26af4667e705f2_47_0.png)

FIGURE 2.8 Feature maps.

t-SNE (Van Der Maaten, 2014), which is an effective visualization technique for high-dimensional data. Here, principal component analysis (PCA) is used to reduce the dimensionality of the feature data to 50. This can speed up the computation of pairwise distances between data points and suppresses some noise without distorting the interpoint distances. Then the dimensionality reduction technique t-SNE is used to convert the 50-dimensional representation to 2-dimensional map and the resulting maps as scatterplot have been shown in Figure 2.8 (a)–c), respectively. It can be seen that the SAE fine-tuned by the DNN cluster points of different conditions are separated well. It presents the good separability of the features extracted by the SAE-based DNN in this study. The results also indicate that SSTM is the most similar with the features of Health. This is also reflected in classification accuracy in Table 2.3. From the trend of the three maps (from Figure 2.8(a)-(c)), it can be observed that the SAE itself is an effective feature learning for induction motor vibration signals and the SAE-based DNN approach that fine-tunes the features learned by the SAE can improve the learned representations of the SAE. It also verifies the superior classification performance of the SAE-based DNN compared to other baseline methods. Therefore, the SAE-based DNN is an effective approach for induction motor learning and fault diagnosis.

## CONCLUSION

In this chapter, an SAE-based DNN approach has been developed for induction motor fault diagnosis. This approach can learn features directly from raw data, which are discriminative over different working conditions of the induction motors. When the denoising coding is integrated with the SAE, it improves the robustness of the learned features and the stability of the DNN against disturbance. The dropout technique integrated into the network classifier reduces the overfitting in the training and improves the performance of the DNN for induction motor fault classification. Experimental study and a detailed analysis have verified the effectiveness of the SAE-based DNN for fault diagnosis.

## REFERENCES

- Ahmadizar, Farid, Khabat Soltanian, Fardin Akhlagagian, and Ioannis Tsoulis 2015. “Artificial Neural Network Development by Means of a Novel Combination of Evolutionary and Genetic Algorithm." Engineering of Artificial Intelligence 17 (2): 105–133 (March): 1–13. https://doi.org/10.1016/j.engappai.2014.11003.
- Alexandra, Monica. 2014. “Analysis of Induction Motor Fault Diagnosis With Fuzzy Neural Network." Applied Artificial Intelligence 17 (2): 50–33. https://doi.org/10.1080/71382702.
- Benouzaid, Mohamed El Chehemi 2000. “A Review of Induction Motor Signature Analysis as a Medium for Faults Diagnosis." IEEE Transactions on Industrial Electronics 47 (5): 984–993. https://doi.org/10.1109/41873206.
- Blödt, Martin, David Bonacci, Jeremi Regnier, Marie Chabert, and Jean Jaeger 2008. “On-Line Monitoring of Mechanical Faults in Variable-Speed Induction Motors Using the Wigner Distribution." IEEE Transactions on Industrial Electronics 55: 522–533. https://doi.org/10.1109/IE.2007.91941.
- Bordohi, D., J., and Rajiv Tiwari 2014. “Support Vector Machine Based Optimization of Multi-Fault Classification with Evolutionary Algorithms from Time-Frequency Vibration Data." Measurement 55 (September): 1–14. https://doi.org/10.1016/j.measurement.2014.04.024.
- Boureaux, Y-Ian, Francois Bach, Yann LeCun, and Jean Ponce 2010. “Learning Mid-Level Features for Recognition." 2010 IEEE Conference on Computer Vision and Pattern Recognition. https://doi.org/10.1109/CVpr.2010.5399663.
- Cao, le, Wen-Bing Huang, and Chun-Sun 2016. “Building Feature Space of Extreme Learning Machine With Sparse Denoising Stacked-Autoencoder." Neurocomputing 174 (January): 60–71. https://doi.org/10.1016/j.neucom.2015.02.096.
