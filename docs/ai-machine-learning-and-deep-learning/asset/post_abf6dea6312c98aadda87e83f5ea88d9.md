
## 13.7 DEEP LEARNING TECHNIQUES IN CYBER SECURITY

These days, there is a huge development in various technologies such as IoT, cloud computing, big data, requiring cyber security to protect applications and networks [44]. Technology giants like Microsoft, Google, Salesforce, Facebook, etc. have deep learning in their deliverables [45]. Deep learning that is grounded on artificial neural networks with more hidden layers is the next level of machine learning. Deep learning when compared with machine learning is more proficient due to its deep layers structure and its capability to learn by itself and produce better results.

### 13.7.1 Deep Auto-encoder

Deep auto-encoder monitors and learns the usage pattern of normal users’ behavior, as depicted in Figure 13.12. It is an unsupervised learning that recreates the output based on the input [15]. When the usage pattern of the user changes, that is measured as an anomaly. Here the resemblance among present behavior Vi(t) and normal behavior Vi(0) is measured [13]. A threshold value k is fixed by the admin, when the difference goes beyond the predefined threshold value that is considered abnormal activity.

![](img/efffc69cb8cda75bcf341884e3396898_304_0.png)

![](img/efffc69cb8cda75bcf341884e3396898_305_0.png)

FIGURE 13.12 Flow of intrusion detection system.

### 13.7.2 Convolutional Neural Networks (CNN)

As the usage of the internet increases, malware is also increasing. CNN is one of the deep learning methods that depend on neural network. This processes the input in the form of an array, generally used for processing two-dimensional and three-dimensional array. The main three components of CNN are (1) the convolutional layer named after the convolution operation in mathematics; (2) the pooling layer used in the dimensionality reduction; and (3) the classification layer used for the final classification. One-dimensional convolutional layers with single-dimensional filters of 3×1 size slide at one stride along with rectified linear unit activation are used, followed by two fully connected dense layers [18, 21], as shown in Figure 13.13. Here, there is no need to reduce input size because max pooling layers are not used. Dropout layers are used to avoid overfitting.

![](img/efffc69cb8cda75bcf341884e3396898_306_0.png)

FIGURE 13.13 Sample 1 dimension CNN architecture.

This one-dimensional CNN is an intrusion detection mechanism that provides accurate results [16, 17]. CNN-based intrusion detection outperforms other intrusion detection mechanisms due to its deep layers and reduced training time.

### 13.7.3 Recurrent Neural Networks (RNNs)

In the world of advanced technology with its enormous data, intrusion and malware become major threats for small to big companies through any means, such as email, downloadable file, software, etc. Such intrusions require efficient systems to prevent these activities and to protect valuable data and the network itself. Recently, deep learning algorithms have played a major part in cyber security. RNN is a feed-forward neural network based on a deep learning method that holds not only the current state but also the previous state, so it is called recurrent. The hidden layer that includes the previous state is represented as follows:

$S_t = \phi\,(w x_t + H x_{t-1})$

where $S_t$ represents the hidden state at time $t$, $w$ is the weight, $H$ is some hidden state, and $\phi$ represents some activation function, which can be a sigmoid or tanh function [19]. This RNN can solve any supervised or unsupervised task and outperforms traditional machine learning algorithm in intrusion or fraud detection. The number of layers and the epochs varies depending on the task on which it acts [20]. This RNN includes a recurrent layer with neurons that maintain the previous information along with the current time information, depicted in Figure 13.14. Followed by a recurrent layer, batch normalization and regularization are done to preclude overfitting and to speed up the training rate. Finally, classification is done with a particular activation function based on the output class.

![](img/efffc69cb8cda75bcf341884e3396898_307_0.png)

FIGURE 13.14 Recurrent neural network.

### 13.7.4 Deep Neural Networks (DNNs)

An intrusion detection system is the need of the hour in today’s world due to the rapid development of information technology. DNN takes on the major role in finding security breaches without accessing the information inside the packet, thus maintaining data privacy [23]. The model created by DNN includes multiple hidden layers, and the neurons in the layers are interconnected. Forward-propagation with the appropriate activation function for the perceptron is depicted in Figure 13.15.

![](img/efffc69cb8cda75bcf341884e3396898_308_0.png)

FIGURE 13.15 Deep neural network (DNN).

To produce the most accurate results, back-propagation with a suitable optimizer and loss function is used to adjust the weights and bias [22]. Here the classification can be binary classification, denoting normal and attack, or multiclassification, such as user to root attack, denial of service attack, remote to user attack, probe, and normal.

### 13.7.5 Generative Adversarial Networks (GANs)

The digital data available needs to be secured to protect it from unknown attacks. Many companies, healthcare organizations, and public institutions have a lot of secure data to be protected. GAN can generate new data that resembles the original data by which the original data can be safeguarded; a sample is shown in Figure 13.16. The new data generated by GAN has a high correlation with the original data, thus improving the security of the original data.

![](img/efffc69cb8cda75bcf341884e3396898_309_0.png)

FIGURE 13.16 Generative adversarial networks architecture.

Another application of GAN is steganography where the sensitive information is hidden inside the images. Also GAN is used to hide a grayscale image inside the color image with high security. Sensitive data can also be stored inside an image container more securely using deep convolutional generative adversarial networks and auxiliary classifier generative adversarial networks. Neural network (NN), combined with steganography called neural cryptography, plays a significant role in securing the information. Here synchronizing the output weights present in NN generates a secret key. PassGAN is used for quality password guesses [24].

### 13.7.6 Restricted Boltzmann Machine (RBM)

The exponential use of technologies in our daily lives has increased the volume of data exchange among people and organizations, leading to new and different attacks in the network. Many organizations have initiated security measures to protect their networks. The RBM algorithm is beneficial in different applications such as regression, dimensionality reduction, feature learning, classification, and many more. RBM comes with two biases: The forward pass is supported by a hidden bias, and the backward pass supported by visible layer’s bias for reconstruction. Here no two neurons on same layer are connected. It is said to be restricted because no intralayer connection or communication is present. Figure 13.17 shows the graphical depiction of RBM with an m visible and an n hidden node [25].

Here, there is no connection between visible and visible nodes or between hidden nodes; the only permissible connection is visible to hidden or hidden to visible.

![](img/efffc69cb8cda75bcf341884e3396898_310_0.png)

FIGURE 13.17 Graphical representation of RBM.

Each node represents a feature from the dataset that is multiplied with the weight and added with the bias passed through the activation function, giving the output of the particular node. Also, multiple inputs can be combined and given to one particular neuron by multiplying the multiple input with its weight, summing it up and adding the bias, and then sending it through the activation function to generate the output. Training makes it possible to produce a compact depiction of input. RBM helps in differentiating normal and anomalous traffic.

### 13.7.7 Deep Belief Network (DBN)

DBN is an unsupervised deep learning algorithm with a generative graphical model. This is a composite of stacked restricted Boltzmann machines, followed by a softmax classification layer or auto encoder with both a directed and an undirected graphical network. The parameters of RBM are trained by a contrastive divergence (CD) algorithm. Figure 13.18 shows the structure of DBN [32].

![](img/efffc69cb8cda75bcf341884e3396898_310_1.png)
