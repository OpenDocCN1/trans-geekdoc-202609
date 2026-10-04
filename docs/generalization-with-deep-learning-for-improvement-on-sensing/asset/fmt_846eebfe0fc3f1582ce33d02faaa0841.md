
## Introduction of Deep Learning Algorithms

© 2021 World Scientific Publishing Company

https://doi.org/10.1142/9789811218842_0001

## Chapter 1

## An Introduction of Deep Learning Methods for Sensing Applications

Keyu Wu[\*](#chap1.xhtml#fn1), Wei Cui^([†](#chap1.xhtml#fn2)), Vuong Nhu Khue^([‡](#chap1.xhtml#fn3)) and Efe Camci^([§](#chap1.xhtml#fn4))

*Institute for Infocomm Research, 1 Fusionopolis Way, Singapore 138632*

[\*](#chap1.xhtml#fnr1)*wu_keyu@i2r.a-star.edu.sg*

^([†](#chap1.xhtml#fnr2))*cui_wei@i2r.a-star.edu.sg*

^([‡](#chap1.xhtml#fnr3))*vuong_nhu_khue@i2r.a-star.edu.sg*

^([§](#chap1.xhtml#fnr4))*efe_camci@i2r.a-star.edu.sg*

**Abstract**

This chapter will briefly introduce various deep learning algorithms for improving sensing capabilities. For different sensing applications, specific deep learning architectures may be employed with proper adjustments based on the properties of sensing applications. In order to know which deep learning algorithms may be suitable for a unique sensing application, a clear understanding of different deep learning algorithms is compulsory. Currently, there are numerous deep learning algorithms. Here, we will only cover some widely used ones for sensing applications, including auto-encoder, restricted Boltzmann machine, convolutional neural network, recurrent neural network and their variants. At the end of this chapter, we will provide some discussion and a comparison of different deep learning methods.

**Keywords:** deep learning, auto-encoder, restricted Boltzmann machine, convolutional neural network, recurrent neural network

### 1.Introduction

With the development of advanced sensing technology, more and more sensory data are easily collected and have become available for various sensing applications, such as activity recognition [[1](#chap1.xhtml#fsr1)], remote sensing [[2](#chap1.xhtml#fsr2)], medical image processing [[3](#chap1.xhtml#fsr3)], disease diagnostic and identification [[4](#chap1.xhtml#fsr4)], etc. Generally, for a specific sensing application, certain suitable sensors can be selected or adopted. For instance, the sensing task of human activity recognition can be achieved by using vision sensors (i.e., cameras) [[5](#chap1.xhtml#fsr5)], inertial sensors [[6](#chap1.xhtml#fsr6)] and/ or WiFi signals [[7](#chap1.xhtml#fsr7), [8](#chap1.xhtml#fsr8)] , although different sensors may have their unique properties and limitations. For example, vision-based solutions have high accuracy for activity recognition. However, they can only cover a specific area with the requirement of sufficient illumination condition and may suffer from privacy concerns. On the other hand, wearable/smartphone inertial sensors are convenient for activity sensing [[9](#chap1.xhtml#fsr9), [10](#chap1.xhtml#fsr10)], but may be only able to identify some simple activities, such as walking, running, sitting, going upstairs/downstairs, etc. Recently, WiFi-based solutions have attracted great attention, because they are widely available and do not require users to wear any devices on their bodies [[11](#chap1.xhtml#fsr11)]. Nevertheless, they often have limited performance, especially for multi-user scenarios.

To achieve real-world sensing applications, we generally can divide the existing methods into two different categories, i.e., model-based and data-driven approaches. The model-based methods require to know the physical relationship/model between sensor data and the specific task. In real life, the physical models are typically not available, especially for complicated sensing applications. Instead, data-driven methods become more and more popular, as they do not require to explicitly know the physical model of the problem. In fact, they are able to automatically learn the relationship from the data.

The most widely used data-driven models in sensing applications are machine learning methods [[12](#chap1.xhtml#fsr12)]. Particularly, conventional machine learning algorithms require two steps for solving sensing application problems from given data. The first step is feature engineering which attempts to manually extract useful representations (also known as features) from the raw data. For instance, some statistical features, such as mean, variance and frequency components, can be extracted in smartphone sensor-based activity recognition [[13](#chap1.xhtml#fsr13)], which are helpful in separating different physical activities of walking, running and staying static. After extracting useful features, traditional machine learning algorithms, e.g., artificial neural network (ANN), support vector machine (SVM), k-nearest neighbor (KNN), decision tree (DT), random forest (RF), etc., can be leveraged to perform sensing or classification tasks. However, the conventional machine learning-based sensing needs to conduct manual feature engineering, which requires strong application-specific domain knowledge and will inevitably miss implicit features [[14](#chap1.xhtml#fsr14)]. This limits the performance of these methods in sensing applications.

Recently, deep learning which is a new branch of machine learning has achieved great success for a variety of sensing applications [[15](#chap1.xhtml#fsr15)]. Different from conventional machine learning methods which contain tedious and costly manual feature engineering, deep learning methods can automatically learn features from data and perform inference simultaneously (end-to-end model), such that the feature learning and inference can be jointly optimized, resulting in a superior performance in many application domains.

This book intends to explore different deep learning methods that enhance sensing capacity. Before that, in this very first chapter, we shall provide a brief description of various standard deep learning algorithms for sensing applications in the following sections, so that readers can have some basic understanding before zooming into more advanced deep learning approaches.

### 2.Deep Learning Methods

Deep learning is a new branch of machine learning. It intends to use multiple layers of neural networks to learn high-level representations of raw data and performs inference with these representations (also known as features) [[15](#chap1.xhtml#fsr15)]. Many deep learning architectures have been proposed for different applications. In this chapter, as we focus on the applications of improving sensing capacities, only relevant deep learning architectures that target sensing capabilities will be introduced in detail. Specifically, we will introduce autoencoder in [Section 2.1](#chap1.xhtml#s2-1), restricted Boltzmann machine in [Section 2.2](#chap1.xhtml#s2-2), convolutional neural network in [Section 2.3](#chap1.xhtml#s2-3) and recurrent neural network in [Section 2.3.6](#chap1.xhtml#s2-3-6).

#### 2.1 Auto-encoder

Auto-encoder is a type of backpropagation neural network where the output and input are set to be the same. Auto-encoders aim to learn an approximation of the identity function and were first introduced by Hinton [[16](#chap1.xhtml#fsr16)] to address the problem of unsupervised learning. To learn interesting properties of the data, auto-encoders are usually conditioned by placing constraints on the network such as limiting the number of hidden neurons. The reason is that learning the identity function could be trivial or meaningless without restrictions of network structure. Therefore, by imposing conditions on the network, auto-encoders are forced to prioritize which relevant aspects of the data are to be copied or learned; hence, hidden structure in the input data such as correlated input features could be discovered [[17](#chap1.xhtml#fsr17)].

![figure](images/p6-1.jpg)
