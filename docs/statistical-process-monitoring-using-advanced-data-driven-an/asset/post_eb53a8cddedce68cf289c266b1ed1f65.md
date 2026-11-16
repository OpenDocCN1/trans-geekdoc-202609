
![](img/aa2f42c739937b682075082233e335bb_225_0.png)

FIGURE 6.14 Illustration of DBM structure with two stacked RBMs.

this case is expressed as

```
\( E(\mathbf{v}, \mathbf{h}_1, \mathbf{h}_2; \theta) = -\mathbf{v}^T \mathbf{W}_1 \mathbf{h}_1 - \mathbf{h}_1^T \mathbf{W}_2 \mathbf{h}_2, \quad (6.32) \)
```

where \(\theta = \{\mathbf{W}_1, \mathbf{W}_2\}\) refers to the model parameters, the vector of visible units \(\mathbf{v} \in \{0, 1\}^D\) and the vectors of hidden units \(\mathbf{h}_1, \mathbf{h}_2 \in \{0, 1\}^P\). For the sake of simplicity, the bias parameters are omitted below. The joint probability is defined as

```
\( P(\mathbf{v}; \theta) = \frac{1}{Z(\theta)} \sum_{\mathbf{h}_1} \sum_{\mathbf{h}_2} \exp(-E(\mathbf{v}, \mathbf{h}_1, \mathbf{h}_2; \theta)). \quad (6.33) \)
```

In the general case of DBM with one visible layer and \(L\) hidden layers, the joint probability is expressed as:

```
\( P(\mathbf{v}, \theta) = \frac{1}{Z(\theta)} \sum_{\mathbf{h}_1} \dots \sum_{\mathbf{h}_L} \exp(-E(\mathbf{v}, \mathbf{h}_1, \dots, \mathbf{h}_L, \theta)), \quad (6.34) \)
```

where \(\theta = \{\mathbf{W}_1, \dots, \mathbf{W}_L\}\) refers to the parameters of the DBM model and the energy function is given by

```
\( E(\mathbf{v}, \mathbf{h}_1, \dots, \mathbf{h}_L, \theta) = -\mathbf{v}^T \mathbf{W}_1 \mathbf{h}_1 - \sum_{l=2}^{L} \mathbf{h}_{l-1}^T \mathbf{W}_l \mathbf{h}_l. \quad (6.35) \)
```

In [72], a greedy layer-by-layer pretraining algorithm for the DBM was considered by making each successive pair of layers in the DBM as an RBM.

### 6.4.4.1 Deep stacked autoencoder

A stacked autoencoder (SAE) model is an unsupervised deep-learning method composed of several layers, each of which is an autoencoder (Fig. 6.15). The output of each layer is the input of the next layer. The encoding process is performed by encoding every layer in a forwarding order, and the decoding process is done in the reverse order. The SAE model is trained based on a layer-by-layer greedy training procedure. This means that the first autoencoder is trained using the input data and produces the learned feature vector. The extracted features are fed to the next layer; this process is repeated until the training is completed. SAE models have been frequently used in different applications, including gearbox fault diagnosis [52], image denoising [55,56], and obstacle detection in autonomous vehicle [14].

![](img/aa2f42c739937b682075082233e335bb_226_0.png)

FIGURE 6.15 Diagrammatic illustration of a stacked autoencoder.

## 6.5 Deep learning-based clustering schemes for process monitoring

As mentioned above, anomaly detection in high-dimensional data based on binary clustering procedures is challenging and time-consuming. For instance, OCSVM with a selected kernel function could encounter challenges to learn from complex datasets, whereas it can get robust decision hyperplanes when applied to reduced and well-structured features. To overcome this problem, here we present a hybrid framework by combining the advantages of deep learning models and unsupervised clustering procedures (Fig. 6.16). In this hybrid approach, an unsupervised deep learning model, such as DBN, DBM, and SAE, will be used to extract relevant features from complex and high-dimensional datasets. The considered deep learning model will be trained in such a way that the used clustering algorithm (e.g., OCSVM) can efficiently discriminate normal data from anomalies based on the learned feature space.

Anomaly detection using hybrid methods can be done in two steps. The deep learning models are constructed through unlabeled training datasets that are devoid of anomalies. Then, the extracted features from the last layer of the considered deep learning model are passed to the used clustering or one-class machine learning algorithm for training purposes. In the testing step, the learned model is used to extract features from new arrival unlabeled data, and the clustering approach is applied to extracted features to separate between normal and anomalies data points.

Several hybrid methods have been developed to benefit from the complementary advantages of deep learning models and unsupervised binary clustering procedures. The method in [90] uses the DBN model and the OCSVM to detect anomalies in an actual wastewater treatment plant. It exhibits good detection performance in comparison to other hybrid methods including DBN-based KNN and k-means algorithms. Also, in [91], several hybrid models including DBNs-based, DSA-based and RBM-based clustering methods (i.e., k-means, BIRCH, and expectation maximization) have been compared when applied to abnormal ozone measurements. The results in [91] showed that hybrid models achieved better results in comparison to the stand-alone binary clustering algorithms. Also, it has been shown that the DBN-OCSVM outperformed the other hybrid models. Here, the DBN is constructed as a dimensionality-reduction procedure to generate a lower-dimensional set of features. The computed features are used as input to train the OCSVM. Subsequently, the established hybrid DBN-OCSVM is used for testing. Such methods are assumption-free and do not require any data labeling or assumption related to the distribution underlying the datasets. A hybrid anomaly detection algorithm merging DBM and AE models is employed for obstacle detection in road environments based on stereovision [13]. The extracted features from this hybrid model are used by OCSVM for anomaly detection. This model merges the greedy learning features of DBM with the AE's dimensionality reduction capability. Results indicate that anomaly detection performance based on hybrid models is improved compared to the stand-alone models. In summary, coupling the extraction features capacity of deep learning models with the sensitivity to changes of the binary clustering methods is advantageous since it bypasses the complexity issues of clustering methods in particular when applied to large-scale datasets.

## 6.6 Discussion

This chapter reviewed the basic features of commonly used clustering algorithms and one-class algorithms (i.e., OCSVM and SVDD). Then, some of deep learning approaches that effectively analyze and model high-dimensional data, such as DBN, RBM and DSA, were presented. To bypass the shortcoming of binary clustering methods when applied to high-dimensional data, we briefly presented hybrid methods that combine the benefits of deep learning models with the clustering approaches to reveal faults in monitored processes. Essentially, extracting relevant and compact information from large datasets using deep learning models improves the detection and discrimination capacity of binary clustering methods.

Note that the above discussed deep learning models have been created using a single scale (i.e., time scale) as they relate process variables only at the scale of the sampling interval. This single-scale feature extraction is suitable for the data including contributions at one scale only. However, data from engineering and environmental processes are multiscale in nature. This is mainly because events can occur with different localization in time and frequency, and process variables can be gathered at different sampling rates or include missing values. Wavelet-based multiresolution is a powerful tool for the multiscale representation of data. Thus, in the future, an interesting research direction would be to develop multiscale deep-learning models and use them to further improve anomaly detection in complex processes.

## References

- [1] D. M. Tax, R.P. Duin, Support vector data description, Machine Learning 54 (1) (2004) 45–66.
- [2] D. Wang, D.S. Yeung, E.C. Tsang, Structured one-class classification, IEEE Transactions on Systems, Man and Cybernetics. Part B, Cybernetics 36 (6) (2006) 1283–1295.
- [3] B. Schölkopf, A.J. Smola, F. Bach, et al., Learning with Kernels: Support Vector Machines, Regularization, Optimization, and Beyond, MIT Press, 2002.
- [4] S. Erfani, M. Baktashmotlagh, S. Rajasegarar, S. Karunasekera, C. Leckie, R1SVM: a randomised nonlinear approach to large-scale anomaly detection, in: Twenty-Ninth AAAI Conference on Artificial Intelligence, 2015, pp. 432–438.
- [5] F.J. Huang, Y. LeCun, Large-scale learning with SVM and convolutional for generic object categorization, in: 2006 IEEE Computer Society Conference on Computer Vision and Pattern Recognition (CVPR'06), vol. 1, IEEE, 2006, pp. 284–291.
- [6] D. Liu, H. Qian, G. Dai, Z. Zhang, An iterative SVM approach to feature selection and classification in high-dimensional datasets, Pattern Recognition 46 (9) (2013) 2531–2537.
- [7] S. Vempati, A. Vedaldi, A. Zisserman, C. Jawahar, Generalized RBF feature maps for efficient detection, in: BMVC, 2010, pp. 1–11.
- [8] Y. Bengio, Y. LeCun, et al., Scaling learning algorithms towards AI, in: Large-Scale Kernel Machines, vol. 34(5), 2007, pp. 1–41.
- [9] Y. Bengio, et al., Learning deep architectures for AI, Foundations and Trends® in Machine Learning 2 (1) (2009) 1–127.
- [10] B. Schölkopf, A. Smola, K.-R. Müller, Nonlinear component analysis as a kernel eigenvalue problem, Neural Computation 10 (5) (1998) 1299–1319.
- [11] S.T. Roweis, L.K. Saul, Nonlinear dimensionality reduction by locally linear embedding, Science 290 (5500) (2000) 2323–2326.
- [12] J. Donahue, Y. Jia, O. Vinyals, J. Hoffman, N. Zhang, E. Tzeng, T. Darrell, DECAF: a deep convolutional activation feature for generic visual recognition, in: International Conference on Machine Learning, 2014, pp. 647–655.
- [13] A. Dairi, F. Harrou, M. Senouci, Y. Sun, Unsupervised obstacle detection in driving environments using deep-learning-based stereovision, Robotics and Autonomous Systems 100 (2018) 287–301.
