
## Code 8.3: Eigen Decomposition Verification

*Code 8.3* provides the steps to verify the Eigen decomposition of covariance (continuation from *Code 8.2*):

```
1. # Eigen Decomposition of covariance matrix
2. eigen_val, eigen_vect = np.linalg.eig(cov_mat)
3. mat_p = eigen_vect
4. mat_p_inv = np.linalg.inv(mat_p)
5. # Diagonal matrix
6. mat_d = np.array([
7.      [eigen_val[0],0,0,0],
8.      [0,eigen_val[1],0,0],
9.      [0,0,eigen_val[2],0],
10.     [0,0,0,eigen_val[3]]
11. ])
12. # Matrix will be equal to covariance matrix
13. mat_obtained = np.matmul(np.matmul(mat_p,mat_d),mat_p_inv)
```

**Code 8.3:** *Eigen decomposition of a symmetric square matrix*

The obtained eigenvalues and corresponding Eigen vectors for the Iris dataset would be as follows:

![](images/2243.jpg) ![](images/2244.jpg)

We can verify that these eigen vectors are unit in length and are orthogonal. These eigen vectors form the orthonormal basis for the linear transformation.

## Reducing with Principal Components

We can use all four eigen vectors for the linear transformation on the original data. However, the resulting vectors after transformation would still be in four dimensions. Instead, we can select the first two eigen vectors that captures top two maximum variations of the original data. Transformation matrix with the first two eigen vectors, also called *principal components*, would be as follows:

![](images/2245.jpg)

We can apply transformation on original data to obtain the transformed data in two dimensions, as shown in *Code 8.4* (continuation of *Code 8.3*):

```
1. # Select two principal components
2. eigen_vect0 = eigen_vect[:, 0]
3. eigen_vect1 = eigen_vect[:, 1]
4. trans_mat = np.array([eigen_vect0, eigen_vect1]).T
5. # Transform the data points
6. x_reduced = np.matmul(x, trans_mat)
```

**Code 8.4:** *Transforming the data to lower dimensions*

As the transformed data is in two dimensions, we can plot the points as shown in *[Figure 8.3](#c08.xhtml#fig8_3)*. With this, we have reduced the dimensionality of Iris dataset from four to two dimensions. From the figure, we can guess that simple linear separator algorithm would help us in classifying three species of Iris flow with good accuracy. Refer to the following figure:

![](images/Image45343.jpg)

**Figure 8.3:** *Plotting of PCA transformed data*

## Variance Retention

We can reduce the dimensions of the data by selecting a few principal components of data covariance matrix and performing linear transformation of original data with chosen orthonormal basis. A question would definitely arise in your mind about the number of principal components to choose. Each of the principal components retains certain variance of the original data. If all components are used, then all variance of the original data is retained. We can calculate the percentage of retention of the variance. Based on this percentage of variance retention, we can decide on the number of principal components.

Trace or sum of diagonal elements of the covariance matrix is equal to sum of its eigenvalues. The percentage retention of one eigen vector can be calculated using the following:

![](images/2246.jpg)

To calculate percentage retention of more than one Eigen vector, we must add its corresponding eigenvalues as follows:

![](images/2247.jpg)

On the Iris dataset, the first principal component would retain 92.5% of total variance. The first two principal components would retain 97.7% of total variance. Adding the third principal component would result in 99.5%. For the Iris dataset, we can comfortably reduce the dimensions from four to three by retaining 99.5% variance of the original data.

## When to Use PCA

AI algorithms assume that features are independent. If we want to make features independent, then PCA would be the right choice. With PCA, we will be able to reduce dimensions of the data as well if a few principal components are able to retain the variance we needed, which, of course, depends on the data.

In original data, each dimension represents a feature. These features convey meaning regarding the sample under consideration. However, when reduced through PCA, dimensions/features of the reduced data may not make sense to understand the sample. If you want to retain the meaning of each dimension, do not use PCA for dimensionality reduction.

## Autoencoder

*Autoencoders* are non-linear unsupervised dimensionality reduction technique that learns the compact representation of the original data using neural networks. Simple autoencoder model is depicted in *[Figure 8.4](#c08.xhtml#fig8_4)*. Dimensions of input and output layer would always be same. The objective of the autoencoder model is to produce the output vector just like as the corresponding input vector while the data passes through hidden layer where dimensions are reduced. In *[Figure 8.4](#c08.xhtml#fig8_4)*, input and output dimensions are four, and there are total of three hidden layers between them. *Encoded layer* also called *bottleneck*, is the lowest dimension layer in the entire network. In this case, we have encoded the layer’s dimension as two. Encoder model during training will learn compact representation of input data such that it is able to recreate the original data from the encoded data. Part of the encoder model that represents input data in compact representation through encoded layer is called *Encoder*. Part of the encoder model that creates original input data from the encoded data is called *Decoder*. Refer to the following figure:

![](images/Image45351.jpg)

**Figure 8.4:** *Simple Encoder Architecture*

There exists variation in the architecture. Regularized autoencoders such as sparse, denoising (creates corrupted copy of input by introducing noise) and contractive (encoded layer has lower dimensions as compared to input) are learning representation for classification tasks. Convolutional autoencoders uses convolution operation to learn convolution filters. Variational autoencoders finds its application in generative AI models. It assumes that data is generated by a model, and encoder is learning an approximation of posterior distribution. After training, sampling from the distribution, followed by decoding, will generate new data. In this section, we will implement simple sparse autoencoder for the Iris dataset.

## Iris Autoencoder

Let us build an autoencoder for the Iris dataset with encoded layer of two dimensions. As the Iris dataset contains four features, dimensions of input and output layer would be four. To keep it simple, let us have one hidden layer that will be the encoded layer. *Code 8.5* provides the steps to create TensorFlow autoencoder model:

```
1. from sklearn import datasets
2. from sklearn.model_selection import train_test_split
3. import tensorflow as tf
4. from tensorflow.keras import layers, losses
5. from tensorflow.keras.models import Model
6. from tensorflow.keras.initializers import RandomUniform
7.
8. class Autoencoder(Model):
9.     def __init__(self):
10.         super(Autoencoder, self).__init__()
11.         self.encoder = tf.keras.Sequential([
12.             layers.Dense(
13.                 units=2, activation='relu',
14.                 kernel_initializer=RandomUniform(minval=0., maxval=1.,
15.                     seed=10)),
16.         ])
17.         self.decoder = tf.keras.Sequential([
18.             layers.Dense(
19.                 units=4, activation='relu',
20.                 kernel_initializer=RandomUniform(minval=0., maxval=1.,
21.                     seed=10)),
22.         ])
23.     def call(self, x):
24.         encoded = self.encoder(x)
25.         decoded = self.decoder(encoded)
26.         return decoded
```

**Code 8.5:** *Simple autoencoder*
