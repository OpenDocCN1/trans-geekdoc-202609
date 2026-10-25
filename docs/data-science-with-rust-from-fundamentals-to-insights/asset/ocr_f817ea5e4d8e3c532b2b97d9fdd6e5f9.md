```
output
}
}
...
```

# Step 3: Backpropagation and Training

Backpropagation is the process through which the network learns by adjusting the weights and biases based on the error of its predictions. This involves calculating the gradient of the loss function and updating the parameters accordingly.

```
rust impl NeuralNetwork { fn train(&mut self, input: Vec, target: Vec, learning_rate: f64) { // Forward pass let hidden = self.forward(input.clone());
// Calculate output layer errors and deltas
let mut output_errors = vec![0.0; self.output_size];
let mut output_deltas = vec![0.0; self.output_size];
for i in 0..self.output_size {
output_errors[i] = target[i] - hidden[i];
output_deltas[i] = output_errors[i] * hidden[i] * (1.0 - hidden[i]);
}
// Calculate hidden layer errors and deltas
let mut hidden_errors = vec![0.0; self.hidden_size];
let mut hidden_deltas = vec![0.0; self.hidden_size];
for i in 0..self.hidden_size {
for j in 0..self.output_size {
hidden_errors[i] += output_deltas[j] * self.weights_ho[i][j];
}
hidden_deltas[i] = hidden_errors[i] * hidden[i] * (1.0 - hidden[i]);
}
// Update weights and biases
for i in 0..self.output_size {
self.bias_o[i] += output_deltas[i] * learning_rate;
for j in 0..self.hidden_size {
```