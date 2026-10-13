
and ⌊ ⋅ ⌋ denotes the floor operation, i.e., ⌊3.7⌋ = 3. For example, if *l* = 5, *m* = 3, *p* = 0, and *s* = 1, then *k* = 3. On the other hand, if *l* = 5, *m* = 3, *p* = 0, and *s* = 2, then *k* = 2 (see [Figs. 18.21](#Chp018_885-995_B978044329238500024X.xhtml#f0115)A and B).

Note that if the values of *l*, *m*, *p*, and *s* are such that the filter matrix, as it slides over *I*, falls outside *I*, such operations are not performed. We only perform operations as long as the filter matrix is *contained* within *I*.

One may wonder why one has to pad with zeros. Note that by the way convolutions are performed, the size of the feature map is smaller than that of the input array. As we will soon see, in a deep network, the output feature map is used as input to the next layer. Thus, the size of the arrays would be decreasing as we move on deeper into the network. In contrast, after padding with zeros, as Eq. [(18.65)](#Chp018_885-995_B978044329238500024X.xhtml#deq111) suggests, we can control the size of the involved arrays. For example, if *l* = 5, *m* = 3, *s* = 1, and *p* = 1, then the output will have the same size *k* = 5 as the input array. As a matter of fact, if *p* = (*m* − 1)/2, for an odd value of *m*, *k* = *l*. In such cases, we call the operation *same convolution*. The other reason that padding may be used is that the border pixels of the input image contribute less to the output, compared to the pixels that are located in the interior of the image. Take as an example [Fig. 18.18](#Chp018_885-995_B978044329238500024X.xhtml#f0100). Pixel *I*(1, 1) contributes only to *O*(1, 1). In contrast, pixel *I*(2, 2) contributes to all output elements, since it is contained within the window area, in all four positions. Using padding with zeros, we give the chance to the border elements to have a more equal “say” to the output values, when compared with the interior pixels.

#### The nonlinearity step

Once convolutions have been performed and the bias term has been added to all feature map values, the next step is to apply a nonlinearity (activation function) to each one of the pixels of every feature map array. Any one of the nonlinearities that have been previously discussed can be employed. Currently, the rectified linear activation function, ReLU, seems to be the most popular one.

[Fig. 18.23](#Chp018_885-995_B978044329238500024X.xhtml#f0125)A shows the image obtained after filtering the original boat image with the edge detector filter in Eq. [(18.64)](#Chp018_885-995_B978044329238500024X.xhtml#deq110), and [Fig. 18.23](#Chp018_885-995_B978044329238500024X.xhtml#f0125)B shows the result that is obtained after the application of the ReLU nonlinearity on each individual pixel.

![Figure 18.23 (A) The image where the edges have been extracted and (B) the resulting image after applying the ReLU on each one of the pixels. Note that after filtering, the image array in (A) may involve negative values, which are set to zero after the ReLU activation.](images/B978044329238500024X/gr023.jpg)

Figure 18.23 (A) The image where the edges have been extracted and (B) the resulting image after applying the ReLU on each one of the pixels. Note that after filtering, the image array in (A) may involve negative values, which are set to zero after the ReLU activation.

#### The pooling step

The purpose of this step is to reduce the dimensionality of each feature map array. Sometimes, the step is also referred to as spatial pooling. To this end, one defines a window and slides it over the corresponding matrix. The sliding can be done by adopting a value for the respective stride parameter, *s*.
