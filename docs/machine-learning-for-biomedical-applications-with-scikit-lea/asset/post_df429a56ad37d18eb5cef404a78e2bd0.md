
```python
net = ANRegressor()
print(net)
>>> ANRegressor(
  (layer): Linear(in_features=1, out_features=1,
    bias=True)
)
```

We can print the learnable parameters of the network:

```python
for parameter in net.parameters():
    print(parameter)
>>> Parameter containing:
tensor([-0.3753], requires_grad=True)
>>> Parameter containing:
tensor([0.1840], requires_grad=True)
```

These parameters correspond to $w_0$ and $w_1$ of the univariate linear regression $\hat{y} = w_0 + w_1x$.

Finally, we define the loss function which will be minimized to fit the model. The most common loss for regression models is the mean-squared-error loss (Eq. (9.3))—this loss function is available in torch.nn module as:
```python
loss_function = torch.nn.MSELoss()
```

# Binary classification in PyTorch

Similarly, for this we will also create an artificial neuron classifier that implements logistic regression, but just like the linear regression, but in addition to that we need a sigmoid activation function, which is available at torch.nn module as:
```python
torch.nn.Sigmoid()
```

The activation function is added to the __init__` and forward functions:

```python
class ANClassifier(nn.Module):
    def __init__(self):
        super(ANClassifier, self).__init__()
        self.layer = nn.Linear(2, 1)
        self.sigmoid = nn.Sigmoid()

    def forward(self, x):
        x = self.layer(x)
        x = self.sigmoid(x)
        return x
```

We can create an instance of a binary classifier net2 as

```python
net2 = ANClassifier()
print(net2)
>>> ANClassifier(
(layer): Linear(in_features=2, out_features=1,
bias=True)
(Sigmoid): Sigmoid())
)
```

Note that in this case we assume two input features and one output feature for the linear layer, this network is suitable for the binary classification example from Sect. 2.1.1 to predict heart failure from the ejection fraction and global longitudinal strain. The classifier is trained by minimizing a binary cross-entropy loss (Eq. (9.4)), which can be defined in PyTorch as follows:

```python
loss_function2 = torch.nn.BCELoss()
```

# 9.2.5 Training models in PyTorch

Once we have created our neural network model, we need to fit it to our data. We will demonstrate the training using linear regression to predict brain volume from the gestational age of a baby, introduced in Sect. 2.1.1. Training binary classification model requires the same steps as regression.

# Prepare training data

First, we will load the data into NumPy arrays and standardize the features using StandardScaler as usual. Note that both the feature matrix X and the target vector y are reshaped into 2D arrays.

```python
import pandas as pd
from sklearn.preprocessing import StandardScaler
data = pd.read_csv('neonatal_brain_volumes.csv').to_numpy()
X = StandardScaler().fit_transform(data[:].reshape(-1,1))
y = data[:].reshape(-1,1)
```

We need to convert the feature matrix X and target vector y to PyTorch tensors and make sure that they are type float.

```python
X = torch.from_numpy(X).float()
y = torch.from_numpy(y).float()
```

# Define the optimizer

Next, we define the optimizer as a stochastic gradient descent with learning rate $\eta=0.2$ (see Sect. 3.1.2). The optimizers are available in the module torch.optim:

```python
optimizer = torch.optim.SGD(net.parameters(), lr=0.2)
```

# Training

The training of the network is performed through a predefined number of iterations called epochs. During each epoch, we update the network using gradient descent. The following code shows how training is implemented. For our simple case of linear regression, we perform the training in a loop with 10 epochs:

```python
epochs = 10
for n in range(epochs):
    # 1. Clear gradients
    optimizer.zero_grad()
    # 2. Forward pass: predict outputs
    prediction = net(X)
    # 3. Compute loss
    loss = loss_function(prediction, y)
    # 4. Backward pass: calculate gradients
    loss.backward()
    # 5. Update parameters
    optimizer.step()
```

In step 1, gradients are set to zero. In step 2, the forward pass predicts the outputs (9.3). In step 3, the MSE loss is calculated (9.4). In step 4, the backward pass calculates the gradients (9.5). In step 5, the network parameters are updated (9.6).

# Plot the results

Figure 9.4 illustrates how to predict brain volume from the age. We can plot the results as follows:

```python
import matplotlib.pyplot as plt
plt.scatter(X, y)
plt.plot(prediction, 'r')
```

# Fitted models over epochs

Figure **9.4** Linear regression in PyTorch. Left: Fitted model over epochs. Right: MSE loss decreasing with increasing epochs.

# Evaluation

The performance of the model needs to be evaluated on the test set. We then calculate the MSE. If we wish to evaluate the root-squared error (for regression models only), we can take the square root of:

```python
rmse = torch.sqrt(mse)
```

# 9.2.6 Summary: creating and training networks

Here, we recap the steps to train a neural network in PyTorch:

1. Convert the training data to PyTorch tensors of type float.
2. Define the model architecture from nn.Module:
   a. In `__init__` define the layers and parameters.
   b. In `forward` define the forward pass.
3. Create an instance of the network, loss function, and optimizer.
4. Create the training loop over the epochs. Inside the loop:
   a. Clear gradients: `optimizer.zero_grad()`.
   b. Forward pass: predict the output of the network, `prediction=net(X)`.
   c. Calculate the loss: `loss=loss_function(prediction, y)`.
   d. Backward pass: calculate the gradients `loss.backward()`.
   e. Update weights using the optimizer `optimizer.step()`.

# 9.2.7 Exercises

1. Practice using PyTorch tensors. First, create and display a PyTorch tensor:
   - Create a NumPy array with values `[1,...,12]`. *Hint*: You can use `np.linspace`.
   - Convert it to a PyTorch tensor:
   - Print the output as size 3 × 4.
Next, learn how to concatenate two PyTorch tensors:
   - Create two random PyTorch tensors with sizes 1 × 2 × 4 × 4 and 1 × 5 × 4 ×4.
   - Concatenate them on the second axis using `torch.cat` (*Hint*: axis are numbered from 0).
   - Print the dimensions of the concatenated tensor.

2. Practice using the Autograd feature of PyTorch:
   - Create a PyTorch tensor `y` with values `[0.1]`.
   - Create PyTorch tensor `p` with values `[0.5,0.5,0.5]`. Set `requires_grad` to `True`.
   - Implement cross-entropy loss $L = -y_0 \log(p_0) - y_1 \log(p_1)$.
   - Print the out loss.
   - Calculate the gradients of the loss with respect to `p` and print them out.
   - Verify that they are correct.

3. Load the file `neonatal_brain_volumes.csv`. The file contains the age of the baby in the first column and the brain volume in the second column. Follow the PyTorch code in this section to fit a linear regression model to predict brain volume from the age. Plot the training data and the fitted model.

4. Load the file `heart_failure_data.csv`. The file contains cardiac indices EF and GLS in the first two columns. The third column contains a binary label indicating the diagnosis of heart failure (label 1). Implement a binary classifier in PyTorch to predict heart failure from EF and GLS, using the code given in this section. Plot the classification result.
