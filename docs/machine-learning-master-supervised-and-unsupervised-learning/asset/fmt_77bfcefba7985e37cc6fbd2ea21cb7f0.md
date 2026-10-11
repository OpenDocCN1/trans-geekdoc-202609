
# Backpropagation Algorithm

The backpropagation algorithm is used to effectively train a neural network using a method known as chain rule. Backpropagation, in a nutshell, performs a backward pass through a network after each forward pass while adjusting the model's parameters (weights and biases). Backpropagation is an abbreviation for "backward propagation of errors". It is a common technique for training artificial neural networks. This method is useful for calculating the gradient of a loss function for the network's weights.

The essence of neural net training is backpropagation. It is a technique for fine-tuning the weights of a neural network based on the error rate obtained in the previous epoch (i.e., iteration). By fine-tuning the weights, you can reduce error rates and make the model more reliable by increasing its generalization.

## Algorithm

Consider the following Figure 6.11 for the backpropagation algorithm working as shown follows:

![](image-vszx09uq.jpg)
**Figure 6.11: Backpropagation algorithm working**

1.  **Step 1:** Inputs `X` arrive through the preconnected path.
2.  **Step 2:** Input is modelled using real weights `W`. The weights are usually randomly selected.
3.  **Step 3:** Calculate the output for every neuron from the input layer to the hidden layers, to the output layer.
4.  **Step 4:** Calculate the error in the outputs.
    `ErrorB = Actual Output – Desired Output`
5.  **Step 5:** Travel back from the output layer to the hidden layer to adjust the weights such that the error is decreased.
6.  **Step 6:** Repeat the process (from steps 1 to 5) until the desired output is achieved.

## Types of Backpropagation Networks

There are two types of Backpropagation Networks:

*   **Static backpropagation:** It is a type of backpropagation network that generates a mapping of a static input to a static output. It can be used to solve static classification problems such as optical character recognition.
*   **Recurrent Backpropagation:** Recurrent backpropagation is used until a fixed value is reached. The error is then computed and propagated backwards.

The main difference between these two methods is that in static backpropagation, the mapping is fast, whereas in recurrent backpropagation, the mapping is non-static.

## Advantages

The following are the advantages of the Backpropagation Networks:

*   It is simple, fast, and easy to program.
*   Apart from the numbers of input, there are no parameters to tune.
*   It is a standard method that generally works well.
*   It is a versatile method because it does not necessitate prior knowledge of the network.

## Disadvantages

The following are the disadvantages of the Backpropagation Networks:

*   The actual performance is determined by the data input.
*   Backpropagation is extremely sensitive to noisy data.
*   Backpropagation must be done using a matrix-based approach rather than a mini-batch approach.

# Introduction to Deep Learning

Deep learning algorithms employ a technique known as a neural network to discover relationships between a set of inputs and outputs.

Machine learning has a subdomain called **deep learning**. Deep learning algorithms can self-learn hidden patterns within data to make predictions using accelerated computational power and large data sets. In essence, deep learning is a subset of machine learning (see Figure 6.12) that is trained on large amounts of data and involves many computational units working together to make predictions.

The term refers to the creation of deep neural networks. This refers to a neural network with many layers. By adding more weights and biases, the neural network improves its capabilities to predict more complex functions.

Deep learning is a subset of machine learning, which is a subset of artificial intelligence. Individual definitions are as follows:

*   **Artificial Intelligence:** The broad mandate of artificial intelligence is to create machines that can think intelligently.
*   **Machine Learning:** Machine learning employs algorithms to extract insights from data.
*   **Deep Learning:** Deep learning employs a specific algorithm known as a Neural Network.

## How do deep learning algorithms “learn”?

The following Figure 6.12 depicts the concept of the deep learning algorithm:

![](image-0ebwx50y.jpg)
**Figure 6.12: Deep Learning Algorithms concept**

A neural network is made up of input, hidden, and output layers, all of which are made up of neurons. Input layers receive a numerical representation of data (for example, images with pixel specs), output layers produce predictions, and hidden layers are correlated with the majority of the computation.

## Difference between Machine Learning and Deep Learning

To grasp the difference between machine learning and deep learning, we must first understand the relationship between deep learning and machine learning. This relationship is best represented by an example shown in Figure 6.13. In machine learning, feature extraction and classification are applied separately to get the output, whereas in deep learning feature extraction and classification are applied together to get the output. By using deep learning, the complexity reduces to achieve the results faster.

![](image-mrime246.jpg)
**Figure 6.13: Machine Learning vs Deep Learning**

The following Table 6.2 shows the difference between Machine Learning and Deep Learning.

**Table 6.2: Difference between Machine Learning and Deep Learning**

*(Note: The original text contained placeholder text "Learning." repeated extensively instead of the actual table content. This has been noted but the table structure is preserved as a header.)*

## Importance of Deep Learning

Deep learning is significant because we have achieved meaningful and useful accuracy on tasks that matter. For decades, machine learning has been used for image and text classification, but it has struggled to cross the threshold of accuracy that algorithms require to work in business settings. Deep learning is finally allowing us to cross that line in places where we previously could not as shown in Figure 6.14.

![](image-79gp13dv.jpg)
**Figure 6.14: Comparison of deep learning and older learning algorithms**

The following are some of the real-time examples:

*   **Computer vision** is an excellent example of a task that deep learning has rendered feasible for business applications. Deep learning is not only better than any other traditional algorithm for classifying and labelling images; it is also beginning to outperform actual humans.
*   Using deep learning, Facebook has already had remarkable success identifying facial expressions in photographs. It's not just a minor improvement; it's a huge success.
*   Deep learning is already being used by Google to manage the energy at the company's data centers. Deep learning has also had an impact on speech recognition.
*   Deep learning is significant because it brings previously inaccessible workloads into the purview of machine learning. We are just beginning to understand how developers and business leaders can use machine learning to drive business outcomes and having more available tasks at your fingertips as a result of deep learning will transform the economy for decades to come.

### Advantages

*   Best in-class performance
*   Reduces the need for feature engineering
*   Cuts out unnecessary expenses
*   Identifies minor defects

### Disadvantages

*   Massive quantity of data is required
*   Training is computationally expensive
*   There is no solid theoretical foundation
