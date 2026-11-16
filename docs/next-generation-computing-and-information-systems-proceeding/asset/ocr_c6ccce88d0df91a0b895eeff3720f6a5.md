monotonic character. When the value of X is greater, on the other hand, the process trend is milder. As a result, the weight value is calculated using the ln X function. The calculation method of the second weight is obtained through the definition of the adequate sample size, and the (Tufail et al. 2021) has its specific inference process. The formula for calculating this weight is:

\(c_i = \frac{1 - \Omega}{1 - \Omega^{n_i}}\) (3)

Among them, bi is the weight value of the i-th type of samples, ni is the number of samples of the i-th type of samples, and set \(\Omega = 0.99\) according to the parameters of the (Ahmad et al. 2022). The formula for applying this weight to the loss function is:

\(M_2 = b \left( -ln \frac{exp(A_j)}{\sum_{i=1}^O exp(A_i)} \right)\) (4)

Formula (2) is used to compute the weight by dividing the number of samples of each kind by the total number of pieces. A weight that makes the model more stable. Both systems of weighing have merits and cons. As a result, the two weights a and b are blended linearly. The following is the enhanced cross-entropy loss function:

# 3.2 Using ResNet50 as a feature extraction network

Wang et al. demonstrated the feasibility of neural network application in X-ray chest disease detection and proposed the COVID-Net network. The network model adds a depth wise convolution layer (depth wise convolution, DWConv) to the ordinary neural network model.
Next, this paper conducts experiments on the accuracy of the models of COVID-Net and ResNext50, respectively, detecting X-ray chest images and classifying images into three categories as the target in the literature accuracy, as shown in Figure 1. ResNext50 can have a similar performance to COVID-Net while reducing the network's number of parameters and computation. To sum up, ResNext50 is chosen as the feature extraction network for this model.

![](bbox=[0.22, 0.585, 0.79, 0.765])

Figure 1. Comparative accuracy of network under same task.

# 3.3 CLAHE algorithm for X-ray image preprocessing

The CLAHE algorithm, also known as contrast limited adaptive histogram equalization (contrast limited adaptive histogram equalization) (Gupta and Awasthi 2009), uses this method to process X-ray images, highlighting the image's internal details and suppressing