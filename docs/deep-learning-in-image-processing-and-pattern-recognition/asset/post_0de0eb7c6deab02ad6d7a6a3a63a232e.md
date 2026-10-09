
cluster centers cannot be known in advance. Therefore, in this paper, the idea of DPC algorithm is used for improving the K-means algorithm. According to the distribution of points in the constellation diagram, find the points with the highest density as cluster centers, thereby reducing the number of iterations of K-means clustering and improving the clustering effect.

KADPC is an auto clustering algorithm combined with K-means and DPC clustering algorithm, whose parameters are defined as follows:

- 1. Cutoff distance $d_{c}$: let the cutoff distance gradually increase from zero, and find the cutoff distance that makes the entropy $H$ reach the minimum

$$ H = - \sum_{i=1}^{n} (\sum_{j} (\delta_{i} \sum_{j} e^{- (\frac{d_{ij}}{d_{c}}) }^{2} ) \log ( \delta_{i} \sum_{j} e^{- (\frac{d_{ij}}{d_{c}}) }^{2} ) \quad (3) $$

$$ d_{ij} = ||x_{j} - x_{i}|| \quad (4) $$

- 2. Local density $p_{j}$: Define the local density of point $x_{j}$ in the constellation diagram with local density $p_{j}$ as:

$$ p_{j} = \sum_{j=1}^{k} \chi (d_{ij} - d_{c}) \quad (5) $$

$$ \chi (x) = \begin{cases} 1 & x < 0 \\ 0 & x \geq 0 \end{cases} \quad (6) $$

- 3. High local density point distance $\theta_{j}$:

$$ \theta_{j} = \min_{j: p_{j} > p_{i}} (d_{ij}) \quad (7) $$

where $d_{ij}$ is the distance between any two constellation point $x_{j}$ and $x_{i}$, $\chi(.)$ is the decision function. The specific steps of KADPC clustering algorithm are shown in Algorithm 2.

### Algorithm 2 KADPC clustering algorithm

INPUT: Sample set D = ($x_{1}, x_{2}, \dots, x_{m}$)

OUTPUT: Eigenvalues $T_{c}$

Step1: Obtain the truncation distance $d_{c}$ by increasing the truncation distance from zero to the distance that minimizes the entropy H.

Step2: According to the truncation distance $d_{c}$, the local density value of constellation points in the constellation diagram is calculated, and the distance between other constellation points and high local density constellation points is calculated.

Step3: Use the value of the calculated local density $p_{j}$ and the distance of high local density point $\theta_{j}$ to make a two-dimensional decision diagram to select the cluster center of the data sample, that is, select the point with the larger $p_{j}$ and $\theta_{j}$ as the cluster center.

Step4: Select K cluster centers and perform K-means clustering on the selected K cluster centers.

Step5: Calculate the sum of the Euclidean distances from the points in the K cluster to the centers of this cluster, find the average value of the sum of distances $\bar{S}_{k}$:

$$ \bar{S}_{k} = \frac{s_{1} + s_{2} + s_{3} + \dots + s_{k}}{k} $$

Step6: Normalize $\bar{S}_{k}$, and define unit Euclidean distance as the eigenvalue $T_{c}$.

In modulation recognition, the modulation method of the signal cannot be known, and the number of cluster centers cannot be determined. The number of cluster centers obtained by the existing modulation method is limited, and the number of cluster centers can be set multiple times. Classify and recognize the obtained set of feature values as the features of the signal, that is, the value of K can be set to 2, 4, 8, 16, 32, 64, and the corresponding feature values obtained are T2, T4, T8, T16, T32, T64.

## 2.3. Modulation Recognition Based on Multi-SVM

The basic SVM model is a linear classifier with the largest interval defined in the feature space. Since the use of the kernel function method overcomes the curse of dimensionality and the problem of non-linear separability, there is no increase in computational complexity when mapping to a high-dimensional space. The SVM classification algorithm was originally only used to solve two classification problem, and lacked the ability to deal with multi-classification problems. Due to the wide variety of modulation methods, in order to reduce the number of SVM classifiers, one-versus-rest (OVR) SVM is used in this paper. Take BPSK, 4PSK, 8PSK and 16PSK as classification targets to realize multi-classification, three SVM classifiers are used to form a multi-classifier as shown in Figure 2, for each classifier is composed of the eigenvalues of the same signal under different SNR.

![](img/e4200cc4308edaf8913e513b0f96dbb6_578_0.png)

Figure 2. The block diagram of multi-classifier system using SVM.

In the data training process, the training of each classifier is composed of the eigenvalues of the same signal under different SNRs, thus reducing the amount of parameter training, as shown in Equation (8).

$$ [T_{2(idb)}, T_{4(idb)}, T_{16(idb)}, T_{32(idb)}, T_{64(idb)}]_{j=-2,0,2,5,10} \quad (8) $$

## 3. Experimental Results and Analysis

In order to verify the feasibility of the algorithm, MATLAB is used in this paper to simulate Phase Shift Keying (PSK) and Quadrature Amplitude Modulation (QAM) signal to obtain BPSK, QPSK, 8PSK, 16QAM, 32QAM at different SNRs. Figure 3 are the constellation diagrams of the five signals at SNR = 6 dB. The symbol rate of each signal is 1200 B/s, the number of symbols is 4000, the carrier frequency is 4800 Hz and the sampling frequency is 16 × 4800 Hz. Gaussian white noise is added to simulate the transmission of all signals on the Gaussian channel.

In this paper, ADBSCAN is used to reduce noise to increase the rate of recognition. Because there are too many constellations generated, in order to more intuitively observe the results of noise reduction, the number of symbols sent by simulation is set to 100. Figure 4 shows that the points in the constellation diagram are divided into two clusters, which are represented by red and blue colors, and the remaining points are labeled as noise points, which will be deleted in the subsequent processing.

This paper selects several classical algorithms of machine learning and deep learning for comparison, including backward propagation (BP) neural network, fuzzy K-means (FK), random forest (RF), K-nearest neighbor (KNN) and SVM algorithm. Under each SNR, there are 21,000 training samples and 9045 test samples. The recognition rate of BPSK modulated signal under different methods is shown in Figure 5a. It can be seen that the overall recognition rate curve of KADPC algorithm model is better than other comparison algorithms. The recognition rate curve is stable and close to 100% when SNR = 2 dB. KADPC algorithm adds noise reduction and preprocessing. At the same time, under ideal conditions, BPSK signal has only two clustering centers. When KADPC algorithm is used for feature extraction, the difference of eigenvalues is obvious. Therefore, KADPC algorithm is significantly improved compared with other algorithms.

![](img/e4200cc4308edaf8913e513b0f96dbb6_579_0.png)

**Figure 3.** Signal Constellation Chart (SNR = 6 dB) (a) BPSK; (b) QPSK; (c) 8PSK; (d) 16QAM; (e) 32QAM.

![](img/e4200cc4308edaf8913e513b0f96dbb6_579_1.png)

**Figure 4.** The noise reduction visualization result of BPSK at SNR = 0 dB.

![](img/e4200cc4308edaf8913e513b0f96dbb6_579_2.png)

![](img/e4200cc4308edaf8913e513b0f96dbb6_580_0.png)

![](img/e4200cc4308edaf8913e513b0f96dbb6_580_1.png)

![](img/e4200cc4308edaf8913e513b0f96dbb6_580_2.png)

**Figure 5.** The Recognition rate of different signals. (a) BPSK; (b) QPSK; (c) 8PSK; (d) 16QAM; (e) 32QAM.

The simulation results of recognition accuracy of QPSK signal under different SNR are shown in Figure 5b. KADPC model is gradually stable and close to 100% when SNR = 4 dB, while the recognition rate of other algorithms is significantly lower than KADPC algorithm when SNR = 2 dB. Although it is close to that of FK when SNR = 4 dB, it is better than FK algorithm at low SNR. Under ideal conditions, the points in the constellation of QPSK signal are closely distributed around the four clustering centers. With the improvement of SNR, the number of clustering centers of FK is closer to the actual value, so the algorithm is improved significantly. However, the recognition rate of FK is lower than that of KADPC algorithm under low SNR, and the other comparison algorithms perform poorly on QPSK signal. The comprehensive results show that the recognition effect of the algorithm proposed in this chapter is better. The recognition accuracy of 32QAM signal at different SNR is shown in Figure 5e. It can be seen that the overall curve of KADPC algorithm has higher recognition rate than other algorithms under SNR = 2 dB, and the average recognition rate of the overall algorithm is higher. Because the FK algorithm does not specify the number of clustering centers and uses a fuzzy K value for clustering, the number of clustering centers is farther away from the real value with the increase of modulation order. Therefore, the recognition effect is very poor at low SNR.

The recognition accuracy of the five signals under different SNR is shown in Table 1. For BPSK signal, it can be seen from Table 1 that the highest recognition rate of KADPC
