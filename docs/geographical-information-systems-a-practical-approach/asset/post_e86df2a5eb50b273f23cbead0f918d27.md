
![](img/8aad3fa01ca9db86bd50bb2edb9a3134_409_0.png)

Figure 7.27 Image segmentation at different scales: (a) colour infrared composite over Worri Yallock, (b) segmentation at a fine scale, (c) segmentation at an intermediate scale and (d) segmentation at a coarse scale.

and features extracted from image objects with over-segmentation may not represent real objects. Indeed, changing the bit depth of the heterogeneity measure can lead to different segmentations. In addition, different segmentation scales lead to differing image objects. There still exists a poor understanding of scale and hierarchical relations among objects derived at different scales.

Object-based classification is suited to heterogeneous landscapes and generally works well with high-resolution black-and-white or multispectral imagery, although they can be used with lower-spatial-resolution imagery as well (Whiteside et al. 2011). It provides a relatively quick, automated method for identifying and extracting features like rooftops or tree crowns.

## 7.5.4 Neural Network Classification

An artificial neural network (ANN) is a statistical learning algorithm in artificial intelligence that teaches computers to process data in a way that is inspired by the properties of a biological neural network. It is implemented as a system of interconnected processing elements, called nodes, which are functionally analogous to biological neurons. An ANN is typically formed by a set of three or more layers, including an input layer, one or more hidden layers and an output layer (Figure 7.28).

The nodes or artificial neurons in the input layer represent input variables. For image classification, the input variables might be selected spectral bands from a multispectral image and ancillary data, such as slope, aspect and texture. The hidden layers can be thought of as individual feature detectors, recognising or learning more and more complex, detailed features and patterns in the input image as it is propagated throughout the network. The nodes in the output layer are the output classes produced by the network. Each output node represents one land cover class in the classification system. Each node connects to another and has an associated weight and threshold. If the output of any individual node is above the specified threshold value, that node is activated, sending data to the next layer of the network. Otherwise, no data are passed along to the next layer of the network. By changing the weights in a systematic way, the network creates an adaptive system that computers use to learn from their mistakes and improve continuously and is eventually able to make inference on land cover classes. ANNs rely on training data to learn and improve their accuracy over time. Section 9.5 provides a detailed discussion on the ANN.

A recent breakthrough in image classification techniques came with the discovery that a **convolutional neural network** (CNN) could be used to progressively extract higher-level representations of the image content. A CNN is a special architecture of the ANN (Rawat and Wang 2017). It contains three main types of layers: convolutional layer, pooling layer and fully connected layer (Figure 7.29). The convolutional layer is the first layer of a CNN. Convolutional layers can be followed

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_410_0.png)

**Figure 7.28** An ANN for image classification.

by additional convolutional layers or pooling layers, and the fully connected layer is the final layer. With each layer, the CNN increases in its complexity, identifying greater portions of the image. Earlier layers focus on simple features, such as colours and edges. As the image data progresses through the layers of the CNN, it starts to recognise larger elements or shapes of the object until it finally identifies the intended object. Instead of preprocessing the data to derive features like textures and shapes, the CNN takes just the image’s raw pixel data as input and learns how to extract these features and ultimately infer what object they constitute.

The convolutional layer is the core building block of a CNN, and it is where the majority of computation occurs. It has a few components, including input data, a spatial filter and a feature map. Suppose the input is a true colour image which is made up of a matrix of pixels in three dimensions: height, width and depth. The height and width correspond to the length and width of the image in pixels, while the depth corresponds to the three bands of the image: red, green and blue. A spatial filter or kernel is used as a feature detector in an image convolution process (described in Section 7.3.4), which moves across the image, extracting meaningful features (for example, textures, edges, shapes and colours) from the image. The output from the series of convolution operations is known as a feature map.

After each convolution operation, a Rectified Linear Unit (ReLU) transformation is applied to the feature map, introducing nonlinearity to the model. The ReLU function F(X) = max(0, X) returns x for all input values of x > 0 and returns 0 for all values of x ≤ 0. This is sometimes referred to as activation, because only the activated features are carried forward into the next layer. As the number of filters (output feature map depth) applied to the input increases, so does the number of features the CNN can extract. Ultimately, the image is converted into numerical values in the convolutional layer, which allows the CNN to interpret the image and extract relevant features or patterns from it for image classification.

Pooling layers downsample the feature map, reducing the number of dimensions of the feature map while still preserving the most critical feature information. The pooling operation moves a kernel across the entire input, which applies an aggregation function to the values within the moving

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_411_0.png)

Figure 7.29 CNN image classification pipeline.

window and outputs the results to a new feature map. There are two main types of pooling: max pooling and average pooling. Max pooling operates in a similar fashion to convolution. For each moving window, the maximum pixel value is output to the output feature map, and all other values are discarded. Average pooling calculates the average value within each moving window and sends it to the output feature map. Although a lot of information is lost in pooling layers, they help reduce complexity and improve efficiency.

information. Box 7.1 and Case Studies 1, 5 and 12 in Chapter 10 provide examples of using remote sensing data to extract land cover information for impact assessment of an earthquake on giant panda habitats, rainfall–runoff modelling, land evaluation and economic evaluation of ecosystem services.

## 7.5.5 Accuracy Assessment

The CNN model has been incorporated into the ArcGIS Image Analyst extension and other digital image processing systems such as ENVI and ERDAS IMAGINE. The challenging part of using the CNN in practice is how to design model architectures that best use the various types of layers.

Although there are many image classification methods available, no single one is inherently superior to any other. Selection of a suitable method depends on the nature of the classification problem, the bio-physical characteristics of the study area, the distribution of the remote sensing data and a priori knowledge. In addition, all image classification results are subjected to a thorough accuracy assessment before they can be used in scientific investigations and policymaking. Assessment of image classification accuracy generally involves the collection of ground reference information at a number of sample locations, often referred to as test sites, in the study area that are representative of each land cover class. It normally requires the image analyst to

- 1 randomly select a number of test sites for each class, ideally 50 or more per class, depending on the size and complexity of the study area;
- 2 visit these randomly selected sites on the ground, determine their true classes and record their locations (for example, using a GPS);
- 3 locate these test sites in the classified image and determine their cover classes derived by the classifier;
