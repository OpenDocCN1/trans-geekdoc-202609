
# MALWARE DETECTION IN DEEP LEARNING 275

- 1. Data acquisition: Preparing data and ghettoizing the case scenario based on the tasks and requirement. It is also called as data preprocessing.
2. Data collection: gathering and storing raw material in the form of datasets.
3. Stream processing system: extracting information from database using it for real-time application.
4. Data warehouse: storing huge amount of the data in this container has n number of data, such as information, images, and videos.
5. Data processing: cleaning, transformation and encoding actions are executed by executor.
6. Data modeling: algorithm and flowchart are executed by the programmer.
7. Execution: testing system, performance of system and decision of system are carried out.
8. Deployment: overall product is thrown out after all possibilities and testing is performed by the teams.

Machine is trained by using three algorithms:

- a. Supervised Learning:
It is used for mathematical model. Supervised learning is ML for acquiring the input relationship information and system based on given set of paired input training samples (Figure 13.9).

![](img/081dc7f102a3793cb08980a6e19b8f17_298_0.png)

Figure 13.9 Supervised learning [7].

(x1, y1) is a supervised training sample
x represents system inputs y represents system outputs
i indicates index of the training sample xi fed to the learning system
yi generates the output
Error signal is to use for adjusting the signal

# 276 CONVERGENCE OF DL IN CYBER-IoT SYSTEMS AND SECURITY

- b. Unsupervised Learning: Unsupervised learning is a second type that looks for earlier hidden patterns in a dataset with no pre-existing and with a minimum of human monitoring (Figure 13.10).

![](img/081dc7f102a3793cb08980a6e19b8f17_299_0.png)

Figure 13.10 Unsupervised learning [7].

- Example: Customer Segmentation
ni. Input data: customer segmentation
ii. Interpretation: analysis of the dataset to track and make strategies for market customer growth.
iii. Algorithm: clustering (finding the similarities between the data item), outlier detection (dataset search for any kind of dissimilarities and anomalies in the data), association rule mining (finds out the most frequently occurring item-sets). eveniv. Processing: execution of algorithm with good accuracy.
vv. Result: displaying output, schedule meeting with heads for verifying and validating end result.

- c. Reinforcement Learning:
Reinforcement learning is the area of ML that deals with sequential decision making [11]. It is used for classifying patterns in the data for tasks, such as data compression.

We need ML in following cases:

- 1. Human expertise is absent.
2. Human are unable to explain their expertise.
3. Solution changes with the time.
4. Problem size is too vast for our limited of reasoning capabilities.

## 13.2.2 Introduction to Deep Learning

Deep learning is a branch of ML based sets of procedures that crack to system top-level abstraction by using multiple processing. It terms covers particular approach to building and training neural networks (Figure 13.11).

# MALWARE DETECTION IN DEEP LEARNING 277

![](img/081dc7f102a3793cb08980a6e19b8f17_300_0.png)

The data are stored in array, which contains of pixel, audio and waveforms. Some operations are performed in execution (Fourier Transform, DIT, FFT). Output predicted by the executor (output is in the form of numbers).
According to the definition, it is considered as the application of multi-layer network with multiple neurons at each layer to perform tasks. System is trained using three methods in deep learning training dataset, validation dataset, test dataset.
It is also called as shallow network.

- 1. Input layer: It consists of raw material such as water, milk in tea.
2. Hidden layer: It is the layer between input and output layer called hidden layer
3. Activation function: Activation Function is a transformation
4. Output layer: Actual output is display with accurate input given to system.

We will discuss few types of architecture of deep learning as follows:

- 1. Auto-encoder: Auto-encoder makes target result set and get equal with the input values. The network attempts to restructure its input, which powers the hidden layer to study the finest demonstrations of the input. The hidden layer is used to explain a program, which aids to denote the input. It represents set of data using high dimensional its using its subtypes (de-noising auto encoder, Sparse auto encoder, Variation

278 CONVERGENCE OF DL In Cyber-IoT Systems and SECURITY

auto encoder, reactive auto-encoder). It is used in NLP and Complex data representation.

- 2. Convolutional neural networks (CNN): Basically, CNN first architecture was identifying the features such as edges, after recombination of some features these flow of data (convolutional, pooling and classification). It is used for document analysis and face recognition.

- 3. Deep stacking networks: DSN is created of mixture of elements which are fragment of the system and architecture. Individual element involves of input zone, hidden zone, and output zone. The information which these system holds a huge number of deep single networks where each network has its specific hidden layers.

- 4. Long short-term memory: LSTM uses a memory unit called cell which can store its value for enough time and gives it as a task of its feedback. This aids the unit to learn the earlier calculated value. The memory created of three ports called gates, which grips stream of data in the cell (first is input port which grips fresh data, second is port handles summarization of the fresh data, and third is output gate which holds the flow of information that is existing in the cell.

- 5. Recurrent neural network: It takes the earlier memory of input and mock-ups within the seconds. These networks can be changed, modified, and extended with usual backpropagation.

Some advance architecture of deep neural network is nowadays used:

- 1. Alex net: The architecture consists of convolutional layers, pooling layers, which are loaded on one another and then tracked by fully interlinked layers on the uppermost.

- 2. Google net: This architecture single layer handles many types of the feature extractors that benefit the network to perform better.

- 3. Res net: The residual units are located on single over the other and made positive and whole node to node network.

- 4. You only look once (YOLO): This architecture resolves image recognition problem, it is used for handling the real time issues.

# MALWARE DETECTION IN DEEP LEARNING 279

5. Generative Adversarial Networks: It is a special network architecture which creates fully new and diverse images which are not previously present in the vacant training dataset.

## 13.2.3 Detection Techniques Using Deep Learning

We have seen architectures of deep learning in Figure 13.11, which show how deep learning is extended its network. Especially newly architecture of deep learning is proving stronger and accurate results [8]. In recent years, which method is most used for malware detection using deep learning are listed:(Table 13.1) [1].

**Table 13.1** Deep learning methods for malware detection.

| Deep learning methods | Description |
|---|---|
| Deep Neural Network | Accuracy of detection is 95% and false rate is 0.1%. |
| CNN and LSTM | Used for spatial and temporal signals difficult of malware illustration. |
| Deep Learning | Mixture of static, dynamic malware analysis is used for recognition. |
| Deep Belief Network | It represent malware as opcode sequences and then apply DBN |
| Deep Learning (CNN) | Using image processing for malware detection which convert malware in greyscale binaries and train the CNN. |

Methodology for malware detection using CNN [8]:

- 1. Malware is unpacked
2. Executable file is stripped
3. API calls is extracted
4. Offered an extension by adding another step.
5. Various features are integrated through static static analysis (Capturing information from executables without running it) and dynamic analysis (running malware in isolated environment).
6. Most new malware is formed using previous malware changing some things in a code taking these as advantage using image processing techniques will detect malware. Here image processing steps is performed to detect malware.
i. Converting Malware binary to image
ii. Apply CNN to Malware image
