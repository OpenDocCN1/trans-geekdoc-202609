
In modern forensic investigations, machine learning has become an essential tool due to its capacity to unravel complex patterns, handle large amounts of data and uncover concealed insights. For instance, imagine a puzzle and each piece of the puzzle has specific information that is useful in solving the case. Traditional forensic investigation methods include manually examining each piece of the puzzle, which could be time-consuming, or some minute detail can be overlooked. However, machine learning is the digital puzzle solver that can solve the most complex puzzle in less time (Lefèvre 2018; Metcalf et al., 2017).

Fingerprints are considered one of the dominant biometric traits due to their various characteristic traits such as acceptability, high security, reliability and low cost (Awad 2012, Jain et al., 1999). Therefore, there are lots of fingerprint identification systems, but they lack identification time and accuracy in different stages of fingerprint examination such as fingerprint acquisition, fingerprint processing and enhancement, fingerprint extraction, fingerprint matching and fingerprint classification as described in Figure 7.1 (Egawa et al., 2012, Jain et al., 2011). Machine learning is used for fingerprint/pattern examination to overcome these problems.

From identifying minute details in fingerprints or deciphering the link between different pieces of evidence, machine learning is also used in DNA forensics to decode complex DNA sequences, genetic profiling or identifying markers. Besides these, it is used in financial fraud investigation, pattern evidence analysis, digital investigations, medicine and toxicology and many more (Padma and Don, 2022; Haroon et al., 2020).

## FINGERPRINT RECOGNITION, IDENTIFICATION, AND MATCHING USING ARTIFICIAL NEURAL NETWORK

![](img/b862fc39ed9add71b3d54909afaeaeb0_135_0.png)

- Fingerprint images are collected from various sources
- Images are preprocessed to enhance quality and remove noise.
- Ridge counting
- Ridge Frequency
- Minutiae Points
- Labelled data to examine whether given image is fingerprint or not.
- Images with marked delta, and core to examine type of fingerprint.
- Pair of images along with the labels indicating whether image belongs to same person or not.

Figure 7.1 Fingerprint recognition, identification and matching using artificial neural networks is the process that involves training neural networks to analyze fingerprint images and make decisions about their identity or similarity (Awad, 2012; Hambalik, 2016; Shehu et al., 2018).

## Machine Learning Techniques in Fingerprint/Pattern Recognition/Identification/Matching

In biometric security and pattern recognition, using machine-learning algorithms has enhanced the security and other parameters in the fingerprint/pattern recognition/identification/matching field. Machine-learning algorithms contribute to fingerprint identification and matching to meet the growing demand for accurate and robust human identity verification methods. From classical algorithms to advanced deep learning models, these techniques have enhanced the precision of fingerprint analysis and enabled automation and scalability in various applications (Awad 2012).

### 1. Artificial Neural Network

It is a model inspired by the human brain’s neural network, that is, it works similarly to the biological neural network in the human brain. Neural network algorithms are used for various tasks such as classification, regression, pattern recognition and management (Krogh 2008). The neural network algorithm works on three layers: input, hidden and output (Walczak 2019).

- **Input Layer:** The starting point receives the raw input data. Each neuron in the input layer corresponds to the specific feature on the attribute, and its value represents the value of that feature. Each neuron passes the value to the neuron of the next level.
- **Hidden Layer:** It is the intermediate layer responsible for learning and representing complex pattern relationships in data. It is the layer where the network learns to recognize features and combinations of features that are relevant to making predictions. The number of hidden layers and the number of neurons in each hidden layer are hyperparameters that need to be chosen based on the complexity of the problem.
- **Output Layer:** It produces the final results of neural network computation.

### Components

- **Neural (Node):** It is the basic unit of the neural network algorithm. Each neuron works on different layers; therefore, each receives input, processes it and produces an output (Walczak 2019).
- **Connection (Synapses):** Neurons are connected through weighted connections called synapses (Walczak 2019).
- **Propagation:** This is how input data is passed through the network. There are two types of propagation methods: (i) feed forward propagation method: in this method, input data is passed through the network to generate prediction or output and (ii) back propagation method: this method follows the feed forward propagation method. This method adjusts the network’s connection weight to minimize the error between predicted and target values (Krogh 2008).
- **Training Data:** This is the supervised machine-learning algorithm; training data consists of input features and corresponding target values.

### 1. Support Vector Machine

Support vector machine (SVM) is one of the most powerful machine-learning algorithms for linear and non-linear classification, regression, and outlier detection. In linear classification, the decision boundary that separates different classes is a single line or hyperplane, whereas non-linear classification involves more complex decision boundaries that a single straight line or hyperplane can not define. SVM utilizes the ‘Kernel trick’ technology to excel in non-linear classification. The classes might have intricate and curved feature space. Moreover, the SVM algorithm can be extended to classify data into more than two groups with the help of a technique known as ‘multi-class-classification’ in combination with various methods such as one-versus-all and one-versus-one (Suthaharan et al., 2016; Pisner et al., 2020).

### Components

- **Data Points and Features:** It refers to a specific instance or example from the data set that you are using to train, validate or test the SVM model. Each data point is linked with a set of features that describes the characteristics (Guenther and Schonlau, 2016).
- **Hyperplane:** Hyperplane is the plane or line that separates different classes in the feature space (feature space is the collection of all feature vectors from space). In 2D cases, the hyperplane is the line, and in higher dimensions, it is the hyperplane. The algorithm aims to find the hyperplane that maximizes the margin (Pisner and Schnyer, 2020).
- **Support Vector:** Support vectors are the closest data points to the hyperplane. These data points determine the optimal position of the hyperplane (Meyer and Wien, 2015).
- **Margin:** Distance between the hyperplane and nearest support vector. The higher the margin, the better the generalization of the new data will be.
- **Kernel Function:** This technology handles the non-linear relationship between features (Pisner and Schnyer, 2020).

The SVM algorithm is used in fingerprints to classify fingerprint images in different categories such as arches, loops, whorl, etc. (Awad, 2012). Fingerprint images were classified into one of five categories: whorl, right loop, left loop, arch and tented arch, using multi-class classification (Yao et al., 2001). The SVM algorithm was designed to classify the fingerprint images in different categories like whorl, right loop, left loop, arch and tented arch with 92.5% accuracy (Alias and Radzi, 2016). The SVM algorithm was designed and trained to recognize the finger code. Moreover, the research compares two methods that are SVM and RBF. And, concluded that SVM has better recognition rates (Elmir et al., 2012). The fingerprint classification method based on the twin support vector machine was studied in which the Gabor filter is used to extract texture features and the experimental results show that applying the twin support vector machine algorithm gives good classification results (Ding et al., 2020). SVM classifier was used to separate fingerprint images into one of the three quality classes: good, medium, and poor (Liu et al., 2008).

## Convolutional Neural Network

It is the extended version of the artificial neural network algorithm. This algorithm is mainly used to extract the features from grid-like matrix datasets. Convolutional neural networks have revolutionized computer tasks by automatically learning hierarchical features from input data, making them particularly effective in tasks such as image classification, object detection, etc. A convolutional neural network (CNN) works on the filters, and filters keep sliding on the image and capture the desired features (O’Shea and Nash, 2015).

### Architecture/Workings (Albawi et al., 2017; O’Shea and Nash, 2015)

- **Input Layer:** The input layer to CNN is typically an image, represented as a grid of pixel values.
- **Convolutional Layer:** These are the core building blocks of CNN. They apply a set of learnable filters to input images. Each filter is a small, square matrix that slides across the input image in horizontal and vertical directions. Multiple filters are applied in parallel to
