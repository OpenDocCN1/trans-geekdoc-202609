
## 5.2.2.2 Convolutional Neural Networks (CNNs)

CNN—used for the recognition of objects and classification of images—is a network architecture for DL. Evolving from the traditional ANNs, a CNN is a network of convolutional layers. These layers are used for detection and extraction of various features from the input data, using small filters (kernels) while processing the input image or the previous layer’s feature map. At each location, the filter computes “a dot product between itself and the corresponding region of the input” [5]. They are fully connected and each layer “generates a successive abstraction of the input data with a high level, called a feature map, which saves essential unique information” [13]. CNN is a kind of DL model used for object recognition and image classification. They extract several features from the input data (information) by using filters, resulting in a feature map. A feature map, which is an output of a convolutional layer, signifies specific features in the input image or a previous layer’s feature map [14]. Feature maps are also known as activation maps or convolutional feature maps. They are defined as “a two-dimensional array or grid of numbers resulting from the application of convolutional filters (also called kernels) to an input image or a previous layer’s feature map. Feature maps play a crucial role in the CNN architecture and are responsible for detecting different visual features or patterns in the input data” [15]. CNNs are tasked with image and video recognition and are able to learn automatically features from the images, making them suitable for tasks like image classification, object detection, and image segmentation [1].

In CNNs, an algorithm is trained on a labeled dataset and works through supervised learning. Here, convolution means a “process of applying a filter or a kernel to an input or feature map.” A filter or kernel is “a small matrix of weights that slides over the input image or feature map and performs a dot product operation at each position” [16]. CNNs perform amazingly by using a very deep hierarchy of layers. They consist of two main types of layers; one layer for feature extraction and the other for classification. The feature extraction layers are convolution layers and max-pooling layers [15].

## 5.2.2.3 Recurrent Neural Networks (RNNs)

RNN, a deep neural network, is designed for processing sequential or time series data. In this network, output of one step acts as input for another retaining the information from the previous inputs. Its application may be in time-series prediction, NLP, speech recognition, and image and video processing [17]. In it “the output of recurrent neural networks depends on the prior elements within the sequence. While future events would also be helpful in determining the output of a given sequence, unidirectional recurrent neural networks cannot account for these events in their predictions” [18]. They are able to maintain an internal state capturing the information about the previous inputs, which is suitable for tasks like speech recognition, NLP, and language translation [1].

## 5.2.2.4 Recursive Neural Networks (RvNNs)

RvNNs are a specialized DL, having the ability to function on hierarchical data like parse trees in NLP, or molecular structures in chemistry. It can handle tree-like structure inputs very effectively by processing the input data recursively, blending “information from child nodes to form representations for parent nodes;” here “the tree structure means combining child nodes and producing parent nodes, and each child-parent bond has a weight matrix, and similar children have the same weights.” It is mainly used in NLP tasks like sentiment analysis, etc. The capacity of RvNNs to capture recursive, nested relationships makes it a powerful tool [19].

## 5.3 Applications of Deep Learning

DL AI can be used for (a) supervised; (b) unsupervised; and (c) reinforcement ML.

- a) **Supervised Machine Learning:** It is a technique wherein the neural network learns to predict or classify data depending on the labeled datasets. “Deep learning algorithms like Recurrent neural networks, Convolutional neural networks, perform supervisory task like image classifications and recognition, language translations sentiment analysis, etc.”
- b) **Unsupervised Machine Learning:** It is a technique that enables the neural network to learn and discover the patterns, and cluster the dataset relying upon unlabeled datasets. “Deep learning algorithms like autoencoders and generative models are used for unsupervised tasks like clustering, dimensionality reduction, and anomaly detection.”
- c) **Reinforcement Machine Learning:** It is a technique that enables an agent to learn to make decisions in an environment to maximize a reward signal. It can be used for learning a set of actions, or policies, which maximizes the cumulative reward over time. “Deep reinforcement learning algorithms like Deep Q networks and Deep Deterministic Policy Gradient (DDPG) are used to reinforce tasks like robotics and game playing etc.”

The primary applications of DLAI can be categorized into computer vision, NLP, and reinforcement learning [1].

1) Computer Vision—In computer vision, DL AI models enable machines to understand and identify visual data that include the following:

- object detection and recognition to perform tasks like surveillance, self-driving cars, and robotics;
- image classification to classify and categorize images such as plants, animals, and buildings, applicable in quality control, medical imaging, and image retrieval;
- image segmentation to identify specific features in the images.

2) Natural language processing (NLP)—DL enables the machines to generate human language, it may be automatic text generation, language translation, sentiment analysis (customer service, political analysis, and social media monitoring), or speech recognition (voice search, speech-to-text conversion, and voice-controlled devices).

3) Reinforcement learning—DL enables machines to work as training agents like taking action in a situation to maximize a reward, it may include the following:

- game playing (deep reinforcement learning models have beaten human experts in games like Chess, Go, and Atari),
- robotics (deep reinforcement learning models train robots to perform complex activities like navigation, grasping objects, and manipulation), and
- control systems (deep reinforcement learning models control complex systems such as traffic management, power grids, and supply chain optimization)

Advances in DL have engendered the emergence of a system that is capable of producing meaningful content. The systems so far were able to classify, translate, or comprehend input data; now with the DL they have become generative and are called generative artificial neural networks (GANNS). ChatGPT (Chat Generative Pre-trained Transformer) is an illustration of a generative language model [7].

## 5.4 Intrusion Detection

ICT (information and communications technology) systems and networks deal with various sensitive data of users who are prone to various attacks—both internal and external intruders. These attacks may be manual or machine-generated, are becoming more diverse, and are gradually advancing in the dark, resulting in data breaches that go undetected. For instance, a data breach caused a $350 M loss to Yahoo and an estimated $70 M loss occurred because of the Bitcoin breach. Such cyberattacks backed by sophisticated algorithms are evolving constantly with the advancement of software, hardware, and network topologies including the current developments in the internet of things (IoT). Malicious cyberattacks pose a serious threat to network security that requires a reliable, flexible, and novel IDS [10]. Over the years the exponential use of networks and computer systems has resulted in increased intrusion and malicious attacks raising serious concerns about computer security policies—confidentiality, integrity, and
