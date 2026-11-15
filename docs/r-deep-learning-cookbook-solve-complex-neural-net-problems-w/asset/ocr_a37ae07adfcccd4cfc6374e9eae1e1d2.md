```
# Plot and output label
plot (img.col.mat,axes=FALSE,ann=FALSE)
}
par(mfrow=c(1,1))
}
```

# How it works...

The function begins with creating a shape tensor; namely, the list of four integers that are
the width of a filter, the height of a filter, the number of input channels, and the number of
given filters. Using this shape tensor, initialize a tensor of new weights with the defined
shape and create a tensor a new (constant) biases, one for each filter.

Once the necessary weights and biases are initialized, create a TensorFlow operation for
convolution using the tf$nn$conv2d function. In our current setup, the strides are set to 1
in all four dimensions and padding is set to SAME. The first and last are set to 1 by default,
but the middle two can factor in higher strides. A stride is the number of pixels by which
we allow the filter matrix to slide over the input (image) matrix.

A stride of 3 would mean three pixel jumps across the x or y axis for each filter slide.
Smaller strides would produce larger feature maps, thereby requiring higher computation
for convergence. As the padding is set to SAME, the input (image) matrix is padded with
zeros around the border so that we can apply the filter to border elements of the input
matrix. Using this feature, we can control the size of the output matrix (or feature maps) to
be the same as the input matrix.

On convolution, the bias values are added to each filter channel followed by pooling to
prevent overfitting. In the current setup, 2 x 2 max-pooling (using tf$nn$max_pool) is
performed to downsize the image resolution. Here, we consider 2 x 2 (ksize)-sized
windows select the largest value in each window. These windows stride by two pixels
(strides) either in the x or y direction.

On pooling, we add non-linearity to the layer using the ReLU activation function
(tf$nn$relu). In ReLU, each pixel is triggered in the filter and all negative pixel values are
replaced with zero using the max (x, 0) function, where x is a pixel value. Generally, ReLU
activation is performed before pooling. However, as we are using max-pooling, it doesn't
necessarily impact the outcome as such because relu (max_pool (x) ) is equivalent to
max_pool (relu (x) ). Thus, by applying ReLU post pooling, we can save a lot of ReLU
operations (~75%).