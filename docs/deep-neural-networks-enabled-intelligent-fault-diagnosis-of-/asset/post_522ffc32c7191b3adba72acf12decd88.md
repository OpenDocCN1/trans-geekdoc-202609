
## 26 Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

fault diagnosis belongs to such a challenging problem since the system itself is a complex electromechanical one. There, some advanced signal processing technologies have been proposed for motor current or vibration signal analysis (Zari and Poshtan 2007; Blölt et al. 2008; Puche-Panadero et al. 2009) as to extract useful features for diagnosis. However, these state-of-the-art methods require the researchers to have a deep understanding of the induction motor and the fault signals. In addition, the required expert knowledge is not easily obtained that those methods are not intelligent enough to the machine learning. In contrast, a deep “autoencoder” (AE) network structure has been trained to learn low-dimensional codes from high-dimensional input vectors in unsupervised manner (Krizhevsky, Sutskeever, and Hinton 2012). Furthermore, sparse AE (SAE) (Ranzato et al. 2007; Wright et al. 2010; Boureau et al. 2010) have been widely studied to realize deep learning, as it is highly effective for finding succinct and high-level representations of complex data.

Inspired by the prior research, this chapter presents SAE-based deep neural network (DNN) approach for induction motor fault diagnosis. The rest of this chapter is organized as AE and its variants, the details of experiments performed on a machine fault simulator and the corresponding results, and some conclusions drawn from this study.

## AUTOENCODER AND ITS VARIANTS

This section is providing systematic introduction for AE, sparse AE, and denoising AE.

### Autoencoder

An AE is a symmetrical neural network that can learn the features in an unsupervised manner by minimizing reconstruction errors (Shin et al. 2013). The basic structure of AE is shown in Figure 2.1, where it tries to learn an approximation in the hidden layer so that the input data can be perfectly reconstructed at the output layer. However, the intrinsic problems of AE, as such simply copying input layer to hidden layer, make ineffective in extracting meaningful features even though its output can be a perfect recovery of input data.

![](img/f29bba55de4872c43f26af4667e705f2_36_0.png)

FIGURE 2.1 The structure of an autoencoder neural network.

### Autoencoders for Intelligent Fault Diagnosis

### Sparse Autoencoder

SAE, an extension of the AE, can learn relatively sparse features by introducing a sparse penalty term inspired by the sparse coding (Olshausen and Field 1996) into the AE. It can improve the performance of traditional AE and exhibits more practical values.

From the measured vibration, an $N \times M$ data set can be constructed as $X=\{x(1),x(2),...,x(i),...,x(N)\}, x(i)\in R^M$, where $N$ is the number of data samples for each working condition and $M$ is the length of each data sample. This data set is used as the input matrix of the SAE. A three-layer neural network similar to that in Figure 2.1 can be constructed, where the sigmoid function is chosen as activation function to the network. For the unlabeled input matrix $X$, the goal is to learn and obtain a feature expression $h(x(i),W,b)=\sigma(Wx(i)+b),j=1,...,N$ at the hidden layer so that the output $\sigma(W^Th(x),W,b)+c$ is close to or reconstructing the input. In the meantime, the sparse penalty term is added to the objective function of the AE so that the learned features actually works on the hidden layer to control the number of "active" neurons. In practice, the sparse penalty term is of constraint rather than simply repeating input. The sparse penalty if the output of a neuron is close to 1, the neuron is considered to be "active", otherwise it is considered "inactive". It is better to keep the neurons of the hidden layer "inactive" most of time. Suppose $a_j(X)$ denotes the activation of hidden unit $j$. In the forward propagation process, for a given input $X$, the activation of the hidden layer can be denoted as $a=sigmoid(Wx+b)$, where $W$ denotes the weights between the input layer and the hidden layer and $b$ denotes the biases. Then the average activation of the hidden unit $j$ can be given as

$$\rho_j = \frac{1}{n}\sum_{i=1}^n[a_j(x(i))] \quad (2.1)$$

In this process, the average activation of each hidden neuron $\rho_j$ is expected to be close to zero, namely the neurons of the hidden layer "inactive". To achieve this, the sparse term is added to the objective function that penalizes $\rho_j$ if it deviates from $\rho$. The penalty term is expressed as

$$P_{penalty} = \sum_{j=1}^{S_2}KL(\rho|\rho_j) \quad (2.2)$$

Where $S_2$ is the number of neurons in hidden layer. $KL(\cdot)$ is the Kullback-Leibler divergence (KL divergence) (Kullback and Leibler 1951), which can be written as:

$$KL(\rho|\rho_j)=\rho\log\frac{\rho}{\rho_j}+(1-\rho)\log\frac{1-\rho}{1-\rho_j} \quad (2.3)$$

This penalty function possesses the property that $KL(\rho|\rho_j)=0$ if $\rho=\rho_j$. Otherwise, increases monotonically as $\rho_j$ diverges from $\rho$, which acts as sparsity constraint.

## 28 Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

The cost function of the neural network is defined as:

$$C(W,b) = \sum_{i=1}^{n} \left[ \frac{1}{2} |h_{w,b}(x(i)) - y(i)|^2 \right] + \frac{\gamma}{2} \sum_{j=1}^{m_j} (W_j(i))^2 \quad (2.4)$$

Adding the penalty penalty to the cost, it can be modified as:

$$C_{sparse}(W,b) = C(W,b) + \beta \sum_{j=1}^{S_2}KL(\rho_j) \quad (2.5)$$

where $\beta$ is the weight of sparsity penalty. During coding, the optimal parameters of $W$ and $b$ need to be identified. Since the sparse cost function shown in Eq. (2.5) is directly related to parameters $W$ and $b$, it can be solved by minimizing $C_{sparse}(W,b)$ to obtain these two parameters. This can be realized using the backpropagation algorithm (Rumelhart, Hinton, and Williams 1986), where the stochastic gradient descent approach is used for training and the parameters $W$ and $b$ in each iteration can be updated:

$$W_j(l) = W_j(l) - \varepsilon \frac{\partial}{\partial W_j(l)} C_{sparse}(W,b) \quad (2.6)$$

$$b_l(l) = b_l(l) - \varepsilon \frac{\partial}{\partial b_l(l)} C_{sparse}(W,b) \quad (2.7)$$

where $\varepsilon$ is the learning rate. A forward pass on all training examples is used to compute the average activation $\rho_j$ to get the sparse error, then the backpropagation algorithm works to update the parameters. After that, the effective feature representations can be learned by the SAE.

### Denoising Autoencoder

Vincent et al. (2008) proposed a denoising AE learning algorithm based on the idea of making the feature representation robust by adding partial corruption to the input pattern, which can be used to train stacked AEs to initialize the deep architectures. It has been known that this type of learning can help obtain better feature representation with denoising, which motivates the introduction of denoising module into our study.

For the input matrix $X$, the process of denoising AE is in Figure 2.2, where the input $X$ is corrupted to get a partially destroyed $\chi$ by applying a stochastic mapping $\chi = X - qD(\chi|X)$, then $\chi$ is coded to $y$. Here distribution $qD$ describes as follows for each input, a fixed number of components are randomly chosen and their values are set to 0, while the others are kept unchanged. A joint denoising is defined as:

$$q^X(X, \chi, y) = q^X(X)qD(\chi|X)\delta_{f_0(X)}(y) \quad (2.8)$$

where $\delta_{f_0(X)}(y)$ is set to 0 if $f_0(X) \neq y$. $q^X(X)$ denotes the empirical distribution associated with N training. Thus, $y$ is a deterministic function of $\chi$. Let $\theta$ be one parameter of the joint distribution $q^\theta(X, \chi, y)$, it can be considered as a link parameter between $\chi$ and $y$. To obtain a reconstructed version (denoted as $X'$) of the input matrix $X$, by an objective function can be set as:

$$\min_{\theta} \arg_{\theta} q^{\theta}(X,X)[L(X,X')] \quad (2.9)$$

$L(X, X')$ is the reconstruction error. The reconstructed matrix $X'$ can be obtained by minimizing function (2.9) using a stochastic descent approach.

![](img/f29bba55de4872c43f26af4667e705f2_39_0.png)

FIGURE 2.2 Structure of denoising autoencoder.

## SAE-BASED INTELLIGENT FAULT DIAGNOSIS

Dropout

Dropout is a technique that can help reduce "overfitting" when training a neural network with limited training data set (Hinton et al. 2012). Generally, when the known training data set is small, the problem of overfitting which leads to a poor performance
