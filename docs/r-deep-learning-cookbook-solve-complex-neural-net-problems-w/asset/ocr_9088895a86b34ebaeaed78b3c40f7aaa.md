Finally, the function returns a list of convoluted layers and their corresponding weights. The convoluted layer is a four-dimensional tensor with the following attributes:

+   - Number of (input) images, the same as `input`
+   - Height of each image (reduced to half in the case of 2 x 2 max-pooling)
+   - Width of each image (reduced to half in the case of 2 x 2 max-pooling)
+   - Number of channels produced, one for each convolution filter

# # Using functions to create a new convolution layer

The four-dimensional outcome of a newly created convolution layer is flattened to a two-dimensional layer such that it can be used as an input to a fully connected multilayered perceptron.

# # Getting ready

The recipe explains how to flatten a convolution layer before building the deep learning model. The input to the given function ( `flatten_conv_layer`) is a four-dimensional convolution layer that is defined based on previous layer.

# # How to do it...

1. Run the following function to flatten the convolution layer:

```
flatten_conv_layer <- function(layer) {
# Extract the shape of the input layer
layer_shape = layer$get_shape()
# Calculate the number of features as img_height * img_width *
num_channels
num_features =
prod(c(layer_shape$as_list()[[2]], layer_shape$as_list()[[3]], layer_
shape$as_list()[[4]]))
# Reshape the layer to [num_images, num_features].
layer_flat = tf$reshape(layer, shape(-1, num_features))
# Return both the flattened layer and the number of features.
return(list("layer_flat"=layer_flat, "num_features"=num_features))
}
```