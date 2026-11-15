# How to do it...

+   1. Run the create_fc_layer function with the preceding input parameters:

```
layer_fc1 = create_fc_layer(input=layer_flat,
num_inputs=num_features,
num_outputs=fc_size,
use_relu=TRUE)
```

# How it works...

Here, we create a fully connected layer that returns a two-dimensional tensor. The first dimension (?) represents any number of (input) images and the second dimension represents the number of output neurons (here, 1,024).

# Applying dropout to the first fully connected layer

In this recipe, let's apply dropout to the output of the fully connected layer to reduce the chance of overfitting. The dropout step involves removing some neurons randomly during the learning process.

# Getting ready

The dropout is connected to the output of the layer. Thus, model initial structure is set up and loaded. For example, in dropout current layer layer_fc1 is defined, on which dropout is applied.

# How to do it...

+   1. Create a placeholder for dropout that can take probability as an input:

```
keep_prob <- tf$placeholder(tf$float32)
```