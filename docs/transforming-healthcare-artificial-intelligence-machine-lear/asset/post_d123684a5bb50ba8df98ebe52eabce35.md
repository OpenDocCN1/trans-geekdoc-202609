
# Classification

# MLP Head

# Sequence Pooling

# Transformer Encoder

# Reshape

![](img/bb14ad24e4d4babb616ee31f6e899c86_249_0.png)

## 11.4.2.2 Tokenization

The input is fed into convolutional layers proceeded by the transformer blocks. Tokenization is performed to capture the contiguous correlations in the input image. It involves the convolutional layer and the pooling layer. The convolutional blocks offer the local attributes and include the non-linearity and compression so as to extract the spatial interconnection. It partitions the input image into tokens.

## 11.4.2.3 Reshaping

The attributes gathered from the tokens are converted into 1D array before transferring them to the proceeding layers for classification. The conversion is required to look after the gestures of the input images, which are required for subsequent processing of data in the forthcoming layers. To transfer the images in the form of encoded data, the tokens, which are the pictorial representation of images, are transformed into numerical depiction that is flexible for encoded layers of transformers. The 1D array of tokens is then passed through the transformer layers for further processing, 1D array conversion proffered the information in a structured way to ensure proficiency in classification tasks.

## 11.4.2.4 Transformer encoders

Transformer encoders are employed to gather the intricate attributes and data dependencies in the input image after tokenization. The transformer encoders are stacked together in the transformer encoder layer. Each transformer encoder layer comprises normalization layers, multi-head attention layer, multi-layer perceptron, and the residual connection. The detailed transformer architecture is shown in Figure 11.5. Normalization layer frames the input image to be stable before propagating through the multi-head attention and multi-layer perceptron.

Normalization layer improves the learning rate of the architecture by reducing the huge distinction in the surface of the image. Multi-head attention improves the learning by going through numerous attributes of the image to draw out the required relevant information for object classification. Residual connections are to prevent the problem of vanishing gradient. It captures the variation between the input image and the proceeding layers to acquire knowledge on attribute relevance in the image.

![](img/bb14ad24e4d4babb616ee31f6e899c86_250_0.png)

Figure 11.5 Transformer block of proposed DBCT.

## Hybrid DBCT for lung cancer detection & severity analysis

Multi-layer perceptron extracts more useful information from an image, which is much beneficial for object classification. It also induces the nonlinearity to extract the required composite features. It also reduces the proportions but preserves the crucial aspects. Multi-layer perceptron can handle the difficulties in object classification, followed by the residual connection. CCTs immensely reduce the computational time and complexity in image classification with minimal datasets.

## 11.4.2.5 Sequence pooling

Sequence pooling is to move forward the attributes required for classification to the Multi-layer Perceptron Head for classification. It pools the attributes related to the tokens and enhance the performance of the compact convolution transformer.

## 11.4.2.6 Multi-layer perceptron

The multi-layer perceptron assists the model in grasping the non-linear gestures from the dataset for effective classification. Non-linear models differ from linear models in such a way that the crucial role in acquiring knowledge on complex, intricate interconnection present in the image. The multi-layer perceptron extracts the most preferred attributes for classification from the previous transformer convolution and encoder layers and consequently upgrades the performance of the compact convolution transformer. Classification is performed using the expertise procured from the images and correlating it to the resultant classes. It proffers flexibility by dealing with the distinct spatial of pixels in the input images.

Compact convolution transformers are simplified models from image classification applications. CCTs are the combination of convolutional neural networks and vision transformers. The combination is to focus and extract both the local and global gestures from the inputs. The vision transformers are used in huge of datasets for gaining expertise in classification, whereas CCT can perform the categorization with a minimal dataset, immensely reducing computation intricacy and time required for performing the task owing to exert on the least possible parameters.

This outperforms the other transformer models, such as MaxViT, Dei, ConViT, and T2T-ViT, and existing state-of-art models. For performing the tokenization, which is dividing the images into patches, CCT employs convolution block composed of convolution and pooling layers. The computational representation of convolutional layers, especially the pooling layers in the convolutional blocks of CCT, is as follows:

```
$X_0 = MaxPool(ReLU(conv2d(x))) \quad (11.1)$
```

```
$xeR \times W \times C \quad (11.2)$
```

The images are transformed into tokens by convolutional layers in the tokenization step. It captures and preserves local features from input images, preceded by converting the images into one-dimensional array for organizing the image in the form of an encoder representation suitable for the further processing. Encoders fasten the learning rate, acquire the most relevant attributes for classification by the attention mechanism, and capture the variance in the distinct input images. It incorporate the non-linearity for learning complex features from the input images and relation in the images. The encoder gets rid of vanishing gradient problems by employing residual connections. The multi-head attention mechanism draws out the most relevant information required for the classification task.

```
$MultiHead(Q, K, V) = [Head1,..., HeadH]Wo \quad (11.3)$
```

The attention mechanism in which the $Q - Query$, $K - Key$, and $V - Values$ are significant in assigning weight to the crucial features extracted from the input images, thereby reducing the time spent for relevant attributes. The attention mechanism in addition acquires the long-term dependencies in the images. Sequence pooling reduces the dimension of the input image without losing the required features for classification. It also captures the global features from the image, avoids the problem of translation invariance, prevents the model from the problem of overfitting, reduces the difficulty in computation, and improves the performance of the model. Classification of image is done by the multi-layer perceptor as it plots the features of input with the output class using vital features extracted from the input. The proposed dense block convolution architecture is shown in Figure 11.6. The compact convolution transformer offers better accuracy in comparison with other transformer and convolutional models.

## 11.5 RESULTS AND DISCUSSION

The performance comparison of the proposed dense block convolution layer with the existing CNN algorithms like the EfficientNet-B0, ResNet-50, and DenseNet-121 and the CCT model in terms of accuracy, recall, precision, and F1-score for three different datasets, such as CT scan for binary classification, and colon adenocarcinoma, LC25000 dataset for five different classes of cancer including colon adenocarcinoma, benign lung adenocarcinoma, benign colonic tissues, and lung squamous cell carcinomas. IQ-OTH/NCCD dataset for severity analysis by classifying the malignant, and the non-cancerous stages of cancer is shown in Tables 11.1–11.3.

![](img/bb14ad24e4d4babb616ee31f6e899c86_253_0.png)

Figure 11.6 Proposed DBCT architecture.

Table 11.1 Performance analysis of CNN algorithms, compact convolutional transformer with the proposed dense block convolutional transformer model on CT scan dataset – binary classification
| Algorithms | Accuracy % | F1-score % | Precision % | Recall % |
|---|---|---|---|---|
| EfficientNet-B0 | 93.5 | 93.6 | 93.8 | 93.2 |
| ResNet-50 | 96.2 | 95.4 | 96.8 | 95.5 |
| DenseNet-121 | 96.5 | 96.4 | 96.7 | 96.3 |
| CCT | 97.6 | 97.4 | 97.8 | 97.5 |
| DBCT | 98.5 | 98.2 | 98.9 | 97.8 |

Table 11.2 Performance analysis of CNN algorithms, compact convolutional transformer with the proposed dense block convolutional transformer model on LC25000 dataset multiclass classification with five classes
| Algorithms | Accuracy % | F1-score % | Precision % | Recall % |
|---|---|---|---|---|
| EfficientNet-B0 | 87.2 | 86.3 | 87.4 | 86.5 |
| ResNet-50 | 90.5 | 89.7 | 90.7 | 90.3 |
| DenseNet-121 | 91.3 | 90.2 | 91.6 | 91.0 |
| CCT | 93.4 | 92.2 | 93.6 | 92.5 |
| DBCT | 94.5 | 93.9 | 94.7 | 94.1 |
