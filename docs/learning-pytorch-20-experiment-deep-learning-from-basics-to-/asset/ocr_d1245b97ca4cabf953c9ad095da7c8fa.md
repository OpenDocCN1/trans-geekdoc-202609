```
out = self.fc(out[:, -1, :])
```

```
return out
```

In this network, input_size is the number of features in the input data, hidden_size is the number of features in the hidden state, and output_size is the number of output features. The line out, _ = self.rnn(x) is where the sequence data is passed through the RNN layer. The hidden state is automatically initialized to zero by PyTorch, and it's not necessary to manually initialize it. The line out = self.fc(out[:, -1, :]) is where the last hidden state is passed through the fully connected layer to generate the output.

Instantiate the network: Creating an instance of your RNN is done in the same way as for the Feedforward network:

```
input_size = 10 # for example
```

```
hidden_size = 20 # for example
```

```
output_size = 1 # for example
```