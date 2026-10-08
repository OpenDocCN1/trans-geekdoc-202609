# Retrieving captions from images and images from captions

Chen et al., in the paper https://www.cs.cmu.edu/~xinleinic/papers/cvpr15_rnn.pdf, proposed a method to retrieve images from text and text from images. This is a bi-directional mapping. The following image shows a person explaining an image in natural language and another person visually thinking about it:

![](bbox=[0.267, 0.273, 0.732, 0.493])

Reproduced from Chen et al. (2015)

Retrieving captions can be achieved by connecting encoders of image and text through a latent space as shown here:

| Full model | Visual features -> Sentences | Sentences -> Visual features |
| --- | --- | --- |
| ![a](https://example.com/a.png) | ![b](https://example.com/b.png) | ![c](https://example.com/c.png) |
| (a) | (b) | (c) |

Reproduced from Chen et al. (2015)