```
class MyNeuralNetwork:

    def __init__(self, s, t):
        self.input  = s

        self.weights1  = np.random.rand(self.input.shape[1],4)

        self.weights2 = np.random.rand(4,1)

        self.t  = t

        self.output = np.zeros(t.shape)
```

Once you have created an artificial neural network, you will have to train it. If you can fill in the biases and weights, you will be able to strengthen your predictions. They will be more accurate. Training, in simple words, is choosing the right values for the biases and weights. It is about trying out different values and then fine-tuning them based on the input data. The more correct the values for these two parameters, the more trained the neural network.

Every single iteration of this training process goes through two steps. The first is the calculation of the predicted output which also is labeled as feedforward. The second step is updating the biases and weights which are known as backpropagation.

A feedforward is a basic calculus. You will have to add a feedforward function to the Python code.

```
def ThisIsfeedforward(self):

    self.layer1 = sigmoid(np.dot(self.input, self.weights1))
```