relative importance in the corpus. TF-IDF is a more advanced technique that aims to weight words based on their importance. It considers both the frequency of a word in a document and the rarity of the word across all documents. The term frequency (TF) of a word $w$ in document $d$ is defined as:

\(\text{TF}(w, d) = \frac{\text{count}(w, d)}{\text{total number of words in } d}\)

The inverse document frequency (IDF) is given by:

\(\text{IDF}(w) = \log \left( \frac{N}{\text{DF}(w)} \right)\)

where $N$ is the total number of documents and $\text{DF}(w)$ is the number of documents containing the word $w$. The TF-IDF score is the product of these two:

\(\text{TF-IDF}(w, d) = \text{TF}(w, d) \cdot \text{IDF}(w)\)

There are several machine learning models that can be used for text classification, ranging from simpler models to more complex ones. A common approach to text classification is to use a linear model such as logistic regression or linear support vector machines (SVM). Given a feature vector \(\mathbf{x}_i\) for document $i$, the prediction of the class label $y_i$ can be made as:

\(\hat{y}_i = \sigma(\mathbf{w}^T \mathbf{x}_i + b)\)

where \(\sigma\) is the sigmoid function for binary classification, and \(\mathbf{w}\) and $b$ are the weight vector and bias term, respectively. The model parameters \(\mathbf{w}\) and $b$ are learned by minimizing a loss function, such as the binary cross-entropy loss. More complex models, such as *Neural Networks (NN)*, involve deeper mathematical formulations. In a typical feedforward neural network, the goal is to learn a set of parameters that map an input vector \(\mathbf{x}_i\) to an output label $y_i$. The network consists of multiple layers of interconnected neurons, each of which applies a non-linear transformation to the input. Given an input vector \(\mathbf{x}_i\), the output of the network is computed as:

\(\mathbf{h}_i^{(l)} = \sigma(\mathbf{W}^{(l)}\mathbf{h}_i^{(l-1)} + \mathbf{b}^{(l)})\)

where \(\mathbf{h}_i^{(l)}\) is the activation of layer $l$, \(\sigma\) is the activation function (e.g., ReLU, sigmoid, or tanh), \(\mathbf{W}^{(l)}\) is the weight matrix, and \(\mathbf{b}^{(l)}\) is the bias term for layer $l$. The input to the network is passed through several hidden layers before producing the final classification output. The output layer typically applies a *softmax* function to obtain a probability distribution over the possible classes:

\(P(y_c|\mathbf{x}_i) = \frac{\exp(\mathbf{W}_c^T \mathbf{h}_i + b_c)}{\sum_{c'} \exp(\mathbf{W}_{c'}^T \mathbf{h}_i + b_{c'})}\)

where \(\mathbf{W}_c\) and $b_c$ are the weights and bias for class $c$, and \(\mathbf{h}_i\) is the output of the last hidden layer. The network is trained by minimizing a *cross-entropy loss function*:

\(\mathcal{L}(\mathbf{W}, \mathbf{b}) = - \sum_{c=1}^C y_{i,c} \log P(y_c|\mathbf{x}_i)\)

where $y_{i,c}$ is the one-hot encoded label for class $c$, and the goal is to minimize the difference between the predicted probability distribution and the true class distribution. Throughout the entire process, *optimization* plays a crucial role in fine-tuning model parameters to minimize classification errors. Common optimization techniques include *stochastic gradient descent (SGD)* and its variants, such as *Adam* and *RMSProp*, which update model parameters iteratively based on the gradient of the loss function with respect to the parameters. Given the loss function \(\mathcal{L}(\theta)\) parameterized by \(\theta\), the gradient of the loss with respect to a parameter \(\theta_i\) is computed as:

\(\frac{\partial \mathcal{L}(\theta)}{\partial \theta_i}\)