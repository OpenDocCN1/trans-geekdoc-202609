# Classification

# MLP Head

# Sequence Pooling

# Transformer Encoder

# Reshape

![](bbox=[0.134, 0.383, 0.763, 0.477])

# 11.4.2.2 Tokenization

The input is fed into convolutional layers proceeded by the transformer blocks. Tokenization is performed to capture the contiguous correlations in the input image. It involves the convolutional layer and the pooling layer. The convolutional blocks offer the local attributes and include the non-linearity and compression so as to extract the spatial interconnection. It partitions the input image into tokens.

# 11.4.2.3 Reshaping

The attributes gathered from the tokens are converted into 1D array before transferring them to the proceeding layers for classification. The conversion is required to look after the gestures of the input images, which are required for subsequent processing of data in the forthcoming layers. To transfer the images in the form of encoded data, the tokens, which are the pictorial representation of images, are transformed into numerical depiction that is flexible for encoded layers of transformers. The 1D array of tokens is then passed through the transformer layers for further processing, 1D array conversion proffered the information in a structured way to ensure proficiency in classification tasks.