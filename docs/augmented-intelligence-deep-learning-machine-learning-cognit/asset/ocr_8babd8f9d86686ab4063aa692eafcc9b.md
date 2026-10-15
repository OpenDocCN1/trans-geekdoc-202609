The main motive of this convolution operation is to extract the details like edges, colours, gradient, etc. from the input image. With an increased number of convolution operations, we can extract other features from the image and in this way the computer gets an overall understanding of the image [12].

Sometimes we have to add zeros to the boundary of the image which is called zero-padding or simply padding. The size of the padding is a hyperparameter. It is use to control the size of convoluted matrix. There are two types of padding –

+   - Same Padding – The dimension of the convoluted matrix is same as of that of the original image.
+   - Valid Padding – The dimension of the convoluted matrix is less than that of the original image.

The Rectified Linear Unit (ReLU) activation function is then applied on the entire convoluted matrix by mapping the negative values to 0 and keeping the positive values.

The main purpose of the of ReLU is to break linearity and to increase the non-linearity in our images as most our images consist of non-linear features like different colours or gradients, etc.

# 4.4.2. Pooling Layer

POOLING layer is responsible for reducing the dimension of the convoluted matrix in order to reduce the computational resources required to process the convoluted matrix. It is also used to extract important and dominant attributes from the image which is unaffected by the position and rotation of the image.

There are generally two kinds of pooling -

+   - Max Pooling – When the filter hovers over a region of the image, it will extract the maximum pixel value from that region of the image as in Fig. (4.9).
+   - Average Pooling – When the filter hovers over a region of the image, it finds out the average of all the pixel values present in the region.

Max Pooling is better than Average Pooling as it removes noise or extraneous values from the convoluted matrix apart from reducing spatial dimensions [13].