author of Keras, and it significantly outperformed Inception-v3 on a huge vision task
(350 million images and 17,000 classes). Just like Inception-v4, it also merges the
ideas of GoogleNet and ResNet, but it replaces the inception modules with a special
type of layer called depthwise separable convolution (or separable convolution for
short⁴). These layers were used before in some CNN architectures, but they were
not as central as in the Xception architecture. While a regular convolutional layer
filters that to simultaneously capture spatial patterns and cross-nannel patterns (e.g., oval) and (mouth + nose + eyes = face), a separable convolutional layer
makes the strong assumption that spatial patterns and cross-channel patterns can be
modeled separately (see Figure 14-19). This is composed of two parts: the first part
lies a single spatial filter for each input feature map, then the second part looks
exclusively for cross-channel patterns—it is just a regular convolutional layer with 1 x
filters.

![](bbox=[0.14, 0.368, 0.859, 0.673])

Figure 14-19. Deepwise Separable Convolutional Layer

Since separable convolutional layers only have one spatial filter per input channel,
y should avoid using them after layers that have too few channels, such as the input
layer (granted, that is what Figure 14-19 represents, but it is just for illustration pur-
poses). For this reason, the Xception architecture starts with 2 regular convolutional
layers, but then the rest of the architecture uses only separable convolutions (34 in