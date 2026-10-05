bias vector will be created and added to the output. But not least, it also applies to the output if the activation is not None.

# 3.6.3 Input layers

Input neurons in the input layer communicate with the embedding gate. Data is sent from the hidden layer to the output layer. Each neuron has an output, an activation function (which determines the output given the input), and weighted inputs (synapses).
Long-Term Memory (LSTM) Recurrent Neural Networks (RNNs) have emerged as efficient and scalable methods for a variety of sequential learning problems which is shown in Figure 2. They are essential for recognizing long-term temporary dependencies. LSTM is an RNN-inspired model [10] with control gates for flow between cells.

![](bbox=[0.313, 0.305, 0.683, 0.52])

Figure 2. Long Short-Term Memory (LSTM) Recurrent Neural Networks (RNNs).

# 3.7 Hyper parameter tuning

During hyper parameter tuning, learning rate and momentum were tweaked and checked up to 300 times the default value to obtain the optimum parameters for the model to predict bitcoin price [11].

# 3.8 Default parameter

Vocab_size=5000,Embedding_size=32,epochs=50,LearningRate=0.01,Decay_rate=learning_rate/epochs,Momentum=0.8 are considered as Default Parameters.

# 3.9 Optimum hyper parameter

Vocab_size=5000,Embedding_size=32,epochs=50,LearningRate=0.3,Decay_rate=learning_rate/epochs,Momentum=0.9 are considered as Optimum Hyper Parameters.

# 4 RESULTS AND DISCUSSION

The model was tested using a range of various sorts of data for testing purposes. It was the one with four LSTM layers of 64,32 units each, a dense layer on top of which we forecasted near time series of the column with a time step of 110 seconds.