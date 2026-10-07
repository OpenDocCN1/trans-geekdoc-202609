to use the word "tensor" instead. This term originally comes from the mathematical field of topology, where it has a somewhat more specific meaning, but in ML it's just shorthand for multi-dimensional array. This is where TensorFlow gives its name: it describes the data flow — what we've calling a pipeline — between tensors.

In math terminology, we call a one-dimensional array a vector, a two-dimensional array a matrix, and anything with more dimensions a tensor. The number of dimensions is the rank of the tensor. A vector is a tensor of rank 1, a matrix is a tensor of rank 2, an image is a tensor of rank 3, a batch of images is a tensor of rank 4 and so on. By the way, scalars or single numbers are tensors of rank 0, and zero-dimensional arrays.

At this point, you may be getting confused by the term **dimensions**. The tensor stores has three dimensions, but the image itself can be considered a point in 150,000-dimensional space. Or in the case of 32x32 images you're using here, a point in 3,072-dimensional space. It's a little confusing that the same word is used in both cases. For tensors we often use the word "axis" to describe a dimension, so an image has three axes with the first axis being the height, the second axis the width, and the third axis being the color channels.

The Param # in the summary shows the number of learnable parameters in each layer. In this simple model, only the Dense layer has learnable parameters: the values of the weights or coefficients a and the values of the vector b. There are 3,072×20 weights plus 20 additional bias values, so this model has 61,460 learnable parameters in total.

Turi Create's model has only 19,000 parameters. Your model is a bit bigger... but is it also better? No spoilers, you'll have to keep reading!

# # Compiling the model

Before you can use the model you need to compile it. This tells Keras how to train the model.

```
model.compile(loss="categorical_crossentropy",
               optimizer=optimizers.Adam(lr=1e-3),
               metrics=["accuracy"]
```