```
1, 2
Output = 3, 4
```

Listing 3.18: Example of an output matrix with a 1 x 1 stride.

With an output stride of (2,2), the 1 x 1 convolution requires the insertion of additional rows and columns into the input image so that the reads of the operation can be performed. Therefore, the input looks as follows:

```
1, 0, 2, 0
Input = 0, 0, 0, 0
       3, 0, 4, 0
       0, 0, 0, 0
```

Listing 3.19: Example of an input matrix with a 2 x 2 stride.

The model can then read across this input using an output stride of (2,2) and will output a 4 x 4 image, in this case with no change as our model weights have no effect by design:

```
1, 0, 2, 0
Output = 0, 0, 0, 0
        3, 0, 4, 0
        0, 0, 0, 0
```

Listing 3.20: Example of an output matrix with a 2 x 2 stride.

# 3.4.1 Worked Example Using the Conv2DTranspose Layer

Keras provides the transpose convolution capability via the Conv2DTranspose layer. It can be added to your model directly; for example:

```
...
# define model
model = Sequential()
model.add(Conv2DTranspose(...))
```

Listing 3.21: Example of defining a model with a Conv2DTranspose layer.

We can demonstrate the behavior of this layer with a simple contrived example. First, we can define a contrived input image that is 2 x 2 pixels, as we did in the previous section. We can use specific values for each pixel so that after the transpose convolutional operation, we can see exactly what effect the operation had on the input.

```
...
# define input data
X = asarray([[1, 2],
             [3, 4]])
# show input data for context
print(X)
```

Listing 3.22: Example of defining an input matrix for the model.

Once the image is defined, we must add a channel dimension (e.g. grayscale) and also a sample dimension (e.g. we have 1 sample) so that we can pass it as input to the model.