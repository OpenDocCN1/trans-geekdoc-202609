Both Algorithm 9.1 and Algorithm 9.2 use the theory of matrix group, which is convenient for extending the algorithm of the traditional vector space to the matrix group space. Using this idea, we can also construct additional algorithms of the matrix sample set. Moreover, from the aspects of time complexity and spatial complexity, there is no additional overhead.

# ### 9.1.4 Cases analysis

This section demonstrates simple applications of the two algorithms described in Section 9.1.2 through a few examples. In the first experiment, the KNN algorithm is applied to the classification of matrix samples. In the second experiment, the K-means algorithm is applied to the clustering problem of matrix samples.

# #### 9.1.4.1 KNN matrix sample classification

First, three types of matrix samples are generated manually, and each sample is a random sample under a two-dimensional Gaussian distribution. However, the mean of each Gaussian sample is different. Hence, the sample is a subset of the $M(1,2)$ matrix group. The mean values of the three samples are taken in two dimensions, $(0,0)$, $(2,2.5)$, and $(4,4)$, respectively, and the variances are all $q=1; 200$. Samples of each type are considered, of which 100 samples are used for training and the remaining 100 are used for testing. There are 600 matrix samples in total. The distribution of 300 training samples is shown in Figure 9.1.

Next, we perform Algorithm 9.1 for 300 test samples, where the parameter is $k = 5$ with the norm $\rho(A, B) = \|A - B\|_F, A, B \in M(1,2)$. The results of the test samples are shown in Figure 9.2. To observe the category of the test samples more clearly, the training samples are also shown in the figure.