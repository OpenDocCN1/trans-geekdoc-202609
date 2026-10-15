```
# Define the model

class LinearRegressionModel(nn.Module):

    def __init__(self, input_size):

        super(LinearRegressionModel, self).__init__()

        self.linear = nn.Linear(input_size, 1)

    def forward(self, x):

        return self.linear(x)

# Initialize the model

# (We use x_train.shape[1] to get the number of input features)

model = LinearRegressionModel(x_train.shape[1])
```

This code defines a new class LinearRegressionModel that extends nn.Module, which is the base class for all neural network modules in PyTorch. The forward method