+   - Num_inputs: This is the number of input features generated post flattening the convoluted layer
+   - Num_outputs: This is the number of output neurons fully connected with the input neurons
+   - Use_relu: This takes the binary flag that is set to FALSE only in the case of the final fully connected layer

# How to do it...

1. Run the following function to create a new fully connected layer:

```
# Create a new fully connected layer
create_fc_layer <- function(input,
num_inputs,
num_outputs,
use_relu=True)
{
# Create new weights and biases.
weights = weight_variable(shape=shape(num_inputs, num_outputs))
biases = bias_variable(shape=shape(num_outputs))
# Perform matrix multiplication of input layer with weights and
then add biases
layer = tf$matmul(input, weights) + biases
# Use ReLU?
if(use_relu) {
layer = tf$nn$relu(layer)
}
return(layer)
}
```

# How it works...

The function begins with initializing new weights and biases. Then, perform matrix multiplication of the input layer with initialized weights and add relevant biases.

If, the fully connected layer is not the final layer of the CNN TensorFlow graph, ReLU non-linear activation can be performed. Finally, the fully connected layer is returned.