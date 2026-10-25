
U., J., Olesnikova, A., Song, C. H., & Lee, W. D. (2009, January). The development and application of decision tree for agriculture data. In 2009 Second International Symposium on Intelligent Information Technology and Security Informatics (pp. 16–20). IEEE.

Valsamis, E. M., Husband, H., & Chan, G. K. W. (2019). Segmented linear regression modelling of time-series of binary variables in healthcare. Computational and Mathematical Methods in Medicine. doi:10.1155/2019/3478598 PMID:31885678

Wiggins, M., Saad, A., Litt, B., & Vachtsevanos, G. (2008). Evolving a Bayesian classifier for ECG-based age classification in medical applications. Applied Soft Computing, 8(1), 599–608. doi:10.1016/j.asoc.2007.03.009 PMID:22010038

Wu, M. C., Lin, S. Y., & Lin, C. H. (2006). An effective application of decision tree to stock trading. Expert Systems with Applications, 31(2), 270–274. doi:10.1016/j.eswa.2005.09.026

Zhao, L., Chen, Y., & Schaffner, D. W. (2001). Comparison of logistic regression and linear regression in modeling percentage data. Applied and Environmental Microbiology, 67(5), 2129–2135. doi:10.1128/AEM.67.5.2129-2135.2001 PMID:11319091

## Chapter 3

## Understanding Convolutional Neural Network With TensorFlow: CNN

**Aswathy Ravikumar**
https://orcid.org/0000-0003-0897-6991
Vellore Institute of Technology, Chennai, India

**Harini Sriraman**
https://orcid.org/0000-0002-2192-8153
Vellore Institute of Technology, Chennai, India

## ABSTRACT

In academia and business, deep-learning-based models have exhibited extraordinary performance over the last decade. The learning potential of Convolutional Neural Networks (CNNs) derives from a combination of several feature extraction levels that completely use a vast quantity of input. CNN is an important technique for tackling computer vision issues, although the theories behind its processing efficacy are not yet completely understood. CNN has achieved cutting-edge performance on a variety of datasets in computer vision applications like remote sensing, medical image categorization, facial detection, and object identification. This is due to the efficiency with which they process visual features. This chapter presents the most significant advancements in CNN for efficient processing in computer vision, including convolutional layer configurations, pooling layer approaches, network activation functions, loss functions, normalization approaches, and CNN optimization techniques.

## INTRODUCTION

The core of intelligence for computers and other electronic devices is machine learning. It use predictive models based on previous data to forecast future behaviors, outcomes, and patterns. Deep learning is an subfield of machine learning in which models brain-inspired are represented mathematically. Deep Neural Networks’ (DNN) parameters, which may vary from a few hundred to over 1.2 billion, are dynamically learnt from the data. DNNs can describe complex nonlinear relationships between inputs and outputs. Their designs result in compositional models that depict the thing as a layered mixture of primitives. There are several variations of a few core approaches with deep structures. DNN utilizes hierarchical structures to learn high-level representations from data. It is a relatively recent technique that is commonly used in traditional applications of artificial intelligence, such as text categorization, learning techniques, natural-language processing, and machine vision. There are three key reasons for the rise in popularity of deep learning: vastly increased chip processing capabilities, decreased computer system prices, and substantial breakthroughs in machine learning techniques. As a consequence, DNNs have garnered a great deal of interest in recent years, and multiple models for diverse applications have been proposed.

Artificial Neural Networks (Guo et al., 2016) are computer processing systems that are substantially influenced by the operation of natural nervous systems. ANNs are primarily composed of many linked computational nodes (called neurons) that function dispersedly to train from inputs to maximize their output. Its input, often in the shape of multidimensional vectors, would have been loaded into the input layer and redistributed among the hidden units. This is known as the learning experience. The hidden units would then make judgments based on the last layer and evaluate how an unexpected change inside itself affects or enhances its correct outcome. Hidden layer levels built atop one another is referred to as deep learning. Supervised and unsupervised learning are the primary learning approaches in image analysis jobs. Supervised learning involves learning using inputs that have been pre-labeled and serve as objectives. Every training sample will have a set of input variables (feature vector) and one or more associated corresponding outputs. This kind of training aims to lower the overall classification error of a model by the proper computation of the actual output of training images.

In unsupervised, the trained model does not contain any labels. Typically, the success of a network is assessed by whether or not it can lower or raise an associated cost factor. However, it is essential to highlight that most image-based pattern recognition tasks rely on categorization utilizing supervised learning. Convolutional Neural Network is similar to conventional ANNs in that it consists of neurons that optimize themselves via learning. Each neuron will continue to receive inputs and execute an action (including a scalar product and then a nonlinear variable) - the fundamental building blocks of innumerable ANNs. The complete network will continue representing a single perceptual criterion (the weight) through input raw picture vectors to output class scores. The last layer will include loss functions connected with the classes, and every one of the standard techniques established for conventional ANNs will still be applicable.

CNN is one of the most essential and useful kinds of neural networks (Albawi et al., 2017) and is commonly used for categorization and object segmentation. The three major layers of a CNN are convolution, pooling, and fully connected. Each level is accountable for certain spatial tasks. CNN uses a variety of kernels in convolution layers to convolve the input image and create feature maps. The pooling layer often follows the convolution layer. This layer compresses both feature maps and system parameters. Following a layer that has been flattened and the layer that is pooling, there are a series of layers that are all interconnected. The flattened layer transforms the 2D feature maps of the previous layer into 1D feature maps suitable for the future fully connected levels. The vector that has been flattened may be used to categorize the photographs later. Pooling is a crucial step in convolutional networks since it reduces the size of the feature maps. By merging a collection of values into a lower number of values,

### Figure 1. Shallow neural network structure

![](img/20813928ec98c7f6fbdbab0d52bde2f1_71_0.png)

it decreases the complexity of a feature map. It turns the composite visual features into information that may be used by conserving essential data and deleting extraneous data.

By eliminating specific connections among convolutional layers, pooling operators enable spatial translation invariance while reducing the computational cost of top layers. This layer conducts downsampling on the previous layer's feature maps to generate new maps with a lower resolution. This layer has two basic functions: the first is to reduce the computational cost by minimizing the number model parameters or weights, and the second is to avoid overfitting. A smart pooling strategy should only extract relevant data and eliminate superfluous pieces.

The Dropout (N. Srivastava et al., n.d.) can be applied for the Regularization of CNN. The regularization of CNN is done by Dropout by the addition of noise to the feature map of the corresponding layer.

Overfitting (Carremans, 2019) occurs when a network cannot properly learn due to various factors. It is a crucial notion in the majority, if not all, ML algorithms, and every effort must be made to minimize its impacts. If our models exhibited symptoms of overfitting, our capacity to identify generalized characteristics for not just our training dataset but also our testing and prediction datasets might be diminished. This is the primary motivation for simplifying our ANNs. The fewer parameters are necessary to train a network, the less probable it is to overfit - and, thus, the better its predictive accuracy. A small ANN structure is shown in Figure 1.

## CONVOLUTIONAL NEURAL NETWORK

CNN is a type of algorithm for deep learning for handling gridded data, such as images, that is impacted by the architectural style of the mammal visual cortex (Albawi et al., 2017; Fukushima, 1980; Hubel &
