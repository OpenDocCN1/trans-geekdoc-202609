```
self.output = sigmoid(np.dot(self.layer1, self.weights2))
```

You can calculate the goodness of the predictions by using the Loss Function.
See how to use that function in the code.

There are a number of loss functions and the nature of the problem must
dictate the choice of the loss function.

```
def Thisbackprop(self):

    d_weights2 = np.dot(self.layer1.T, (2*(self.t - self.output) *
    sigmoid_derivative(self.output)))

    d_weights1 = np.dot(self.input.T,  (np.dot(2*(self.t - self.output)
    * sigmoid_derivative(self.output), self.weights2.T) *
    sigmoid_derivative(self.layer1)))

    self.weights1 += d_weights1

    self.weights2 += d_weights2
```

# Applications of Artificial Neural Networks

If I must explain an artificial neural network, I can easily do that by taking
the example of a human being. A child learns things when you teach him or
her. Parents and teachers play a crucial role in educating them. Later on, the
learning process goes on through self-learning and practicing. Researchers
and scientists are struggling to make machines intelligent just like humans
and ANNs are playing an important role due to the below-mentioned reasons.