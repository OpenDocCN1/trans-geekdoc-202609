
| Year | Event |
| :--- | :--- |
| 2012 | In its “cat experiment” `Google Brain` using unsupervised learning, a convolutional neural net given unlabeled data needed to find recurring patterns. |
| 2014 | Ian Goodfellow proposed a generative adversarial neural network (GAN) in which two networks compete against each other in a game. |
| 2016 | `AlphaGo`, a neural network based computer program, mastered the complex game Go and beat a professional Go player. |

## 15.4 Deep Learning in Action

Aside from your favorite music streaming service suggesting tunes you might enjoy, how is deep learning impacting people’s lives? As it turns out, deep learning is finding its way into applications of all sizes. Anyone using Facebook cannot help but notice that the social platform commonly identifies and tags your friends when you upload new photos. Digital assistants like `Siri`, `Cortana`, `Alexa`, and `Google Now` use deep learning for natural language processing and speech recognition. Skype translates spoken conversations in real time. Many email platforms have become adept at identifying spam messages before they even reach the inbox. PayPal has implemented deep learning to prevent fraudulent payments. Apps like `CamFind` allow users to take a picture of any object and, using mobile visual search technology, discover what the object is.

`Google`, in particular, is leveraging deep learning to deliver solutions. `Google Deepmind`’s `AlphaGo` computer program recently defeated standing champions at the game of Go. `DeepMind`’s `WaveNet` can generate speech mimicking human voice that sounds more natural than speech systems presently on the market. `Google Translate` is using deep learning and image recognition to translate voice and written languages. `Google Planet` can identify where any photo was taken. `Google` developed the deep learning software database `Tensorflow` to help produce AI applications.

Deep learning is only in its infancy and, in the decades to come, will transform society. Self-driving cars are being tested worldwide; the complex layer of neural networks is being trained to determine objects to avoid, recognize traffic lights, and know when to adjust speed. Neural networks are becoming adept at forecasting everything from stock prices to the weather. Consider the value of digital assistants who can recommend when to sell shares or when to evacuate ahead of a hurricane. Deep learning applications will even save lives as they develop the ability to design evidence-based treatment plans for medical patients and help detect cancers early.

Now, as you have clearly understood what deep learning is and want to step up in this cutting-edge technology, you must know the career prospects.

### 15.4.1 Applications

1.  **Automatic text generation**: A corpus of text is learned, and from this model new text is generated, word by word or character by character. Then this model is capable of learning how to spell, punctuate, and form sentences, or it may even capture the style.
2.  **Health care**: Helps in diagnosing various diseases and treating them.
3.  **Automatic machine translation**: Certain words, sentences, or phrases in one language are transformed into another language (deep learning is achieving top results in the areas of text and images).
4.  **Image recognition**: Recognizes and identifies peoples and objects in images as well as to understand content and context. This area is already being used in gaming, retail, tourism, and so on.
5.  **Predicting earthquakes**: Teaches a computer to perform viscoelastic computations, which are used in predicting earthquakes.

### 15.4.2 Differences Between Machine Learning and Deep Learning

Knowing the differences between machine learning and deep learning techniques is very important and [Table 15.2](#ch15.xhtml#table15_2) shows the comparison between machine learning and deep learning techniques.

[Table 15.2 Comparison Between Machine Learning and Deep Learning](#ch15.xhtml#R_table15_2)

| Machine Learning | Deep Learning |
| :--- | :--- |
| Works on small amount of data set for accuracy | Works on large data sets. |
| Dependent on low-end machine | Heavily dependent on high-end machine |
| Divides the tasks into subtasks, solves them individually and finally combines the results | Solves problem end to end |
| Takes less time to train | Takes longer time to train |
| Testing time may increase | Less time to test the data |

Understanding the mathematics behind neural networks and deep learning becomes essential to know how and why they work.

## 15.5 Neural Networks

Neural networks are networks of interconnected neurons, for example interconnection of neurons in human brains. Artificial neural networks are highly connected to other neurons and perform computations by combining signals from other neurons. Outputs of these computations may be transmitted to one or more other neurons. The neurons are connected together in a specific way to perform a particular task.

A neural network is a function. It consists basically of (1) neurons, which pass input values through functions and output the result, and (2) weights, which carry values (real-number) between neurons. Neurons can be categorized into layers: (1) input layer, (2) hidden layer, and (3) output layer.

### 15.5.1 Basic Components of Biological Neurons

The human nervous system can be divided into three stages as shown in [Figure 15.1](#ch15.xhtml#fig15_1).

![Figure 15.1 Stages of human nervous system.](images/fig15_1_B.jpg)

*Figure 15.1 Stages of human nervous system.*

1.  **Receptors**: Receptors convert stimuli from the external environment into electrical impulses. The best example is the rods and cones of eyes. Pain, touch, hot, and cold receptors of skin are another example for receptors.
2.  **Neural net**: Neural nets receive information, process it, and make appropriate decisions. The brain is a neural net.
3.  **Effectors**: Effectors convert electrical impulses generated by the neural net (brain) into responses to the external environment. Examples of effectors are muscles and glands and speech generators.

The basic components of a biological neuron as given in [Figure 15.2](#ch15.xhtml#fig15_2) are (1) cell body (soma), which processes the incoming activations and converts them into output activations; (2) the neuron nucleus, which contains the genetic material (`DNA`); (3) dendrites, which form a fine filamentary bush, each fiber thinner than an axon; (4) the axon, a long, thin cylinder carrying impulses from the soma to other cells; and (5) synapses, the junctions that allow signal transmission between the axons and dendrites.

![Figure 15.2 Basic components of a biological neuron.](images/fig15_2_B.jpg)

*Figure 15.2 Basic components of a biological neuron.*

Computation in biological neurons happens as follows: (1) Incoming signals from synapses are summed up at the soma, and (2) on crossing a threshold, the cell fires, generating an action potential in the axon hillock region.

#### 15.5.1.1 Perceptrons

`Perceptrons`, invented by Frank Rosenblatt in 1958, are the simplest neural network that consists of `n` number of inputs, only one neuron, and one output, where `n` is the number of features of our data set as shown in [Figure 15.3](#ch15.xhtml#fig15_3). The process of passing the data through the neural network, known as `Forward propagation`, is explained in the following three steps.

![Figure 15.3 Single layer perceptron.](images/fig15_3_B.jpg)

*Figure 15.3 Single layer perceptron.*
