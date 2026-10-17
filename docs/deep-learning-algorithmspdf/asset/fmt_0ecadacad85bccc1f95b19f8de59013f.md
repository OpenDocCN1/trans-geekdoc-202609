
N is the number of kernels of the certain layer,

represents the feature

j

map of the previous layer, is the weight matrix, and is the bias term.

Max-pooling or average pooling is conducted after the convolution operation. Furthermore, the learned features are sent to the fully connected layer.

< '

input x will get the probability of belonging to class i.

(3)

where y is the response variable (i.e., predict label), k is the number of categories, and is the parameters of our model.

**Raw Dataset**

The raw tomato leaf dataset utilized in this work comes from an open access repository of images, which focus on plant health \[43\]. Health and other 8 diseases categories are included (see Table 1, Figure 2), i.e., early blight (pathogen: Alternaria solani) \[1\], yellow leaf curl disease (pathogen: Tomato Yellow Leaf Curl Virus (Tylcv), Family Geminiviridae, Genus Begomovirus) \[2\], corynespora leaf spot disease (pathogen: Corynespora cassiicola) \[3\], leaf mold disease (pathogen: Fulvia fulva) \[4\], virus disease (pathogen: Tomato Mosaic Virus) \[5\], late blight (pathogen: Phytophthora Infestans) \[6\], septoria leaf spot (pathogen: Septoria lycopersici) \[7\], and two-spotted spider mite (pathogen: Tetranychus urticae) \[8\]. The total dataset is 5550.

**Data Augmentation**

Deep convolutional neural networks contain millions of parameters; thus, massive amounts of data is required. Otherwise, the deep neural network may be overfitting or not robust. The most common method to reduce overfitting on image dataset is to enlarge the dataset manually and conduct label-preserving transformations \[21, 44\].

samples and 20% testing samples, and then the data augmentation procedure

\`{| \`|

\# \`| \`| "

brightness of image, setting the max delta to 0.4; (5) adjusting the contrast of image, setting the ratio from 0.2 to 1.5; (6) adjusting the hue of image, setting the max delta to 0.5; (7) adjusting the saturation of image, setting the ratio from 0.2 to 1.5; (8) rotating the image by 90° and 270° , respectively.

< <# #

the disease categories which are given in Table 1.

本书版权归Arcler所有

![Image 752](index-167_1.png)

![Image 753](index-167_2.png)

![Image 754](index-167_3.jpg)

![Image 755](index-167_4.png)

![Image 756](index-167_5.png)

![Image 757](index-167_6.png)

Can Deep Learning Identify Tomato Leaf Disease?

141

**Table 1**. The raw tomato leaf dataset

**Deep Learning Models**

***AlexNet***

AlexNet is the winner of ImageNet LargeScale Visual Recognition Challenge (ILSVRC) 2012, a deep convolutional neural network, which has 60 million parameters and 650,000 neurons \[21\]. The architecture of AlexNet utilized in this paper is displayed in Figure 3. The AlexNet architecture consists of five convolutional layers (i.e., conv1, conv2, and so on), some of which are followed by maxpooling layers (i.e., pool1, pool2, and pool5), three fully connected layers (i.e., fc6, fc7, and fc8), and a linear layer with softmax activation in output. In order to reduce overfitting in the fully connected layers, a regularization method called “dropout” is used (i.e., drop6, drop7)

\[21\]. The ReLU activation function is applied to each of the first seven layers (i.e., relu1, relu2, and so on) \[45\]. In Figure 3, the notation in each convolutional layer represents the size of the feature map for each layer, 4096

represents the number of neurons of the first two fully connected layers. The number of neurons of the final fully connected layer was modified to 9, since the classification problem in this work has 9 categories. In addition,

! # »

pixel size requirement of AlexNet.

本书版权归Arcler所有

![Image 758](index-168_1.jpg)

![Image 759](index-168_2.jpg)

![Image 760](index-168_3.png)

![Image 761](index-168_4.png)

![Image 762](index-168_5.png)

Deep Learning Algorithms

142

***GoogLeNet***

GoogLeNet is an inception architecture \[22\], which is the winner of ILSVRC 2014 and owns roughly 6.8 million parameters. The architecture of GoogLeNet is presented in Figure 4. The inception module is inspired by spatial dimension and limits the size of GoogLeNet. The whole architecture of GoogLeNet is stacked by inception module on top of each other (See Figure 4), which has nine inception modules, two convolutional layers, four maxpooling layers, one average pooling layer, one fully connected layer, and a linear layer with softmax function in the output. GoogLeNet uses dropout regularization in the fully connected layer and applies the ReLU activation function in all of the convolutional layers \[29\]. In this work, the last three layers of GoogLeNet were replaced by a fully connected layer, a softmax layer, and a classification layer; the fully connected layer was modified to 9 neurons, which is equal to the categories in the tomato leaf disease identification problem. The size requested of input image of GoogLeNet is

»

**Table 2**<

**Figure 3**. The architecture of AlexNet in this work.

***ResNet***

The deep residual learning framework is proposed for addressing the degradation problem. ResNet consists of many stacked residual units, which won the first place in ILSVRC 2015 and COCO 2015 classification challenge with error rate of 3.57% \[26\]. Each unit can be expressed in the following formulas \[47\]:

where are input and output of the l-th unit, and F is a residual function. In \[26\] is an identity mapping and f is a ReLU function

\[42\]. A “bottleneck” building block is designed for ResNet (See Figure 5)

responsible for changing in dimensions. ResNet model has three types of layers with 50, 101, and 152. For saving computing resources and training time, we choose the ResNet50, which also has high performance. In this work,

was replaced to 9 neurons, which is equal to the categories of the tomato leaf disease. We changed the structure of ResNet subsequently. The size of input

»

**EXPERIMENTS AND RESULTS**

In this section, we reveal the experiments and discuss the experimental results. All the experiments were implemented in Matlab under Windows 10, using the GPU NVIDIA GTX1050 with 4G video memory or NVIDIA GTX1080Ti with 11G video memory. In this paper, overall accuracy was regarded as the evaluation metric in every experiment on tomato leaf disease detection, which means the percentage of samples that are correctly classified:

(6)

where “true positive” is the number of instances that are positive and total number of samples. In addition, the training time was regarded as an additional performance metric of the network structure experiment.

**Experiments on Optimization Methods**

The first experiment is designed for seeking the suitable optimization method between SGD \[30\] and Adam \[30, 31\] in identifying tomato leaf diseases, combining with the pretrained network AlexNet, GoogLeNet, and ResNet, respectively. In this experiment, the hyperparameters were set as follows for each network: the batch size was set to 32, the initial learning rate was set to 0.001 and dropped by a factor of 0.5 every 2 epochs, and the max epoch was set to 5; i.e., the number of iterations is 6240. So far as SGD
