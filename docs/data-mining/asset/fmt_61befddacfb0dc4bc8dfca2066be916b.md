
[Appendix D.1](#FigD1_687-703_B9780443158889000248.xhtml#s0010) gives equations for implementing backpropagation in matrix-vector form. For readers unfamiliar with manipulating functions that have matrix arguments, and their derivatives, [Appendix A.1](#TableA1_617-636_B9780443158889000212.xhtml#s0010) summarizes some useful background.

## 10.1 Deep Feedforward Networks

While neural networks have been considered standard ML techniques for decades, four key developments have played a crucial role in their resurgence:

* Proper evaluation of ML methods;
* Vastly increased amounts of data;
* Deeper and larger network architectures;
* Accelerated training using GPU techniques.

With regard to the first point, evaluation, it has been standard practice in the past for different groups to compare results using the same data sets. However, even when the data was public results were often difficult to compare because researchers used different protocols for their experiments, such as different testing and training splits. Moreover, significant time was spent reimplementing other methods, which often led to weak baselines. The rise of ML challenges with large common test sets ensures that results are more directly comparable, and it motivates teams to spend their time and energy on their own method. As the volume of evaluation data increases, deeper, more complex, and flexible models become feasible. The use of high-capacity models, which require extra care to prevent overfitting, makes it even more important to ensure that test sets are reserved for final tests only. For these and other reasons, some competitive challenges have been organized in which the labels for test data are hidden and results must be submitted to a remote server for evaluation. In some cases the test data itself is also hidden, in which case participants must submit executable code.

### The MNIST Evaluation

To underscore the importance of large benchmark evaluations, consider the Mixed National Institute of Standards and Technology (MNIST) database of handwritten digits. It contains 60,000 training and 10,000 test instances of hand-written digits, encoded as 28 × 28-pixel grayscale images. The data is a remix of an earlier National Institute of Standards and Technology (NIST) data set in which adults generated the training data and high school students generated the test set. [Table 10.1](#Ch011_391-432_B978044315888900011X.xhtml#t0010) gives some results on this data. Note that the LeNet convolutional network (row 5), a deep architecture discussed in [Section 10.3](#Ch011_391-432_B978044315888900011X.xhtml#s0120), outperformed many standard ML techniques, even in 1998.

Table 10.1
Summary of Performance on the MNIST Evaluation

| Classifier | Test Error Rate (%) | References |
| --- | --- | --- |
| Linear classifier (1-layer neural net) | 12.0 | LeCun et al. (1998) |
| --- | --- | --- |
| K-nearest-neighbors, Euclidean (L2) | 5.0 | LeCun et al. (1998) |
| 2-Layer neural net, 300 hidden units, mean square error | 4.7 | LeCun et al. (1998) |
| Support vector machine, Gaussian kernel | 1.4 | MNIST Website |
| Convolutional net, LeNet-5 (no distortions) | 0.95 | LeCun et al. (1998) |
| Methods using distortions |  |  |
| Virtual support vector machine, deg-9 polynomial, (2-pixel jittered and deskewing) | 0.56 | [DeCoste and Scholkopf (2002)](#References_705-736_B978044315888900025X.xhtml#fur125) |
| Convolutional neural net (elastic distortions) | 0.4 | [Simard, Steinkraus, and Platt (2003)](#References_705-736_B978044315888900025X.xhtml#fur494) |
| 6-Layer feedforward neural net (on GPU) (elastic distortions) | 0.35 | [Ciresan, Meier, Gambardella, and Schmidhuber (2010)](#References_705-736_B978044315888900025X.xhtml#fur101) |
| Large/deep convolutional neural net (elastic distortions) | 0.35 | [Ciresan, Meier, Masci, Maria Gambardella, and Schmidhuber (2011)](#References_705-736_B978044315888900025X.xhtml#fur102) |
| Committee of 35 convolutional networks (elastic distortions) | 0.23 | [Ciresan, Meier, and Schmidhuber (2012)](#References_705-736_B978044315888900025X.xhtml#fur103) |

![Image](images/T00011Xtabt0010.png)

Credit: Christopher J. Pal

The lower half of the table shows the results of methods that augment the training set with synthetic distortions of the input images. The use of transformations to further extend the size of an already large data set is an important technique in deep learning. Large networks, with more parameters, have high representational capacity. Plausible synthetic distortion of the data multiplies the amount of data available, preventing overfitting and helping the network to generalize. Of course, other methods such as support vector machines can also scale up model complexity with additional data. Simply adding more support vectors can allow support vector model (SVM)-based methods to outperform classical network architectures. However, as [Table 10.1](#Ch011_391-432_B978044315888900011X.xhtml#t0010) shows, training deep feedforward networks or CNNs with synthetic elastically transformed imagery yields even better results. Because of the large test set (relative to other datasets of that era) differences in the error rate of more than 0.01 are statistically significant.

The last four entries illustrate the effectiveness of deep networks. Interestingly, a standard multilayer perceptron with six layers using synthetic transformations and trained on a graphics processing unit matches the performance of a large and deep CNN. This shows that plain neural networks can be effective when they are deep and data augmentation is used because training such a network with synthetically transformed data encourages robustness with respect to plausible distortions. In contrast, CNNs embed translational invariances within the network design itself ([Section 10.3](#Ch011_391-432_B978044315888900011X.xhtml#s0120)). The best result in [Table 10.1](#Ch011_391-432_B978044315888900011X.xhtml#t0010) is based on an ensemble of convolutional networks. Ensembles are used to obtain the top performance in many settings ([Chapter 8](#Ch009_323-345_B9780443158889000091.xhtml#Ch009_323-345_B9780443158889000091), “Ensemble learning”). In recent years, ensemble learning has become somewhat less common due to the size and computational burden of training modern deep neural networks; nevertheless, it remains a useful technique, even in a deep learning context.

### Losses and Regularization

[Section 9.2](#Ch010_347-389_B9780443158889000108.xhtml#s0050) noted that different activation functions can be used for multilayer perceptrons. We distinguish the final-layer parameterization, from which the loss function is computed, from the intermediate-layer activation functions. In the past it was common practice to use sigmoids as output activation functions and base final-layer loss functions on squared errors—sometimes even when classification labels were constrained to be 0 or 1. Later designs, however, embrace the natural probabilistic encoding for any given data type by defining output activation functions as the negative log of the distribution functions used to make probabilistic predictions, whether these distributions are binary, categorical, or continuous. Then predictions can correspond precisely to the underlying probability models defined by Bernoulli—discrete or Gaussian distributions—as in linear and logistic regression but with greater flexibility.
