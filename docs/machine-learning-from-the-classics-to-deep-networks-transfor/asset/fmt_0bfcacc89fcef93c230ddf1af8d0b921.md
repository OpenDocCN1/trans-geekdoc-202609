
## Network in network and 1×1 convolution

Let the input to a layer be an *h* × *w* × *d* volume. When volumes are involved, hidden layers consist of filter/kernel volumes, too. However, there is a crucial point here. The filter volume associated with the hidden layer *must* be of the same depth as the input volume. The height and width dimensions can be (and in practice usually are) different. We are going to use bold capital letters to denote volumes. Assume that the input is the *l* × *l* × *d* volume **I**. Obviously, this comprises *d* images, say, *I*[*r*], *r* = 1, 2, …, *d*, each one of dimensions *l* × *l*. Let the filter be the *m* × *m* × *d* volume **H**. The latter comprises the set of *d* images, *H*[*r*], *r* = 1, 2, …, *d*, each one of dimensions *m* × *m*. Then the operation of convolution is defined via the following steps:

1. Convolve corresponding two-dimensional image arrays to generate *d* two-dimensional output arrays, i.e., *O*[*r*] = *I*[*r*] ∗ *H*[*r*], *r* = 1, 2, …, *d*.
2. The convolution of the two volumes, **I** and **H**, is defined as

   $$O = \sum_{r=1}^{d} O_r.$$

In words, the convolution (denoted by ∗) of two volumes is a *two-dimensional array*.

The operation is illustrated in [Fig. 18.27](#Chp018_885-995_B978044329238500024X.xhtml#f0145). Corresponding arrays (shown by different colors and types of lines) are convolved. The three (*d* = 3) output arrays are subsequently added together to form the convolution of the two volumes. The dimension *k* of the output depends on the values of *l* and *m*, the stride *s*, and the padding *p*, if used, according to Eq. [(18.65)](#Chp018_885-995_B978044329238500024X.xhtml#deq111).

![Figure 18.27 The figure illustrates the case of depth d = 3. Convolving the l × l × d input volume (I) with a filter volume (H) with dimensions m × m × d is equivalent to convolving the d (l × l) matrices which comprise the input volume with an equal number of d (m × m) filters. This operation results in d output (feature map) matrices, which are subsequently added together. The value of k is determined by the specific values of l, m, and the stride s. No padding is involved in the case of this figure.](images/B978044329238500024X/gr027.jpg)

[Figure 18.27](#Chp018_885-995_B978044329238500024X.xhtml#cf1500) The figure illustrates the case of depth *d* = 3. Convolving the *l* × *l* × *d* input volume (**I**) with a filter volume (**H**) with dimensions *m* × *m* × *d* is equivalent to convolving the *d* (*l* × *l*) matrices which comprise the input volume with an equal number of *d* (*m* × *m*) filters. This operation results in *d* output (feature map) matrices, which are subsequently added together. The value of *k* is determined by the specific values of *l*, *m*, and the stride *s*. No padding is involved in the case of this figure.

In practice, each layer of a convolutional network comprises a number of such filter volumes. For example, if the input to a layer is an *l* × *l* × *d* volume, and there are, say, *c* kernel volumes, each one of dimensions *m* × *m* × *d*, the output of the layer will be a *k* × *k* × *c* volume, where *k* is determined as explained before.
