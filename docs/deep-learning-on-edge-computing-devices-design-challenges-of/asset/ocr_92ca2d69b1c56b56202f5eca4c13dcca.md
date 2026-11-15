![](bbox=[0.106, 0.102, 0.843, 0.328])

**Figure 7.7** The sparsely connected binary-weighted Deep Adaptive Network (DAN$_b$) learned from the MNIST dataset. A neural network classifier is connected to the Deep Adaptive Network for recognizing the label (0–9) of a given image.

threshold process, the weight matrices of the first-layer and the second-layer AdaRBMs become very sparse, and the nonzero weights tend to cluster into different groups.

We change the parameter \(\lambda\) from \(10^{-1}\) to \(10^{-8}\) to evaluate its relation to classification accuracy. Our experiment randomly selects 10000 images for training, and tests the DAN, the DBN, the DBN with L$_1$-norm weight-decay (DBN$_1$), and the DBN with L$_2$-norm weight-decay (DBN$_2$) over the rest images. The experiment is carried out ten times, and the average accuracies are shown in Fig. 7.8(a). It seems that the DAN, DBN, and DBN$_2$ have similar classification accuracy when \(\lambda\) is smaller than \(10^{-4}\); however, the DBN$_1$ has noticeably lower accuracy.

Since the parameter \(\lambda\) controls the sparsity of the weight parameters in a Deep Adaptive Network, it can affect the efficiency of hardware implementation. Fig. 7.8(b) shows the relation between the ratio of reserved weights \(\sigma\) and the value of \(\lambda\). A typical threshold value \(u = 0.1\) and \(\gamma = 0.5\) are set. Results show that the ratio of reserved weights drops significantly from about 50% to less than 5% when \(\lambda\) changes from \(10^{-8}\) to \(10^{-1}\). Experiment also shows that the second layer of the DAN is over 15% sparser than the first layer.

We performed a experiment to illustrate how the parameter \(\gamma\) controls the tradeoff between rowwise sparsity and columnwise sparsity of the weight matrix. The weights of the DAN$_t$ with different values of \(\gamma\) are examined. We compare the rowwise matrix norm \(\|\mathbf{W}\|_M\) and the columnwise