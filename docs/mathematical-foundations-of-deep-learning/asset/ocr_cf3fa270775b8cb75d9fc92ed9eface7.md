# ## 5.4 Loss Functions

In neural networks, the **loss function** is a crucial mathematical tool that quantifies the difference between the predicted output of the model and the true output or target. Let **x**_<sub>i</sub>_ be the input vector and **y**_<sub>i</sub>_ the corresponding target vector for the _i_-th training example. The network, parameterized by weights **W**, generates a prediction denoted as \(\hat{\mathbf{y}}_i = f(\mathbf{x}_i; \mathbf{W})\), where \(f(\mathbf{x}_i; \mathbf{W})\) represents the model's output. The objective of training the neural network is to minimize the discrepancy between the predicted output \(\hat{\mathbf{y}}_i\) and the true label **y**_<sub>i</sub>_ across all training examples, effectively learning the mapping function from inputs to outputs. A typical objective function is the **average loss** over a dataset of _N_ samples:

\(\mathcal{L}(\mathbf{W}) = \frac{1}{N} \sum_{i=1}^N L(\mathbf{y}_i, \hat{\mathbf{y}}_i)\) (214)

where \(L(\mathbf{y}_i, \hat{\mathbf{y}}_i)\) represents the loss function that computes the error between the true output **y**_<sub>i</sub>_ and the predicted output \(\hat{\mathbf{y}}_i\) for each data point. To minimize this objective function, optimization algorithms such as **gradient descent** are used. The general update rule for the weights **W** is given by:

\(\mathbf{W} \leftarrow \mathbf{W} - \eta \nabla_{\mathbf{W}} \mathcal{L}(\mathbf{W})\) (215)

where \(\eta\) is the **learning rate**, and \(\nabla_{\mathbf{W}} \mathcal{L}(\mathbf{W})\) is the gradient of the loss function with respect to the weights. The gradient is computed using **backpropagation**, which applies the **chain rule** of calculus to propagate the error backward through the network, updating the parameters to minimize the loss. For this, we use the partial derivatives of the loss with respect to each layer's weights and biases, ensuring the error is distributed appropriately across all layers. For regression tasks, the **Mean Squared Error (MSE)** loss is frequently used. This loss function quantifies the error as the average squared difference between the predicted and true values. The MSE for a dataset of _N_ examples is given by:

\(L_{\text{MSE}} = \frac{1}{N} \sum_{i=1}^N (\mathbf{y}_i - \hat{\mathbf{y}}_i)^2\) (216)

where \(\hat{\mathbf{y}}_i = f(\mathbf{x}_i; \mathbf{W})\) is the network's predicted output for the _i_-th input **x**_<sub>i</sub>_. The gradient of the MSE with respect to the network's output \(\hat{\mathbf{y}}_i\) is:

\(\frac{\partial L_{\text{MSE}}}{\partial \hat{\mathbf{y}}_i} = 2 (\hat{\mathbf{y}}_i - \mathbf{y}_i)\) (217)

This gradient guides the weight update in the direction that minimizes the squared error, leading to a better fit of the model to the training data. For **classification tasks**, the **cross-entropy loss** is often employed, as it is particularly well-suited to tasks where the output is a probability distribution over multiple classes. In the binary classification case, where the target label **y**_<sub>i</sub>_ is either 0 or 1, the binary cross-entropy loss function is defined as:

\(L_{\text{CE}} = -\frac{1}{N} \sum_{i=1}^N [y_i \log(\hat{y}_i) + (1 - y_i) \log(1 - \hat{y}_i)]\) (218)

where \(\hat{y}_i = f(\mathbf{x}_i; \mathbf{W})\) is the predicted probability that the _i_-th sample belongs to the positive class (i.e., class 1). For multiclass classification, where the target label **y**_<sub>i</sub>_ is a one-hot encoded vector representing the true class, the general form of the cross-entropy loss is:

\(L_{\text{CE}} = -\frac{1}{N} \sum_{i=1}^N \sum_{c=1}^C y_{i,c} \log(\hat{y}_{i,c})\) (219)