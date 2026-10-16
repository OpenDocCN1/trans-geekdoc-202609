
## 5
## Intrusion Detection Through Deep Learning: Emerging Trends and Challenges

Achyutananda Mishra

School of Law, Christ University, Bangalore, Karnataka, India

## 5.1 Introduction

Internet technology has brought the world closer than ever seamlessly connecting all parts of the world. Its increasing use has exposed the world to cyberattacks (malicious attacks)—manual or machine-generated—compromising the data and system/network security of individuals and institutions. Malicious cyberattacks are a serious security threat; malware attacks are dynamic in nature; they keep changing so does their methodology of attacking [1]. Cybercrime is on the rise, cybercriminals operate internationally with ease disrupting businesses and services, and malware is intentionally created, compromising the security of computer systems [2].

The intrusion detection system (IDS) has emerged as a network security tool to monitor computer networks or systems for malicious attacks and detect intrusion. It can be a network intrusion detection system (NIDS), a host intrusion detection system (HIDS), or a cloud intrusion detection system. IDSs commonly employ techniques like signature-based detection, anomaly-based detection, and stateful protocol analysis. It is a software that observes network traffic to detect intrusion, and if it detects any unusual activity or policy violation, then it immediately sends an alert or blocks it. It is built on a predictive model (a classifier) to distinguish between “bad connections” (intrusion/attacks) and “good (normal) connections.” These techniques discover algorithms permitting machines to learn without human intervention.

Deep learning is a breakthrough technology transforming various domains like computer vision, autonomous driving, healthcare, and finance. Deep learning (DL)—a cutting-edge and revolutionizing technology—brings substantial transformation to the IDS; it enables machines to understand, learn, and interact with data. It is a branch of machine learning based on artificial neural network architecture—that simulates the learning mechanism of biological organisms—and the complex model and an advanced subset of machine learning algorithms to overcome a few shallow networks’ limitations. DL artificial intelligence (AI) mimics the innate neural network embedded in the human brain, enabling computers to discover patterns automatically and arrive at decisions from a vast amount of unstructured data. It can be supervised learning and unsupervised learning. In supervised learning the machine is trained with labeled data whereas in unsupervised learning the machine self-learns. Supervised learning can be a convolutional neural network (CNN) or a recurrent neural network (RNN), and unsupervised can be an autoencoder (AE), and deep belief network (DBN). It has a lot of potential to shape the future of the planet.

## 5.2 Deep Learning

DL is a branch of machine learning (ML). It works on an artificial neural network (ANN) architecture—a network constituted in line with the structural and operational principles of human neurons. These are also known as neural nets or neural networks, and they employ layers of interconnected nodes called neurons as shown in Fig. 5.1. Such a network of neurons processes and learns from the data injected into it. Artificial neurons, known as units, are found throughout ANNs. An ANN has three layers namely (i) input layer, (ii) output layer, and (iii) hidden layers [1]. ANNs are inspired by the “nervous system of living beings,” which have the ability of acquiring and maintaining information-based knowledge. It “can be defined as a set of processing units, represented by artificial neurons, interlinked by a lot of interconnections (artificial synapses), implemented by vectors and matrices of synaptic weights” [3].

Neural network architecture

![](img/a13b588839130d750aecd8a32b6143d9_139_0.png)

Figure 5.1 Neural network architecture. Source: [12] / Neural Network Architecture: Types, Components & Key Algorithms, 2025 / upGrad Education Private Limited / https://www.upgrad.com/blog/neural-network-architecture-components-algorithms/, last accessed on 21 April 2025.

ANNs are well-known ML techniques that mimic the mechanism of learning in living organisms [4]. According to Arthur Samuel, ML is a field of study in which algorithms infer, from the input data, how to perform a specific task, without being specifically programmed for the task [5]. ML—a subdomain of AI that refers to machines or systems resembling human intelligence—emphasizes the development of a system (built upon data) that learns or improves performance. It is a data-driven technology that works on large amounts of data—which is crucial for ML—and helps organizations make better decisions. It identifies various patterns on available data [2].

ML empowers the computer with the capability to learn without being programmed explicitly. It is a system wherein the machines/computers learn models without human supervision—known as unsupervised learning where “algorithms are tasked with finding patterns and relationships within the data without any prior knowledge of the data’s meaning.” The purpose of such a process is to understand the structure beneath the data, and analyze and cluster datasets with the help of ML algorithms that help find hidden patterns and data [2].

DL is a complex subnetwork of ML that can learn hierarchical feature representations and hidden sequential relationships bypassing the TCP/IP (Transmission Control Protocol/Internet Protocol—a fundamental framework for networking) information onto several hidden layers. It has achieved substantial results in long-standing AI tasks in the fields of speech recognition, image processing, natural language processing (NLP), and many others [6].

The idea of DL is rooted in ML research starting from the mid-1940s and early stages of cybernetics to the contemporary research on AI and neural networks in the brain. DL refers to attempts to develop AI in machines to learn from experience and operate in terms of conceptual hierarchy. It means multiple singular experiences are logically linked together, revealing overarching dimensions that were hidden behind these singularities. It creates connections between different fields of knowledge like the neurons do in the brain [7]. In DL techniques, which are a subset of ML, the algorithm interprets data like humans do by using ANNs; for example, virtual assistants, remote switches, automated cars, voice recognition, and personalized e-commerce recommendations are some of its key features [8].

### 5.2.1 Neural Network Architectures

Neural networks are a well-known subset of ML algorithms, which are inspired by the human brain. Here biological neurons (nerve cells) respond to the activation of other neurons that they are connected to [9].

A deep neural network consists of an input layer and one or more hidden layers connected to each other. Each neuron in the network receives input from the previous connected layer of neurons or the input layer; the output generated by one neuron becomes the input for other neurons in the next layer of the network; and this continues until the final layer produces the output of the network. The neural network, which exists in layers, transforms the input data that exists in a series of nonlinear transformations and allows the network to learn patterns and complex representations of the input data [1].

A neural network architecture characterizes the structure and organization of an ANN, which is a computational model (artificial) based on the human brain. This explains the process of data flow through the network, connectivity of artificial neurons (units), and the learning of the network to make predictions. The ANN architecture symbolizes the structural arrangement of nodes (neurons) and the multiple layers that define how an ANN processes and learns from data. The design of the ANN influences its ability to learn complex patterns and perform tasks efficiently. [10].

The key components of a neural network architecture are as follows [11]:

- a) Layers—layers of neurons, i.e., input layers, hidden layers, and output layers.
- b) Neurons (nodes)—basic computational units that perform a weighted sum of their inputs, apply a bias, and pass the result through an activation function.
- c) Weights and biases—weights constitute the strength of the connections among neurons and biases allow neurons to predict even when all inputs are zero.
- d) Activation function—nonlinear functions (like ReLU and sigmoid) are used to introduce nonlinearity into the network, empowering it to model complex relationships.

### 5.2.2 Types of Neural Networks

The most widely used models in DL are (i) Feed-forward neural networks (FNNs), (ii) convolutional neural networks (CNNs), and (iii) recurrent neural networks (RNNs).

### 5.2.2.1 Feed-forward Neural Networks (FNNs)

They are the simplest type of ANN with a linear flow of information through the network where data flows from the input layer to the output layer without any cycles or loops. Under these networks, neurons are interconnected and arranged in layers, with each layer fully connected to the next. They are being used widely for tasks such as image classification, speech recognition, and NLP [1, 11].
