+   - Convolutional Neural Networks (CNN)
+   - Long Short-Term Memory (LSTM)
+   - Deep Belief Network (DBN)
+   - Rectified Linear Unit (ReLU)
+   - Generative Adversarial Network (GAN)

# McCulloch and Pitts network

It is well known that the most important unit of the deep neural network is known as the perceptron or artificial neuron. However, the actual first step in the direction of the perceptron, which we use nowadays, was actually taken by McCulloch and Pitts in 1943 by impersonating the functionality of the biological neuron.

In a biological neuron, the term dendrites are the segments of the neuron that conduct electrical messages for the cell to be active. Soma or cell body is where the signals from the dendrites are joined and passed on to other cells. Figure 3.5 shows McCulloch and Pitts neural network. Principally, a neuron or node takes a signal (input) in the dendrite, then further processes it like the CPU in the soma and passes the produced output using a cable-like structure to other connected neurons (axon) to synapse to the other neuron’s dendrite:

![](bbox=[0.19, 0.53, 0.82, 0.755])

Figure 3.5: McCulloch and Pitts neural network

Our sense organs interact with the outer world and send visual and sound information to the neurons. Let us say you are watching different objects in your surroundings, such as your friends, cars, birds, and so on. Then, the information your brain receives is taken in by the laugh or not set of neurons, which helps you to make a decision on whether to laugh or not. Each neuron gets fired /activated only when their respective criterion (more on this later) is met as follows.