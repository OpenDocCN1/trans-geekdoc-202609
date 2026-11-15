
as time-series, language, audio, and text. Data in these domains are inherently ordered and context sensitive where later values depend on previous ones. The wiring for a Recurrent Neural Network allows for feedback in ways that make it possible to capture these temporal effects. We primarily see Recurrent Neural Network architectures applied in the time-series domains for applications.

A Recurrent Neural Network includes a feedback loop that it uses to learn from sequences, including sequences of varying lengths. Recurrent Neural Networks contain an extra parameter matrix for the connections between time-steps, which are used/trained to capture the temporal relationships in the data.

Recurrent Neural Networks are trained to generate sequences, in which the output at each time-step is based on both the current input and the input at all previous time steps.

## Sequences and Time-series Data

We find sequential data in many problem domains in industry for which our model needs to output a sequence of vectors:

- Image captioning
- Speech synthesis
- Music generation
- Playing video games
- Language modeling
- Character-level text generation models

In other domains, we need a sequence of input vectors:

- Time-series prediction
- Video analysis
- Music information retrieval

And then we have domains that require both a series of input and output vectors:

- Natural language translation
- Engaging in dialogue
- Robotic control

Recurrent Neural Networks contrast with other deep networks in what type of input they can model (nonfixed input):

- Nonfixed computation steps
- Nonfixed output size
- It can operate over sequences of vectors, such as frames of video

## Understanding Model Input and Output

Traditional machine learning operates on the concept of a single fixed-sized input vector. In traditional modeling activities, we typically would see an input-to-output relationship of fixed input size to fixed output size.

This is commonly the pattern for modeling in building classifiers for image classification or classifying columnar data.

Recurrent Neural Networks change this input dynamic to include multiple input vectors, one for each time-step, and each vector can have many columns. The following list gives examples of how Recurrent Neural Networks operate on sequences of input and output vectors:

- One-to-many: sequence output. For example, image captioning takes an image and outputs a sequence of words.

- Many-to-one: sequence input. For example, sentiment analysis where a given sentence is input.

- Many-to-many: For example, video classification: label each frame.

## 3D Volumetric Input

Input into Recurrent Neural Networks involves more dimensions than standard machine learning modeling input. This is similar conceptually to CNNs. We have three dimensions for the input:

- Mini-batch Size
- Number of columns in our vector per time-step
- Number of time-steps

![](img/c4a53cbbd40023d194b7887dddf3293b_166_0.png)

Mini-batch size is the number of input records (collections of time-series points for a single source entity) we want to model per batch. The number of columns matches up to the traditional feature column count found in a normal input vector. The number of time-steps is how we represent the change in the input vector over time. This is the time-series aspect to the input data. In the terminology from the previous section, we’d consider any time-step count above 1 to be “many-to-” in terms of input and output architecture.

## Uneven Time-series and Masking

The concept of time-steps in addition to features in our input vector.

![](img/c4a53cbbd40023d194b7887dddf3293b_167_0.png)

Every column value likely will not occur at every time-step, especially for the case in which we’re mixing descriptor data (e.g., columns from a static database table) with time-series data (e.g., measurements of an ICU patient’s heartrate every minute). For cases in which we have “jagged” time-step values, we need to use masking to let DL4J know where our real data is located in the vector.

![](img/c4a53cbbd40023d194b7887dddf3293b_167_1.png)

## 5.5.2 General Recurrent Neural Network Architecture

Recurrent Neural Networks are a superset of feed-forward neural networks but they add the concept of recurrent connections. These connections (or recurrent edges) span adjacent time-steps (e.g., a previous time-step), giving the model the concept of time. The conventional connections do not contain cycles in recurrent neural networks. However, recurrent connections can form cycles including connections back to the original neurons themselves at future time-steps.

## Recurrent Neural Networks Architecture and Time-steps

At each time-step of sending input through a recurrent network, nodes receiving input along recurrent edges receive input activations from the current input vector and from the hidden nodes in the network’s previous state.

The output is computed from the hidden state at the given time-step. The previous input vector at the previous time step can influence the current output at the current time-step through the recurrent connections.

We can chain layers of these specialized recurrent neurons together to build better models. We connect the output of the previous layer to the input of the next layer similar to how we’d connect feed-forward multilayer neural networks.

## LSTM Networks

LSTM networks are the most commonly used variation of Recurrent Neural Networks. LSTM networks were introduced in 1997 by Hochreiter and Schmidhuber.

The critical component of the LSTM is the memory cell and the gates (including the forget gate, but also the input gate).

The contents of the memory cell are modulated by the input gates and forget gates. 30 Assuming that both of these gates are closed, the contents of the memory cell will remain unmodified between one time-step and the next. The gating structure allows information to be retained across many time-steps, and consequently also allows gradients to flow across many time-steps. This allows the LSTM model to overcome the vanishing gradient problem that occurs with most Recurrent Neural Network models.

## Properties of LSTM networks

LSTMs are known for the following:

- Better update equations
- Better back-propagation

Here are some example use cases of LSTMs:

- Generating sentences (e.g., character-level language models)
- Classifying time-series
- Speech recognition
- Handwriting recognition
- Polyphonic music modeling

LSTM and Bidirectional Recurrent Neural Networks (BRNN) architectures have shown industry-leading benchmarks in recent years on tasks such as the following:

- Image captioning
- Language translation
- Handwriting recognition

LSTM networks consist of many connected LSTM cells and perform well in how efficient they are during learning.

## LSTM Network Architecture

To better understand the complex arrangement of connections between units and layers in LSTM networks, let's build on some earlier concepts.

![](img/c4a53cbbd40023d194b7887dddf3293b_169_0.png)

If we were to show each layer from the network shown in Figure as a single node in a flattened representation.

![](img/c4a53cbbd40023d194b7887dddf3293b_170_0.png)

With Recurrent Neural Networks, we introduce the idea of a type of connection that connects the output of a hidden-layer neuron as an input to the same hidden-layer neuron. With this recurrent connection, we can take input from the previous time-step into the neuron as part of the incoming information.

![](img/c4a53cbbd40023d194b7887dddf3293b_170_1.png)

## REFERENCES

- 1. Al-Abaid, Shaimaa Abbas. “Artificial Neural Network Based Image Encryption Technique.” Journal of Advanced Research in Dynamical and Control Systems 12, SP3 (February 28, 2020): 1184–89.
- 2. Al-Rawi, Kamal R., and Consuelo Gonzalo. “Adaptive Pointing Theory (APT) Artificial Neural Network.” International Journal of Computer and Communication Engineering 3, no. 3 (2014): 212–15.
- 3. Bengio, Y., LeCun, Y., Hinton, G. (2015). Deep Learning. Nature 521: 436-44.
- 4. Bernard, Etienne (2021). Introduction to Machine Learning. Wolfram Media Inc. p. 9.
- 5. CVS, Rajesh, and Nadikoppula Pardhasaradhi. “Analysis of Artificial Neural-Network.” International Journal of Trend in
