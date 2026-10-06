# Deep Learning With PyTorch

In deep learning, a large amount of labeled data is provided to the neural network architecture and it can extract relevant information to perform the given task.

For example, in the case of breast cancer detection, the engineer needs to extract specific features in the image and use those features to train a classifier, whereas in deep learning they just need to provide the labeled image.

# Comparison with State-of-the-Art

Ketkar, Nikhil. "Introduction to PyTorch." (Ketkar et al., 2017) discusses only the basics of PyTorch library methods along with a brief introduction of PyTorch with no focus on practical applications.
The authors of this chapter discuss not only the basics and features of PyTorch but also explains how deep learning works by discussing the mathematical expressions behind the algorithms. The authors explain PyTorch with real-life examples. The chapter is a complete description of deep learning using PyTorch that will be insightful to those who are just starting deep learning but also those who have some previous knowledge on the topic.

+   * PyTorch: An imperative style, high-performance deep learning library (Pazske et al., 2019) discusses in detail the architecture and ideology of PyTorch. The paper discusses the lower workings of PyTorch along with benchmarks which might be too details for a beginner. Similarly it ignores the concepts of deep learning, hence not suitable for beginners.
* Automatic differentiation in PyTorch (Pazske et al., 2017) is the original paper published with PyTorch that discusses the automatic differentiation module of PyTorch. Introduction to PyTorch, Tensors, and Tensor Operations (Mishra, 2019) discusses the basic operations on tensors in PyTorch.

# PyTorch vs Deep Learning Libraries

Over the past couple of years, several deep learning frameworks have emerged, each having its own set of methods to implement neural networks. Most of the major frameworks support GPU acceleration. Some use optimized libraries for GPU support such as CUDA (Nvidia C.U.D.A., 2007).
Deep learning libraries have accelerated the process of neural network so that the engineer can focus on creating new neural networks rather than implementing lower-level mathematical every.

The frameworks also optimize the neural networks to be more efficient and less-intensive. This section discusses some of the deep learning frameworks and libraries.

# Tensorflow

Tensorflow is the most widely used deep learning library that is developed by Google. Tensorflow allows the creation of neural networks by constructing static graphs that take data in runtime and are executed. The use of static graphs allows for more optimizations. Tensorflow can train and infer deep models on CPU, GPU, and TPU (Tensor processing unit), which is specialized hardware developed by Google to specifically train neural networks. Tensorflow model can also be inferred on low power devices like smartphones with the help of Tensorflow Lite. Tensorflow also supports high-level API like Keras (Chollet, 2015) which simplifies the process of creating simple models.