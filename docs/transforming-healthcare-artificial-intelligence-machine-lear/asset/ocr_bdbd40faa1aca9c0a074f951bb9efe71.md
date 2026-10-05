# Hybrid DBCT for lung cancer detection & severity analysis

Multi-layer perceptron extracts more useful information from an image, which is much beneficial for object classification. It also induces the nonlinearity to extract the required composite features. It also reduces the proportions but preserves the crucial aspects. Multi-layer perceptron can handle the difficulties in object classification, followed by the residual connection. CCTs immensely reduce the computational time and complexity in image classification with minimal datasets.

# 11.4.2.5 Sequence pooling

Sequence pooling is to move forward the attributes required for classification to the Multi-layer Perceptron Head for classification. It pools the attributes related to the tokens and enhance the performance of the compact convolution transformer.

# 11.4.2.6 Multi-layer perceptron

The multi-layer perceptron assists the model in grasping the non-linear gestures from the dataset for effective classification. Non-linear models differ from linear models in such a way that the crucial role in acquiring knowledge on complex, intricate interconnection present in the image. The multi-layer perceptron extracts the most preferred attributes for classification from the previous transformer convolution and encoder layers and consequently upgrades the performance of the compact convolution transformer. Classification is performed using the expertise procured from the images and correlating it to the resultant classes. It proffers flexibility by dealing with the distinct spatial of pixels in the input images.

Compact convolution transformers are simplified models from image classification applications. CCTs are the combination of convolutional neural networks and vision transformers. The combination is to focus and extract both the local and global gestures from the inputs. The vision transformers are used in huge of datasets for gaining expertise in classification, whereas CCT can perform the categorization with a minimal dataset, immensely reducing computation intricacy and time required for performing the task owing to exert on the least possible parameters.

This outperforms the other transformer models, such as MaxViT, Dei, ConViT, and T2T-ViT, and existing state-of-art models. For performing the tokenization, which is dividing the images into patches, CCT employs convolution block composed of convolution and pooling layers. The computational representation of convolutional layers, especially the pooling layers in the convolutional blocks of CCT, is as follows:

```
$X_0 = MaxPool(ReLU(conv2d(x))) \quad (11.1)$
```