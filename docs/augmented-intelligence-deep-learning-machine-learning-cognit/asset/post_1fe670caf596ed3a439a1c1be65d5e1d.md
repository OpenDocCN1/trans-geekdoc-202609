
[http://dx.doi.org/10.2527/1999.77497x] [PMID: 10328365]

- [62] MAPA, *INSTRUÇÃO NORMATIVA No 1, DE 13 DE JANEIRO DE 2020*. Brasília, 2020.
- [63] L.D.C. Luiz, M.J.V. Bell, R.A. Da Rocha, N.L. Leal, and V.D.C. Dos Anjos, "Detection of Veterinary Antimicrobial Residues in Milk through Near-Infrared Absorption Spectroscopy", *J. Spectrosc.*, vol. 2018, pp. 1-6, 2018. [http://dx.doi.org/10.1155/2018/5152832]

## CHAPTER 4

## Applications of Deep Learning in Medical Engineering

**Sumit Kumar Jindal**^1, **Sayak Banerjee**^1, **Ritayan Patra**^1 and **Arin Paul**^1

^1 School of Electronics Engineering, Vellore Institute of Technology, Tamil Nadu, India

**Abstract:** As a result of considerable breakthroughs in the field of artificial intelligence, deep learning has achieved exceptional success in resolving issues. This work brings forth a historical overview of deep learning and neural networks and further discusses its applications in the domain of medical engineering - such as detection of brain tumours, sleep apnea, arrhythmia detection, *etc.*

One of the most important and mysterious organs of our body is the brain. Like any other organ, our brain may suffer from various life-threatening diseases like brain tumours which can be malignant or benign. Analysis of the brain MRI images by applying convolution neural networks or artificial neural networks can automate this process by classifying these images into various types of tumours. A faster and more effective method can be provided by this method for detecting the disease at a key stage from where recovery is possible.

Sleep apnea is a sleeping disorder involving irregular breathing. The brain detects a sudden decrease in the level of oxygen and sends a signal to wake the person up while he is sleeping. Cardiac arrhythmia refers to a group of conditions that causes the heart to beat irregularly, too slowly, or too quickly, *e.g.*, atrial fibrillation. Deep learning along with bio-medical signal and audio processing techniques on respiratory sound datasets and ECG datasets have huge potential in the detection of these diseases. Deep learning outperforms the existing detection algorithms and a good amount of effort on feature engineering, augmentation techniques, and building effective filters can get a high accuracy result.

**Keywords:** Artificial intelligence, Artificial neural networks, Atrial fibrillation, Automation, Audio processing, Brain tumours, Bio-medical signal processing, Cardiac arrhythmia, Convolution neural networks, Deep learning, ECG, EEG, Feature engineering, Machine learning, MRI imaging, Neural networks, Optimization, Signal processing, Signal analysis, Sleep apnea.

*Corresponding author Sumit Kumar Jindal:* School of Electronics Engineering, Vellore Institute of Technology, Tamil Nadu, India; Tel: +918603559888; E-mail: sumitjindal08@gmail.com

### 4.1. HISTORICAL OVERVIEW OF DEEP LEARNING

### 4.1.1. Machine Learning

Machine learning can be defined as methods used to make a computer learn and automate various tasks without being explicitly programmed [1]. Tom Mitchell provides a modern definition of machine learning. “A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at Tasks T, as measured by P, improves with experience E.” These methods or algorithms work on the data, learn important features from that data, and then apply these learned features to make important decisions to new sets of data. For example, machine learning algorithms are used in online music streaming services or video streaming services to make a recommendation to its users based on the user’s listening preferences.

In earlier days, when the penetration of internet in the society and the use of technology in everyday life was less, the amount of data generated was less, and the training of machine learning algorithms on such a small amount of data led to problems known as overfitting. Overfitting decreases the accuracy of machine learning algorithms as it performs poorly on test data. So, researchers, data scientists, and machine learning engineers would primarily focus on how to solve this problem of overfitting.

But with time, the size of datasets began to increase. Nowadays, several GBs of data can be found on various topics and the problem of overfitting began to disappear as the dimensionality of the data began to increase. But processing such a huge dataset using machine learning algorithms is not possible as the learning capacity gets saturated, which leads to underfitting. This happens because machine learning algorithms use shallow structures.

The deep neural networks used in deep learning algorithms have large learning capacities as they can handle a large number of parameters. When compared to machine learning techniques, the performance of deep learning owing to overfitting is either the same or worse. So, whenever the dataset is huge, the use of deep learning techniques is most suitable. They increase the learning capacity of the models as they have better optimization techniques and use large computational resources.

### 4.1.2. Neural Networks

A neural network is a web of neurons [2]. In biology, these are similar to the neurons present in the brains of any living organisms, while in computer science,

these are artificial neurons used to solve complex mathematical, statistical, or artificial intelligence problems. These artificial neurons mimic the working of the human brain. The deep learning algorithms use these deep neural networks, as shown in Fig. (4.1), to train the model.

![](img/be45bf301a3c0ebefb162571e2625fab_82_0.png)

**Fig. (4.1).** Architecture of a Deep Neural Network.

Neural networks must include numerous layers, not just one or two, to answer difficult real-world artificial intelligence concerns. In Fig. **4.1**, the neurons are arranged in various layers, which are in turn connected to adjacent layers with some numerical weights. In feedforward operations, the neurons in each layer receive some signal and transfer it to the neurons in the adjacent layer after performing some mathematical calculations on the input and passing it through an activation function [3].

In each hidden neuron j, the weighted sum of input neurons is first calculated as in Equation 1a:

$$Net_j = \sum_{i=1}^{d} x_i w_{ji} + w_{j0} \tag{1a}$$

Where $Net_j$ is the total activation value of the neuron, $w_{ji}$ are the weights of connections between the input layer and the hidden layer, $w_{j0}$ are the bias terms associated with each neuron, and $x_i$ is the input value. This value is then passed through a special activation function like $y = g(Net_j)$, which is used to remove the linearity in the data. If the total activation value is greater than the threshold value of the activation function, then the value is transmitted to the next neuron; otherwise, it will not get transferred.

In a multi-layer neural network, the final output looks something like the one shown in Equation 1b –

$f(x) = g(\sum_{j=1}^{nH} Wkj\, g(\sum_{i=1}^{d} wijg(...) + wj0) + wk0)$  (1b)

Another important process that is applied is Backpropagation. It is one of the most important training algorithms in deep learning. It is used to reduce the error rate in the previous epochs. It is done by choosing the proper weight of each neuron in order to increase the accuracy, making the deep learning model more reliable and closer to real-world scenarios. When the feed-forward operation is applied, most of the time, it generates some loss that is fed backwards in the neural network during backpropagation, helping fine tune the weights for the next epoch in order to get a better result (or reduced loss). It uses an optimization function that is different for each deep learning algorithm to determine in which way it will adjust the weights in order to reduce the loss from the present value and produce a better result that is closer to the target value [2, 3].

### 4.1.3. Deep Learning

Deep learning is a subpart of machine learning. Deep Learning, in simple terms, can be defined as a combination of neural networks and algorithms which consume raw input data from users and performs nonlinear mathematical transformations on the given input data in order to reach the desired output with high accuracy [4].

In 1943, Walter Pitts and Warren McCulloch created a computer model of neural network, which acts like the human brain. Henry J. Kelley developed the continuous Back Propagation Model in 1960. Kunihiko Fukushima developed the first convolutional neural network in 1979. He designed a neural network with multiple pooling and convolutional layers. In the late 20th century, the computational power was not high enough to create complex deep learning neural networks. But in the early 2000s, GPUs were a thousand times more powerful than normal CPUs developed and they acted as fuel in the development of highly efficient neural networks. By 2011, the speed of GPUs was sufficient enough to train whole neural networks together instead of training layer by layer. It became clear that with increased computational speed, the deep learning algorithms have a significant edge over other machine learning algorithms in terms of efficiency and speed.

Deep Learning architectures like Convolutional Neural Network (CNN) or Recurrent Neural Network (RNN) are being applied every day in fields like
