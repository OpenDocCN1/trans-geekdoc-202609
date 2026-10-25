# Image Classification

With the progress of CNN, among the most important jobs is anticipating meaningful representation, which contributes to good classification results (John et al., 2021; Ravikumar et al., 2022; Ravikumar & Sriraman, 2023; Robin et al., 2022).

# Image Translation

CNN is not inherently translation-independent. However, CNN can acquire translation-invariant forms, provided it is trained with a suitable dataset. Learning the data with substantial amounts of change due to translating is the most critical factor in creating translation-invariant systems (Kauderer-Abrams, 2017).

# Image Tagging

Image tagging represents the most fundamental sort of image categorization technique. An image tag is a descriptive word or phrase which makes photographs simpler to locate. This strategy is used by major corporations such as Instagram, Google, and Amazon. In addition, it is one of the key components of visual search. Tagging encompasses item detection and even assessment of the emotional tone of a picture.

# Face Recognition

Face recognition generates a series of related issues, which are as follows: Identifying the faces in the image, Focusing on every expression, regardless of the face's quality or the positions it is exhibited in, and Recognizing distinctive traits,. Comparing the identified traits to those in the database and identifying the individual's name Expressions are complex, multimodal visual stimuli that were demonstrated using a neural net hybrid consisting of a local image sample, a self-organizing mapping neural net, and a CNN.

# RELATED WORKS

Since AlexNet (Deng et al., 2009; Krizhevsky et al., 2012) gained tremendous success in the ImageNet Challenge, CNNs have demonstrated superior performance on picture classification and a variety of other visual tasks. With the rapid expansion of hardware capacity, it can be used to train huge networks without difficulty. Nowadays, the primary trend for boosting networks' overall performance is to increase their depth. LeNet5 (Lecun et al., 1998), the first proposed CNNs are large and complex, gradient vanishing is a significant issue throughout the training process. ResNets (He et al., 2016) and DenseNets (R. K. Srivastava et al., 2015) explicitly use the structure of shortcuts between every two blocks. Highway Networks (R. K. Srivastava et al., 2015) inherently include nonlinear transforms and transform gates to provide shortcuts. FractalNets (Larsson et al., 2017; Yang et al., 2015) employ drop routes like ResNets. All of the solutions above are effective at resolving the gradient vanishing problem. According to research, classification accuracy degrades significantly when backpropagation (LeCun et al., 1989b) is used on deeper plain networks. The normalization approach (Ioffe & Szegedy, 2015) can assist in alleviating the difficulty. Despite their lack of depth, simple networks nevertheless provide several advantages, mainly when dealing with specific embedded vision applications. ALL Convolution Net (ALL-CNN)