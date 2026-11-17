+   Watershed segmentation method: This method of segmentation is a combination of both region and edge-based segmentation techniques. This methodology for segmenting watersheds is based on how differential equations function.

+   K-Means clustering segmentation: In this method, a collection of data is divided into k numerical groups. It creates k different groups from a single set of data. K-means algorithm can be separated into two parts firstly, it identifies the k centroid and secondly, it shifts each point to that cluster's nearest centroids. The distance between the nearest centroid and the nearest point can be calculated in a variety of ways. Euclidean distance is one of the most widely utilized approaches. Eq. (3) shows the formula for calculating the Euclidean distance. Where K is the total no of cluster
+   
+   d = || p(x, y) – c_k ||

# 3.3.2. Deep learning-based segmentation techniques

In image processing, segmentation of the image is a difficult task that has been greatly improved using deep learning algorithms. The approaches based on deep learning have been suggested by researchers and the images may be effectively segmented using these techniques. These architectures include Deep Convolutional neural networks, U-Net, the Fully Convolutional Residual Network, etc. These are described more below.

+   CNN architecture: Neural Network (CNN) is a two-dimensional data processing variant of Multilayer Perceptron. CNN is a Deep Neural Network because of its great network depth and widespread use of image data. CNN's design is similar to that of neural networks in general; neurons in convolutional Neural networks have a bias, activation, and weight function. Fig. 4 explains the architecture of CNN, which includes a convolution layer with ReLU activation, a pooling layer for feature extraction, and then an entirely connected layer with softmax activation for classification. The feature extraction process is divided into three stages: convolution, activation, and pooling. These characteristics from the input image are retrieved and result in higher accuracy. CNN's layers make the model computational effective and it is better than other approaches because of its ability to handle massive data sets. Each filter has a modest equal height, width, and depth based on the size of the input. Convolution may be accomplished by employing the right filters. Convolution is a mathematical procedure that by combining two functions, x and y creates a third function (z) shown in Eq. (4) [3].
+   
+   z (n)def = x ( n ) * y ( n ) = 
+   \sum_{\eta=-\infty}^{\infty} x (\eta) g ( n - \eta)

+   U-Net architecture: This design was built using a Fully-Convolutional network. Convolutional layers are used in both the encoder and decoder of this network, in addition to convolutional layers; the encoder and decoder sections have pooled and upsampling layers, respectively. Between the encoder and decoder components, there's a shortcut link. Some researchers have used this design to split skin lesions. This architecture used to predict the likelihood of each pixel when segmenting skin lesion photos. They used expanded convolutions in the encoder branch's lowest layer to alter the U-Net architecture, resulting in the skinNet system.

+   Deep residual network (DRN): ANNs that employ skip connections to traverse many convolutional layers to construct a pyramidal structure are known as deep residual networks. Convolutional layers dominate the structure. An FCRN technique that uses deep residual networks to segment and classifies images of skin lesions. DRN that has greater than 50 layers was working to gain more

![](bbox=[0.071, 0.665, 0.926, 0.92])