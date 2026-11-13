
Moreover, the mean threshold [49–51] is defined by choosing $t$ as the mean value of the distribution of pixel values. Analogously, the median threshold, as a special method of Doyle's $p$-tile method [166], is set so that 50 % of pixels lie in each of the two binary classes [49].

The use of those different thresholding techniques concerning carbon fiber reinforced polymers will be taken up again in the Methods (Chapter 3, Section 3.4.2.2 and Section 3.6).

## 2.4 Artificial intelligence

The term artificial intelligence describes the intelligence of machines or software. It is a field of study in computer science and its technologies have spread across various applications throughout industry, governments, science and entertainment. Initiated by Alan Turing in the 1950s [167], AI rose to its initial promise only in the last decade as large computational power and big data storage and handling possibilities emerged [168]. This led to the AI boom, sometimes called AI Spring [169], in the later 2010s and early 2020s.

The large field of AI is further differentiated. Machine learning (ML) is probably the largest sub-category [168]. It refers to algorithms that can automatically improve the execution of a specific task [170]. Hong et al. [168] emphasize that the major difference between conventional programming and machine learning programming is ML working through induction. In the former, a programmer has to formulate general rules and the algorithm is able to deduce the result for specific observations, while in ML the algorithm itself finds general rules from the given observations [168]. The programmer's work lies in the development of the structure and environment of the algorithm for it to reliably induce those rules. Either another subcategory of ML or a mixture of AI and ML concepts (depending on the definition), is the so-called deep learning (DL) [168]. Deep learning refers to processing the observations through ANNs that are inspired by biological neural networks. The adjective "deep" stresses the use of multiple layers in the network.

There is the further differentiation into *supervised* and *unsupervised* ML. The former denotes networks that work on input data that was labelled by a human, while the latter type signifies networks that have to find common patterns and make predictions without any other human guidance [170].

In the following, the general theoretical principles of ANN will be elaborated on, before specific types of those networks will be outlined.

### 2.4.1 Theoretical principles of ANNs

#### 2.4.1.1 Single layer perceptrons

The smallest sub-unit of an ANN is a so-called single layer perceptron (SLP). Based on the original neuron model by McCulloch and Pitts in 1943, it was first introduced as perceptron by Rosenblatt in 1957 and is a linear classifier whose structure resembles that of a biological neuron (cf. Figure 2.14). [171, 172]

![](img/332d06e0447dbfd85ea7d2fb553468f3_113_0.png)

**Figure 2.14:** Schematic depiction of a single layer perceptron as described by Rosenblatt [171]. Based on [173].

Different inputs \(\{x_1, x_2, ..., x_n\}\) (similar to the impulses collected by dendrites of a biological neuron) are weighted based on their relative importance by the weights \(\{w_1, w_2, ..., w_n\}\) and subsequently summed up by a linear aggregator. A lower threshold value _b_, also known as the bias, determines whether an output signal is afterwards triggered. The activation function σ(u) depends on the difference between \(b\) and the result of the linear aggregator, the activation potential \(u\). This results in the output signal \(y\) of the SLP

\(y = \sigma(u) = \sigma \left( \sum_{i=1}^n w_i x_i - b \right) .\) (2.90)

The activation function thereby restricts the possible output values to a set range. [174] Equation (2.90) can be simplified by adding a dummy input \(x_0 = 1\) and the corresponding weight \(w_0 = b\) to

\(y = \sigma \left( \sum_{i=0}^n w_i x_i \right) = \sigma(\boldsymbol{x} \cdot \boldsymbol{w}) = \sigma(\boldsymbol{w}^{\top}\boldsymbol{x}) ,\) (2.91)

which increases the vector dimensions of \(\boldsymbol{x}\) and \(\boldsymbol{w}\) by 1 [175].

There are many different possible activation functions including the step function, linear function, sigmoid function, tanh function or a rectified linear unit (ReLu) [174]. Assuming a simple bipolar step function for demonstration purposes, which is given by

\(y = \sigma(\boldsymbol{x} \cdot \boldsymbol{w}) = \left\{ \begin{array}{ l l } 1 & \text{if } \boldsymbol{w} \cdot \boldsymbol{x} > 0, \\ -1 & \text{if } \boldsymbol{w} \cdot \boldsymbol{x} \le 0, \end{array} \right.\) (2.92)

one gets a binary output \(y\) independent of the (possibly non-binary) input [174, 175]. If only two input values and weights were given, this would result in the following inequalities

\(w_1 x_1 + w_2 x_2 - b \ge 0,\) \(w_1 x_1 + w_2 x_2 - b < 0,\) (2.93)

which creates a linear boundary between two classes [174]. In case of more than two input and weight parameters, this approach has to be extended to a hyperplane defined by \( w \cdot x = 0 \) [176]. This function of SLP as classifier is shown in Figure 2.15.

![](img/332d06e0447dbfd85ea7d2fb553468f3_115_0.png)

**Figure 2.15:** Schematic two-dimensional illustration of a hyperplane (dashed blue line) separating two classes originating from the system of inequalities given by a SLP. Based on [176].

The perceptron learns by adjusting the weights when it has made wrong decisions. This updating or learning rule is a recursive algorithm. Suppose that the respective class label \( z_i \) of a given input value \( x_i \) is given by

\( z_i = \begin{cases} 1 & \text{if } x_i \in \text{ of the first class,} \\ -1 & \text{if } x_i \in \text{ of the second class.} \end{cases} \) (2.94)

For a set of p training samples \( (x_i, z_i) \ \forall \ i = 0, 1, ..., p \), then \( y = y(w) \) gives the (binary) prediction of \( z_i \) for a given \( x_i \) based on the current weights and bias. The change of the weights \( w_i \) is then defined as

\( w_i \rightarrow w_i + \Delta w_i, \) (2.95)

with

\(\Delta w_i = r_1(z_i - y_i)x_i.\)

This learning rule is also called *delta rule* and is a gradient descent algorithm for optimization. The parameter \(r_1 \in [0, 1]\) denotes the learning factor or more commonly known the *learning rate*. The convergence of this learning rule after a finite number of iterations was proven by Rosenblatt in the perceptron convergence theorem. [171, 175, 176]

#### 2.4.1.2 Multi-layer perceptron (MLP)

A standard neural network normally consists of multiple layers of perceptrons, more precisely an input layer, some number of hidden layers and an output layer; so at least three layers. The input layer is often not counted in the amount of layers as it performs no processing and only has a distribution function towards the next layer [177]. These kinds of neural networks are often referred to as "vanilla" neural networks emphasizing their simplicity and them being the first of their kind [178]. A simple fully connected MLP with one hidden layer can be seen schematically in Figure 2.16.

The input values \(\boldsymbol{x} = \{x_1, x_2, ..., x_n\}\) are often referred to as "features" in the context of neural networks making \(\boldsymbol{x}\) the feature vector [174]. Following, one or multiple layers of hidden nodes \(h_i\) process the input until it reaches the final output layer, where the results are given out in the output vector \(\boldsymbol{y}\). An activation function maps the weights to the following layer [179]. The name multi-layer perceptron is misleading or incorrect in that contrary to the step function used as activation function by the original perceptron, modern neural networks rely on nonlinear kinds of activation functions providing them the ability to distinguish data that is not linearly separable [180]. Different kinds of activation functions will be shortly outlined in Section 2.4.1.5. In this simple case, connections are only permitted between nodes in consecutive layers and in a forward direction, which is why they are also called *feedforward* networks [175].
