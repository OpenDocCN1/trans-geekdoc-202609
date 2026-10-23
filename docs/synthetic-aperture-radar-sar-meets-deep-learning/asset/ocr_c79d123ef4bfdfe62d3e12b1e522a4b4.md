where g is activation function, b is bias, m is the feature cube connected to the current feature cube in the previous layer and W is the (r, s) th value of the kernel connected to the m th feature cube in the previous layer. Moreover, R and S are the length and width of the convolution kernel size, respectively.

# 2.3.2. Multi-Scale Block

In RS imagery with meter and sub-meter-level spatial resolution, there are many objects in different sizes. In addition, there are large structures and details in the texture of the objects and ground scenes that need to be extracted. Since small-scale features, like short building edges, typically respond to smaller-sized convolutional filters, but large-scale structures respond better to larger convolutional filters, we use the multi-scale convolutional block. The multi-scale convolutional block extracts helpful dynamic features and improves feature extraction. Using this multi-scale convolutional block, the network can continuously learn a set of features and the related scales at which these features occur with a minimum increase in parameters.

According to Figure 3, in the n th layer of the multi-scale block, three sizes of convolutional filters are set: 1 × 1, 3 × 3 and 5 × 5. With a 1 × 1 convolutional kernel, features are extracted from pixels themselves. A 3 × 3 convolutional kernel extracts features from a small neighborhood. Additionally, a 5 × 5 convolutional kernel extracts features of a larger range, which is suitable for some continuous large-scale images. In the traditional multi-scale approach, the number of filters is the same for each kernel size, N and the output feature maps have a 3N spectral dimension. Therefore, large kernel size (i.e., 3 × 3 and 5 × 5) require more processing time and have high parameters. Therefore, it is better to change the number of filters for each kernel size in the multi-scale block. To achieve this, this research develops an adaptive formula for determining the number of filters (NoFs) in a multi-scale block. To keep a constant total number of filters in each block and to preserve a large increase in the number of parameters, we consider the number of filters that have smaller length and width dimensions more than filters with larger length and width. According to Equation (4), NoFs is the total number of filters of a multi-scale block and is divided into NoF1, NoF2 and NoF3, which are the number of filters for 1 × 1, 3 × 3 and 5 × 5 kernels, respectively:

$$\begin{cases} NoF_1 = \alpha \times NoF \\ NoF_2 = \beta \times NoF \\ NoF_3 = \gamma \times NoF \\ s.t.: \alpha + \beta + \gamma = 1 \end{cases}\tag{4}$$

where α, β, γ are coefficients that determine the number of filters for 1 × 1, 3 × 3 and 5 × 5 kernels, respectively. To reduce the network parameters, we consider these coefficients in such a way that α > β > γ.

![](bbox=[0.22, 0.75, 0.78, 0.92])

Figure 3. A multi-scale shallow block.

# 2.3.3. Residual Block

CNNs with deeper layers can generally model more complex patterns and have higher nonlinearity. Visual representation of feature maps shows that a deeper network can lead