
Deep learning (DL) which is subdivision of ML that includes computing hierarchical features or depictions of sample facts (for example, photographs) by combining lower-level abstract qualities, higher-level abstract qualities is formed (Deng et al.. 2014). DLC can process raw images straight, eliminating the necessity of preprocessing, dissection, and feature abstraction. Major DL methods necessitate image scaling due to the input value constraint. Some processes call for force normalization and contrast enhancement that may be evaded by employing the facts augmentation methods deliberated late in the passage. As a result, DLC improves classification accuracy by avoiding issues like erroneous feature vectors and sloppy segmentation. The feature vector is fed into ML classifier, which produces the object class, whereas the picture is fed into a DLC, which produces the object class. It’s worth noting that DL is theoretically superior to regular artificial neural networks (ANN) because this one has additional layers (`[Shen et al., 2017](#ch36.xhtml#ref36_20)`). Representable learning occurs when each layer translates the preceding layer’s response facts into a new depiction of the preceding layer’s response facts into a new depiction at advanced and additional abstract levels. That all levels of a DL network, a non-linear purpose transforms data into representation. In most circumstances, the occurrence or non-appearance of edges in precise arrangements, as well as their location in the image, can be determined using attributes gained from an image’s initial layer of representation. The second layer detects edge location while ignoring slight changes, and the third layer combines these patterns into higher groupings that match sections of comparable matters, allowing subsequent layers to recognize objects using these groupings. Deep learning’s remaining efficiency for a variety of AL uses is due to this hierarchical feature representation, which learns straight via response. `[Figure 36.9](#ch36.xhtml#fig36_9)` below displays a comparison of the ML and DLC methods (`[Suzuki et al., 2017](#ch36.xhtml#ref36_27)`).

``` 
![Figure 36.9 Comparison of ML and DL](images/fig36_9_B.jpg)
```

`[Figure 36.9 Comparison of ML and DL](#ch36.xhtml#R_fig36_9)`

Because it is like standard NN, CNN is the most often used DL architecture. Contrasting a traditional NN (displayed in `[Figure 36.10](#ch36.xhtml#fig36_10)a`), CNN responds to a picture and has a triple-dimensional structure of neurons to only connect to a little fraction of the prior level rather than the whole level (displayed in `[Figure 36.10](#ch36.xhtml#fig36_10)b`). The convolutional layer makes bulks of feature maps comprising the filter’s retrieved features by performing a convolution operation among pixels in the response picture and a strainer. The non-linear activation layer of ReLU increases non-linearity and training speed by applying the function f(x) = max (o, x) on reply inputs.

``` 
![Figure 36.10 Types of neural network (a) Traditional neural network (b) CNN (c) FCN](images/fig36_10_C.jpg)
```

`[Figure 36.10 Types of neural network (a) Traditional neural network (b) CNN (c) FCN](#ch36.xhtml#R_fig36_10)`

### Convolutional neural network (CNN)

CNN is frequently used to tackle classification prob-lems, as previously indicated. To practice CNN for semantic dissection, the response picture was distributed among minor squares of identical magnitude. A patch is then progressive to the next pixel in the center to be classified. However, because the corresponding topographies of the sliding squares are not reprocessed, the image loses spatial information of topographies traveling to finishing interconnected layers of the network which approach is inefficient. To resolve this difficulty, the FCN was suggested (shown in `[Figure 36.10](#ch36.xhtml#fig36_10)c`).

### Restricted Boltzmann machines (RBMs)

RBMs are a specific kind of NN and part of the broader group of unsupervised learning methods. The RBM is trained using a technique called contrastive divergence, which is a variant of Markov Chain Monte Carlo sampling. RBMs are useful for many different processes, such as feature learning, dimensionality reduction, collaborative filtering, and generative modeling. Applications including recommendation systems, picture recognition, and natural language processing have seen them particularly effective. One key advantage of RBMs is their ability to learn complex patterns and dependencies in the data without requiring labeled examples. This makes them useful in situations where labeled data is scarce or expensive to obtain. Overall, RBMs are powerful models for unsupervised learning that have found applications in various domains, contributing to advancements in ML and AI research. Established with the plan displayed in `[Figure 36.11](#ch36.xhtml#fig36_11)`, the RBM’s energy functions express:

``` 
*E*(*I*, *h*) =  − ∑[*i*]*a*[*i*]*I*[*i*] − ∑[*j*]*b*[*j*]*h*[*j*] − ∑[*i*, *j*]*I*[*i*]*h*[*j*]*w*[*i*, *f*]
```

### Autoencoder-based DL architectures

Autoencoders have insufficient applicability and are not appropriate as generative models because of breaks in latent space descriptions. It was decided to develop variational autoencoders to deal with this issue. For a variational autoencoder, the encoder produces two encoded vectors rather than a single encoded vector. The means vector is one and the standard deviations vector is the other. These vectors are used as inputs to an accidental adjustable that samples productivity encoded vector. `[Figure 36.12](#ch36.xhtml#fig36_12)` depicts the design of an autoencoder.

``` 
![Figure 36.12 Autoencoder architectures with vector](images/fig36_12_C.jpg)
```

`[Figure 36.12 Autoencoder architectures with vector](#ch36.xhtml#R_fig36_12)`

### Sparse coding-based deep learning architectures

This refers to NN models that incorporate the principles of sparse coding. Sparse coding is a technique used to represent data in an efficient and compact manner by utilizing a small number of non-zero activations. The idea is to select a small number of basic functions that capture the essential features of the data, while most coefficients remain zero or close to zero. In the context of DL architectures, sparse coding principles have been integrated in various ways to improve the representation learning capabilities of NNs. The use of sparse coding in DL architectures aims to capture more meaningful and informative representations of the data.

### Generative adversarial networks (GANs)

Generative adversarial networks (GANs) constitute a potent category of DL models capable of producing highly realistic synthetic data. Comprising two competing NNs a generator and a discriminator GANs are designed to create synthetic samples, such as images or text, which closely resemble real data. The generator network employs random noise as input to produce these synthetic samples, aiming to grasp the inherent data distribution and generate items akin to those found in the training data.

In contrast, the discriminator network functions as a binary classifier with the objective of distinguishing between authentic samples from the training data and spurious examples generated by the generator. GANs’ training mechanism involves an adversarial interplay between the generator and discriminator, wherein both networks enhance their performance through iterative iterations of this adversarial competition.

In essence, GANs have brought about a revolutionary shift in the realm of generative modeling by furnishing a framework for generating synthetic data that is both authentic and diverse. This area of research remains vibrant, with continuous advance-ments striving to enhance GANs’ stability, diversity, and relevance across various domains.

### Recurrent neural networks (RNNs)
