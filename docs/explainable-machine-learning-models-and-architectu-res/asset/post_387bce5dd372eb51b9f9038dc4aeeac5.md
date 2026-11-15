

![](img/d2107fc60629942e7da5355e47fcc33d_24_0.png)

Figure 1.6 Principal component analysis [11].

function.

Regression analysis predicts a continuous target variable, while classification predicts a label from a finite set. Multiple regression model with linear input variables is:

z = B_0 + B_1x_1 + B_2x_2 + ..... + e (1.1)

supervised learning algorithms include linear regression [11]. We train the model on labelled data (training data) and use it to predict labels on unlabeled data (testing data).

Figure 1.7 shows how the model (red line) fits training data (blue points) with known labels (z axis) as accurately as possible by minimizing a loss function. We can use the model to predict unknown labels (x value, z value).

### 1.1.8 Logistic Regression

Like Naive Bayes, logistic regression [12] extracts a set of weighted features from the input, logs them, and adds them linearly. It is a discriminative classifier, while Naive Bayes is generative.

Bayes is generative. The logistic regression diagram in Figure 1.7 predicts event probability by fitting data to a logistic function. It uses several numerical or categorical predictor variables.

![](img/d2107fc60629942e7da5355e47fcc33d_25_0.png)

Figure 1.7 Visual representation of the logistic function [14].

Its hypothesis is defined as,

$A_b(y)=d(b^T y)$

Where d is sigmoid function defined as,

$d(z)=\frac{1}{1+e^{-z}}$

In machine learning, we use a built-in function called fmin bfgs2 to find the minimum of this cost function given a fixed dataset. Parameters are initial values of parameters to be optimized and a function that, given the training set and a particular, computes the logistic regression cost and gradient with respect to for the x and y dataset. Final value is used to plot training data decision boundary.

### 1.1.9 Semi-Supervised Learning

Semi-supervised learning combines supervised and unsupervised methods. It can be useful in machine learning and data mining where unlabeled data is present and labelling it is tedious. With supervised machine learning, you train an algorithm on a “labelled” dataset with outcome information [13].

### 1.1.10 Transductive SVM

TSVM is widely used for semi-supervised learning with partially labelled data. Its generalizations have been a source of mystery. It labels unlabeled data so the margin between them is maximum. TSVM is NP-hard [14].

### 1.1.11 Generative Models

Data-generating models are generative. It models features and class (complete data). All algorithms modelling P (x, y) are generative because I can use its probability distribution to generate data points. One labelled sample per component confirms mixture distribution.

### 1.1.12 Self-Training

A classifier self-trains using labelled data. Unlabeled data feeds the classifier. The training set combines unlabeled and predicted labels. It's repeated. The classifier self-trains, hence the name [15].

### 1.1.13 Relearning

Reinforcement learning focuses on how software agents should act to maximise cumulative reward. Reinforcement learning is one of three basic machine learning paradigms [16, 17].

### 1.2 Conclusions

In this chapter we survey some algorithms of machine learning. When we have less amount of labelled data then machine learning would be best. In the future we will review Reinforcement learning. Today, each person uses machine learning algorithm, whether knowingly or unknowingly.

This chapter summarizes supervised learning algorithms and explains machine learning. It also describes machine learning algorithm structures. This area has seen a lot of development in the last decade. The learning methods produced excellent results that were impossible in the past. Due to rapid progress, developers can improve supervised learning methods and algorithms.

## References

- 1. Carbonell, Jaime G., Ryszard S. Michalski, and Tom M. Mitchell. An overview of machine learning. *Machine Learning* (1983): 3-23.
- 2. Mahesh, Batta. Machine learning algorithms-a review. *International Journal of Science and Research (IJSR)*. [Internet] 9 (2020): 381-386.
- 3. Ayodele, Taiwo Oladipupo. Types of machine learning algorithms. *New Advances in Machine Learning* 3 (2010): 19-48.
- 4. Ray, Susmita. A quick review of machine learning algorithms. *2019 International Conference on Machine Learning, Big Data, Cloud and Parallel Computing (COMITCon)*. IEEE, 2019.
- 5. Vabalas, Andrius, et al. Machine learning algorithm validation with a limited sample size. *PloS one* 14.11 (2019): e0224365.
- 6. Tom Mitchell, McGraw Hill (2015) *Machine Learning*.
- 7. S. B. Kotsiantis. (2007) Supervised Machine Learning: A Review of Classification Techniques. In *Proceedings of the 2007 Conference on Emerging Artificial Intelligence Applications in Computer Engineering: Real World AI Systems with Applications in eHealth, HCI, Information Retrieval and Pervasive Technologies, The Netherlands*.
- 8. Amanpreet Singh, Narina Thakur, Aakanksha Sharma (2016). A review of supervised machine learning algorithms. In *Computing for Sustainable Global Development (INDIACom), 2016 3rd International Conference on*.
- 9. http://www.slideshare.net/GirishKhanzode/supervised-learning-52218215
- 10. https://www.researchgate.net/publication/221907660_Types_of_Machine_Learning_Algorithms
- 11. http://radimrehurek.com/data_science_python/
- 12. http://www.slideshare.net/cnu/machine-learning-lecture-3 An overview of the supervised machine learning methods
- 13. http://gerardnico.com/wiki/data_mining/simple_regression
- 14. http://aimotion.blogspot.mk/2011/11/machine-learning-with-python-logistic.html
- 15. Dasari L. Prasanna; Suman Lata Tripathi, “Machine and Deep-Learning Techniques for Text and Speech Processing,” in *Machine Learning Algorithms for Signal and Image Processing*, IEEE, 2023, pp. 115-128, doi: 10.1002/9781119861850.ch7
- 16. Kanak Kumar; Kaustav Chaudhury; Suman Lata Tripathi, “Future of Machine Learning (ML) and Deep Learning (DL) in Healthcare Monitoring System,” in *Machine Learning Algorithms for Signal and Image Processing*, IEEE, 2023, pp. 293-313, doi:10.1002/9781119861850.ch17.
- 17. Deepika Ghai, Suman Lata Tripathi, Sobhit Saxena, Manash Chanda, Mamoun Alazab, *Machine Learning Algorithms for Signal and Image Processing*, Wiley IEEE Press-2022, ISBN: 978-1-119-86182-9

## Artificial Intelligence and Image Recognition Algorithms

Siddharth¹*, Anuranjana¹ and Sanmukh Kaur²

¹Dept. of Information Technology, Amity School of Engineering and Technology, Amity University Uttar Pradesh, Noida, India ²Dept. of Electronics and Communication Engineering, Amity School of Engineering and Technology, Amity University Uttar Pradesh, Noida, India

### Abstract

Various computer vision tasks, including video object tracking and image detection/classification, have been successfully achieved using feature detectors and descriptors. In various phases of the detection-description pipeline, many techniques use picture gradients to characterize local image structures. In recent times, convolutional neural networks (CNNs) have taken the place of some or all of these algorithms that rely on detectors and descriptors. Earlier algorithms, such as the Harris Corner Detector, SIFT, ASIFT and SURF that were once hailed as cutting-edge image recognition algorithms have now been replaced by something more robust. This document highlights the generational improvement in image recognition algorithms and draws a contrast between current CNN-based image recognition techniques and previous state-of-the-art algorithms that don’t rely on CNN. The purpose of this study is to emphasize the necessity of using CNN-based algorithms over traditional algorithms which are not as dynamic.

### Keywords

Convolution Neural Networks (CNN), Scale Invariant Feature Transform (SIFT), Artificial Intelligence (AI), Speeded Up Robust Features (SURF)

## 2.1 Introduction

The rising capabilities of artificial intelligence in areas like high-level thinking and sensory handling have made it more revered than human intelligence. Its encounter nature excels in every significant aspect of the supervisory environment. The sole focus of critics since the advent of the fifth computing period has been to pretend that the brain-computer is viable and dynamic [1]. The capacity for computers to decode and identify the contents of the billions of photographs and millions of hours of video that are published on the internet each year is a challenge that has immense importance. However, there has been a lot of study on deriving high-level information from raw pixel data.

Many conventional techniques rely on the discovery and extraction of significant key points. Numerous techniques have been put forth to find and describe characteristics mentioned in [2, 3]. SIFT and ASIFT [4], which are built on and improved upon from Harris Corner Detector [5], are two of the most often used techniques along with SURF [6]. The image matching algorithms usually consist of two parts: detector and descriptor. They first detect points of interest in the compared images and select a region around each point of interest, and then associate an invariant descriptor or feature to each region. Similarities may thus be established by matching the descriptors. Detectors and descriptors should be as invariant as possible [3].

For identifying and categorizing features, researchers have proposed Convolution Neural Network–based algorithms in recent years [7]. CNNs have been effectively employed to tackle challenging issues like speech recognition and image classification. They were first introduced by Fukushima in 1998. CNNs are made up of neurons, and each one determines the learning’s weight and inclination. It also includes an input layer, an output layer, and various hidden layers, where the hidden layer includes standardized layers such as convolutional, pooling, and fully associated layers [10]. The convolutional layer connects two data arrangements using a convolution activity. It pretends to be a certain neuron's input for visual enhancements. The pooling layer is used to reduce the dimensions by pooling the output of the neuron cluster at a single layer with one neuron [8].

This paper highlights the transition between CNN-based and traditional image detection algorithms. We also draw a contrast between the two methods and why CNNs are preferred over the traditional image recognition/classification methods.

