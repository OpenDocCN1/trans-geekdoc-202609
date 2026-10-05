
# 36 | Scientific programming with Python

Hence, this operation to find the red spot is really a convolution over space and addition over channel (convadd). This operation is illustrated in Fig. 2.10. This operation has

![](img/2087e3fd78fc2bbc9ee0bfaab66e3bde_42_0.png)

**Fig. 2.10** illustration of 2-dimensional convolutions with adding of channels. In this example different $2 \times 2$ filters are applied over the color channel and the corresponding elements are multiplied and then added up. The filter is then moved by an amount of pixels specified by the stride until the image was covered.

become the workforce in computer vision with convolutional neural networks that we explore later in this book.

It is useful to mention that applications of convolutions are sometimes modified slightly to accommodate the preservation of the signal size. We have seen that the output of a convolution has a reduced size that depends on the size of the filter. Sometimes we want the output image to be the same size. We can achieve this by simply adding appropriate columns and rows to the input image. This is called padding, and padding with zeros is a common choice. Of course, this method can introduce some artifacts that might not be desirable.

Finally, it is interesting to note that edge detectors are an important part of computer vision systems. For example, we can apply to an image $2 \times 2$ filter with $1s$ on the left column and $-1s$ on the right column,

$$\begin{pmatrix} -1 & 1 \\ -1 & 1 \end{pmatrix}$$

For example, if we have an image with two color like:

$$\begin{pmatrix} 0 & 0 & 1 \\ 0 & 1 & 1 \\ 0 & 0 & 1 \\ 0 & 1 & 1 \end{pmatrix}$$

then the filtered image would be

$$\begin{pmatrix} 0 & 0 & 2 \\ 0 & 2 & 0 \\ 0 & 2 & 0 \end{pmatrix}$$

which highlights an horizontal edge. An example of applying this filter to the image on the left-hand image of Fig. 2.11 results in the right-hand image in the same figure.

![](img/2087e3fd78fc2bbc9ee0bfaab66e3bde_43_0.png)

**Fig. 2.11** An example of simple edge detector on the first component of JPG image.

Of course, our filter is very small and only shows edges with significant changes between two consecutive edges. There are therefore better designs of edge detectors, such as the Canny edge detector. These techniques combine some gradient filters with Gaussian smoothing and removal of some sparse cases. Also, a continuous version of edge filters is, for example, described by Gabor functions as the ones shown in Fig. 2.12a and b. A Gabor function is described by a sinusoidally-modulated Gaussian,

```
$f(u, v) = e^{-\frac{u^2+v^2}{2}} \cos(\frac{2\pi}{\lambda}u+\varphi)$
```

The example of a $64^2$ pixel filter with parameters $\gamma=0.5$, $\sigma=10$, $\lambda=32$, and $\varphi=\pi/2$ is shown in Fig. 2.12a. This filter can be rotated with a rotation matrix

```
$$\begin{pmatrix} x \\ y \end{pmatrix} \leftarrow \begin{pmatrix} \cos(\varphi) & \sin(\varphi) \\ -\sin(\varphi) & \cos(\varphi) \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix}$$
```

as shown in Fig. 2.12b for $\varphi=\pi$. Interestingly, these functions describe some of the neurons in the primary visual cortex of primates. Detecting edges seems therefore a good step to process images, a fact that we will encounter again in later discussion.

![](img/2087e3fd78fc2bbc9ee0bfaab66e3bde_43_1.png)

**Fig. 2.12** Example of Gabor functions for (a) vertical and (b) horizontal edge detection.

# 3 Machine learning with sklearn

The open-source series of libraries called scikit is built on the NumPy and SciPy libraries for more domain-specific support. In this chapter we briefly introducing the scikit-learn library, or sklearn for short. This library started as a Google Summer of Code project by David Courneau and developed into an open source library which now provides a variety of well-established machine learning algorithms. These algorithms together with excellent documentation are available at http://scikit-learn.org.

The goal of this chapter is to show how to apply machine learning algorithms in a general setting using some classic methods. In particular, we will show how to apply three important learning algorithms, a support vector classifier (SVC), a random forest classifier (RFC), and a multilayer perceptron (MLP). While many of the methods studied in this book go beyond these now classic methods, this does not mean that these methods are obsolete. The contrary; many applications have limited amounts of data where more data-hungry techniques as deep learning might not work. Also, the algorithms discussed are providing some form of baseline to discuss advanced methods like probabilistic reasoning and deep learning. Our aim is here to demonstrate that applying machine learning methods based on machine learning libraries is not very difficult. It also provides us with an opportunity to discuss evaluation techniques that are very important in practice.

![](img/2087e3fd78fc2bbc9ee0bfaab66e3bde_44_0.png)

Figure 3.1 illustration of sklearn components and a typical workflow for different data and machine learning goals.

Fundamentals of Machine Learning, Thomas P. Trappenberg, Oxford University Press (2020).
Oxford University Press, DOI: 10.1093/oso/9780199882804.001.0001

# Classification with support vector machines, random forests, and multilayer perceptrons 39

An outline of the algorithms and a typical work flow provided by scikit-learn, sklearn for short, is shown in Fig. 3.1. The machine learning methods are thereby divided into classification, regression, clustering, and dimensionality reduction. We will later discuss the algorithms, specifically in the second half of this chapter, though we start by treating the methods first as a blackbox. We specifically outline in this chapter a typical learning setting for classification. In some applications it is possible to achieve sufficient performance without much knowing exactly what these algorithms do, although we will later later that applying machine learning to more challenging requires some deeper understanding of the algorithms. Our aim for the later part of this book is therefore to look much deeper into the principles including probabilistic and deep learning.

# 3.1 Classification with support vector machines, random forests, and multilayer perceptrons

We will show how to apply three different types of machine learning classifiers using sklearn implementations, of a support vector classifier (SVC), a random forest classifier (RFC), and a multilayer perceptron (MLP). We therefore concentrate on the mechanisms and what is discussed about these classifiers using the classical example of the iris flowers that we discussed in the previous chapter to how to read data into NumPy arrays. We will start with the SVC, which is support vector machine. The sklearn implementation is actually a wrapper for the SVMLIB library from Chih-Chung Chang and Chih-Jen Lin that has been very popular for classification applications. In this chapter we describe more of the math and tricks behind this method, but for now we use it to demonstrate the mechanics of applying this method.

To apply this machine learning technique of a classifier to the data-set in the program Irisificationssklearn.ipynb. The program starts as usual importing the necessary libraries. We import the data similar to the program discussed in the previous chapter. We choose to split the data into a training set and a test set by using every second data point as training point and every other as a test point. This is accomplished with the index specifications 0:-1 which is a list that starts at "0", iterates until the end specified by "1" and uses a step of "2". Since the data are ordered and well balanced in the original data file, this will leave us also on a balanced dataset. Balance here means that we have the same, or nearly the same, number data in the training set for each class. It turns out that this is often important for the good performance of the models. Also, instead of using the names features and target, we decided to shorten the notation by denoting the input features as x and the targets as y.

¹SVM was the original name as it originated for classification problems. Later, the techniques were generalized to support vector regression, and we here follow the abbreviation used in sklearn.
