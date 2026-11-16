
| STEP | DESCRIPTION | USE CASE EXAMPLE |
| :--- | :--- | :--- |
| Calculate the covariance matrix. | The first step is to use PCA to calculate the covariance matrix of data. This matrix tells you how correlated the different variables are. If two variables are highly correlated, they will have a high value for covariance value, and if they are negatively correlated, they will show a negative covariance value. | For a dataset with variables like age, income, and purchasing history, the covariance matrix will reflect how these variables correlate with each other. |
| Identify the principal components. | Next, you use the covariance matrix to identify the principal components in the data. These components are the linear combination of variables that capture the significant patterns in the data. The first principal component is the one that explains the most variance in the data, followed by the second. | In a customer dataset, the principal components might be combinations of variables that explain the most variability, such as a combination of age and income. |
| Retain the top N components. | After identifying all the principal components, you can choose to retain the top N components and discard the rest and thus reduce the number of dimensions. After doing the principal component analysis, you discover that the top three principal components account for 90 percent of the data variance, as shown in Figure 16.15. You can therefore retain those three dimensions instead of the ten or more you had. | If the top three principal components account for 90 percent of the data variance, these can be retained while the rest are discarded, simplifying the data from 10 dimensions to 3. |

![](img/1490b3cf638678afadc8c48abc1698d5_428_0.png)

FIGURE 16.15: Interpreting the PCA: The start of the bend indicates that three factors should be retained.

> NOTE A scree plot is a line plot of the eigenvalues of factors or principal components used in PCA to identify the significant factors.

Here are some use cases of the principal component analysis:

| USE CASE | DESCRIPTION |
| --- | --- |
| Dimensionality reduction | Used to reduce the dimensions in the data, thus helping to simplify complex datasets with numerous variables |
| Pattern analysis | Helps to reveal underlying patterns in the data by focusing on the principal components that explain the most variance |
| Dataset compression | Used to compress a dataset by retaining only the most informative dimensions, which can be beneficial for saving storage and improving computational efficiency |
| Noise reduction | Removes noise from a dataset by focusing on the components that explain the most variance and ignoring components associated with noise |
| Clustering | Useful in a clustering scenario where it can be used to visualize clusters in a lower-dimensional space after reducing the dimensionality of the data |

> **TIP** Use PCA for high-dimensional data to simplify the dataset and is beneficial for noise reduction, data compression, and improving cluster visualization.

## Feature Extraction and Dimensionality Reduction Using Singular Value Decomposition

Singular value decomposition (SVD) is a mathematical technique used in dimensionality reduction and feature extraction tasks. Its usage in unsupervised tasks depends on the algorithm in which it is included. SVD is a factorization method that breaks the matrix into three separate matrices: U, Σ, and V. Breaking it into its constituent parts, you can understand the matrix’s structure and properties intuitively.

Say you have a dataset of all the customer purchases in a grocery store. You want to conduct a customer insight analysis, but it is too complex to draw that insight. You can apply SVD to create three smaller components: a left singular matrix, a diagonal matrix, and a suitable singular matrix.

The left singular matrix represents the customer and their purchases, and the suitable singular matrix represents the purchases and the items bought. The diagonal matrix represents the strength between those relationships. Armed with this kind of data, you can identify the group of customers based on their purchases or identify which products are purchased together.

SVD can be used under the following conditions:

| USE CASE | DESCRIPTION |
| :--- | :--- |
| Large dimensionality | When you have large dimensionality in the data and you want to reduce the computational resources reducing the dimensions. |
| Identifying essential features | SVD can be used to identify the most essential features in a dataset. |
| Collaborative filtering | SVD can be used for product recommendations, such as collaborative filtering, to identify which products the users are likely to purchase based on their historical behavior. |
| Image and signal processing | In image and signal processing tasks, SVD can be employed to manipulate and analyze data effectively. This includes tasks like image compression, noise reduction, and signal enhancement. |

> **TIP** Utilize SVD for efficient dimension reduction and feature extraction in large datasets, making it useful for recommendation systems and image processing tasks.

## Using Autoencoders

An autoencoder is a type of artificial neural network that is primarily used in unsupervised learning and for dimensionality reduction. It solves many problems, such as facial recognition, feature detection, and anomaly detection, and it can generate meanings of words and in generative models to create new data that is like the input training data.

> NOTE Autoencoders are versatile tools that can be used for both supervised and unsupervised learning.

The autoencoder is focused on creating the most compact representation of the input data, effectively reducing the dimensionality of the data.

The autoencoder has an input layer that's connected to an encoder, which is a series of hidden layers that reduce the dimensionality of the input data. It contains two functions. It contains an encoding function that transforms the input data into a lower-dimensional latent space representation, also known as an _encoding_. Figure 16.16 shows how an autoencoder works.

![](img/1490b3cf638678afadc8c48abc1698d5_430_0.png)

FIGURE 16.16: Schema of a basic autoencoder

The encoded data is then passed to a _decoder_, which is a series of hidden layers. The decoder layer uses a decoder function that re-creates the input data from the encoded representation. The output layer is compared to the input layer and the error is used to train the autoencoder.

Autoencoders can be used for the use cases listed in Table 16.6.

## TABLE 16.6: Use Cases for Autoencoders

| USE CASE | DESCRIPTION | INDUSTRY | DATA TYPE | PREDICTIVE OUTPUT |
| :--- | :--- | :--- | :--- | :--- |
| Dimensionality reduction | Autoencoders learn lower-dimensional representations of high-dimensional data. It results in efficient storage and computation. | Data compression, image processing | Numerical data Categorical data Image data Audio data Video data | Lower-dimensional encoded representation Image compression Feature extraction |
| Feature extraction | Autoencoders can extract important features from input data learning meaningful representations for downstream tasks. | Natural language processing Computer vision | Text data Image data Sensor data | Salient features Embeddings Classification Clustering |
| Anomaly detection | Autoencoders reconstruct normal data and in the process identify outliers. | Network security Fraud detection | Numerical data Categorical data | Anomaly score Outlier detection |
| Data denoising | Autoencoders re-create clean data by removing unwanted variations. | Speech recognition Image denoising | Noisy data Numerical data Image data | Clean data Image denoising Audio restoration |
| Data generation | Autoencoders can generate new data. | Image generation Text generation | Image data Text | New data similar to input data |

> **TIP** Leverage autoencoders in unsupervised learning tasks for efficient dimensionality reduction, feature extraction, and anomaly detection.

## Using Hierarchical Clustering

Hierarchical clustering is a clustering algorithm used in unsupervised learning to group similar data points into clusters based on their similarities or differences. It offers several advantages, such as the ability to identify clusters at different scales, and it preserves the full hierarchy of the clustering solutions.

Hierarchical clustering is a bottoms-up approach where it treats each data point as a cluster and then groups them together to form clusters that form a hierarchical structure. It uses different linking techniques, such as single linkage, complete linkage, and average linkage.

Hierarchical clustering is used in various domains, including biology, social sciences, image analysis, market segmentation, customer segmentation, and so on. It can be used
