
# Understanding the earth from satellite imagery

Satellite images have become abundant recently. The images captured by satellite provide a high-resolution view of the total surface of the earth. By analyzing the satellite imagery, we can understand several things about earth such as:

- Measuring the rate of construction in a country related to economic growth
- Measuring the oil tanks
- Planning and organizing the traffic
- Calculating the deforestation and its effects
- Helping wildlife preservation by counting animals and tracking their movements
- Discovering archaeological sites
- Mapping the damaged regions due to a natural disaster

There are more applications possible with satellite imagery. For most of these problems mentioned, the solution starts with the segmentation of satellite images. We will see how to segment satellite images robots in the chapter.

# Enabling robots to see

Segmenting the scenes is crucial for robots to see and interact with the world around. Industrial and home robots have to handle the objects. The handling becomes possible once the vision to the objects is strides according to the objects. There are a few more applications worth mentioning:

- Industrial inspection of tools for segmenting the defects
- Color diagnostics of the fashion industry; an image can be segmented with various fashion objects and use them for color parsing
- Distinguished foreground from background to apply portrait effects

In the next section, we will learn a few public datasets for evaluating segmentation algorithms.

# Datasets

The PASCAL COCO datasets that were mentioned in Chapter 4, Object Detection, be used for the segmentation task as well. The annotations are different as they are labelled pixel-wise. New algorithms are usually benchmarked against the COCO dataset. COCO also has stuff datasets such as grass, wall, and sky. The pixel accuracy property can be used as a metric for evaluating algorithms.

Apart from those mentioned, there are several other datasets in the areas of medical imaging and satellite imagery. The links to a few of them are provided here for your reference:

- http://www.cs.bu.edu/~betke/BiomedicalImageSegmentation
- https://www.kaggle.com/c/intel-mobiledt-cervical-cance-r-screening/data
- https://www.kaggle.com/c/diabetic-retinopathy-detection
- https://grand-challenge.org/all-challenges
- http://www.via.cornell.edu/databases
- https://www.kaggle.com/c/dst1-satellite-imagery-feature-detection
- https://aws.amazon.com/public-datasets/spacenet
- https://www.iarpa.gov/challenges/fmow.html
- https://www.kaggle.com/c/planet-understanding-the-amazon-from-space

![](img/48c861eac4dc634fbf2a09fdbe884beb_147_0.png)

Creating training data for segmentation tasks is expensive. There are online tools available for annotating your dataset. The LabelMe mobile application provided by MIT University is good for annotating and can be downloaded from http://labelme.csail.mit.edu/

Release3.0.

# Algorithms for semantic segmentation

There are several deep learning-based algorithms that were proposed to solve image segmentation tasks. A sliding window approach can be applied at a pixel level for segmentation. A sliding window approach takes an image and breaks the image into smaller crops. Every crop of the image is classified for a label. This approach is expensive and inefficient because it does not reuse the shared features between the overlapping patches. In the following sections, we will discuss a few algorithms that can overcome this problem.

# The Fully Convolutional Network

The Fully Convolutional Network (FCN) introduced the idea of an end-to-end convolutional network. Any standard CNN architecture can be used for FCN by removing the fully connected layers, and the implementation of the same was shown in Chapter 4, Object Detection. The fully connected layers are replaced by a convolution layer. The depth is higher in the final layers and the size is smaller. Hence, 1D convolution can be performed to reach the desired number of labels. But for segmentation, the spatial dimension has to be preserved. Hence, the full convolution network is constructed without a max pooling, as shown here:

![](img/48c861eac4dc634fbf2a09fdbe884beb_148_0.png)

The loss for this network is computed by averaging the cross-entropy loss of every pixel and mini-batch. The final layer has a depth equal to the number of classes. FCN is similar to object detection except that the spatial dimension is preserved. The output produced by the architecture will be coarse as some pixels may be mispredicted. The computation and in the next section, we will see how to address this issue.

# The SegNet architecture

The SegNet has an encoder and decoder approach. The encode has various convolution layers and decoder deconvolution layers. SegNet improved the coarse outputs produced by FCN. Because of this, it is less intensive on memory. When the features are reduced in dimensions, it is upsampled to the image size by deconvolution, reversing the convolution effects. Deconvolution learns the parameters for upsampling. The output of such architecture will be coarse due to the loss of information in pooling layers.

![](img/48c861eac4dc634fbf2a09fdbe884beb_149_0.png)

Now, let's learn the few new concepts called upsampling, atrous convolution, and transpose convolution that will help us in understanding this network better.

# Upsampling the layers by pooling

In Chapter 1, Getting Started, we discussed max pooling. Max pooling is a sampling strategy that picks the maximum value from a window. This could be reversed for upsampling. Each value can be surrounded with zeros to upsample the layer, as shown here:

| 1 | 0 | 2 | 0 |
|---|---|---|---|
| 1 | 2 | 0 | 0 |
| 3 | 4 | 3 | 4 | 0 |
| 0 | 0 | 0 | 0 |

# Semantic Segmentation
# Chapter 5

The zeros are added at the same locations which are the numbers that are upsampled. Unpooling can be improved by remembering the locations of downsampling and using it for upsampling, as shown here:

| | 0 | 0 | 2 | 0 |
|---|---|---|---|---|
| 1 | 2 | 0 | 1 | 0 |
| 3 | 4 | 0 | 0 | 0 |
| | 3 | 0 | 0 | 4 |

Index-wise, upsampling yields better results than appending zeros. This upsampling the layers by pooling is not learned and works as it is. Next, we will see how we can upsample and downsample with learnable parameters.

# Sampling the layers by convolution

The layers can be upsampled or downsampled directly using convolution. The stride used for convolution can be increased to cause downsampling as shown here:

![](img/48c861eac4dc634fbf2a09fdbe884beb_150_0.png)

Downsampling by convolution is called atrous convolution or dilated convolution or strided convolution. Similarly, it can be reversed to upsample by learning a kernel as shown here:

# Semantic Segmentation
# Chapter 5

![](img/48c861eac4dc634fbf2a09fdbe884beb_151_0.png)

Upsampling directly using a convolution can be termed as transposed convolution. Some other synonyms are deconvolution or fractionally strided convolution or up-convolution. Now the process of upsampling is understood. Here is a code snippet that describes the previous algorithm:

```
input_height = 360
input_width = 480
kernel = 3
filter_size = 64
pad = 1
pool_size = 2
```

After the input is taken, it follows the neural net with decreasing size, which can be termed as an encoder. The following code can be used for defining the encoder:

```
model = tf.keras.models.Sequential()
model.add(tf.keras.layers.Layer(input_shape=(3, input_height, input_width)))

# encoder
model.add(tf.keras.layers.ZeroPadding2D(padding=(pad, pad)))
model.add(tf.keras.layers.Conv2D(filter_size, kernel, kernel, border_mode='valid'))
model.add(tf.keras.layers.Normalization())
model.add(tf.keras.layers.Activation('relu'))
model.add(tf.keras.layers.MaxPooling2D(pool_size=pool_size, pool_size=pool_size))

model.add(tf.keras.layers.ZeroPadding2D(padding=(pad, pad)))
model.add(tf.keras.layers.Conv2D(128, kernel, kernel, border_mode='valid'))
model.add(tf.keras.layers.Normalization())
```
