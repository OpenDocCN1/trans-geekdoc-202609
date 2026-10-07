
# Sewer Pipe Defect Detection in CCTV Images ■ 225

## 12.3.1.2 Feature Map

The convolved feature map is formed by sliding the filter over the image and computing the dot product. Every layer feature map output acts as input to the next layer.

## 12.3.1.3 Region Proposal Network (RPN)

In RPN training, each region proposal is labeled to indicate whether an object has a defective or region. If the intersection (IOU) between the proposal and the ground-truth box exceeds the threshold (0.7 in this study), or if it has the highest IOU with a ground-truth box, the proposal is assigned as a positive training sample; if the maximum IOU between a non-positive proposal and the ground-truth box is lower than the corresponding threshold (0.3 in this study), the proposal is regarded as a negative sample. RPN in faster R-CNN is trained using a multi-task loss defined by Eq. 12.2.

```
$L\{p_i\}, \{t_i\} = \frac{1}{N_{cls}} \sum_{cls} L_{cls}(p_i, p_i^*) - \frac{1}{N_{reg}} \sum_{reg} P_i^* L_{reg}(t_i, t_i^*)$  (12.2)
```

where $i$ indicates the anchor, $P_i$ represents the predicted probability of anchor being one type of sewer pipe defect. $P_i^*$ represents the ground-truth label of anchor if the anchor is a positive sample and 0 if it is negative. $t_i$ is a vector indicating the coordinates of the predicted bounding box to a positive anchor. $N_{cls}$ and $N_{reg}$ are two normalization factors for the two components and are weighted by a balancing parameter $\lambda$. With reference to a related study [22], the value of $N_{cls}$ is set to 256 and $N_{reg}$ equals 2,400 which is an approximate value of the number of anchor locations in the model. The balancing parameter $\lambda$ is set to 10, so that both cls and reg are roughly weighted equal.

## 12.3.1.4 Region of Interest (ROI) Pooling

ROI operation is widely used in object detection tasks to reuse the feature map from CNN (Figure 12.1). It allows training object detection system to be used in an end-to-end manner and speeds up both training and testing time.

## 12.3.1.5 Max Pooling Layer

Max pooling is a sample based on the discretization process. The main objective is to download a sample of an input representation of an image to hidden layer output, etc. (Figure 12.2). It reduces dimensionality and allows assumptions to be about features contained in the sub-regions binned. Max pooling uses the maximum value from each of a cluster of neurons in the prior layer and the hyperparameter values, filter (f) =2 stride(s)=2.

226 Machine Intelligence 

![](img/f07153152e20646619066fcf6f1ecf5b_250_0.png)

Figure 12.1 Architecture model for developed faster R-CNN for sewer pipe defect detection.

| 1 | 3 | 2 | 1 |
|---|---|---|---|
| 2 | 9 | 1 | 1 |
| 1 | 3 | 2 | 3 |
| 5 | 6 | 1 | 2 |

Figure 12.2 Max pooling conversion process.

## 12.3.2 System Architecture

This proposed work is to detect sewer pipe defects trained in different networks and apply some background effects. Defects have been detected and feature matching is carried out. The flow diagram for pipe defect detection is shown in Figure 12.3. In this method, sewer pipe images have been collected from CCTV inspection videos.

Sewer Pipe Defect Detection in CCTV Images 227

![](img/f07153152e20646619066fcf6f1ecf5b_251_0.png)

Figure 12.3 Proposed workflow.

![](img/f07153152e20646619066fcf6f1ecf5b_251_1.png)

Figure 12.4 Labeled input image.

### 12.3.2.1 Labeled Input Image

The CCTV inspection videos are converted into frames and these frames are considered the input images. Further, they have been annotated using a labeling tool. (Figure 12.4). Finally, bounding boxes are created to be saved as .xml extension, like VOC dataset.

## 12.3.2 Identify Defects Using Faster R-CNN (RPN) and fast R-CNN

A faster R-CNN model consists of a region proposal network (RPN) and fast detector. There are three main steps in applying Faster R-CNN for object detection. First, a convolutional neural network is used on the raw images to extract features. A feature map of the raw image is generated through several layers of a CNN network, such as convolution, activation, pooling, and normalization. Based on the generated feature map, RPN, a single fully convolutional network generates region proposals with different aspect ratios and scales to distinguish foreground regions from background regions. In the third step, the generated region proposals are fed into the fast R-CNN detector for further refining, so that more accurate classification and bounding box localization are obtained. This predicts the location of the proposed bounding boxes, thereby getting the ground-truth box for the anchor. The coordinates of the anchor are calculated using Eqs (12.3)–(12.6).

```
$t_x = \frac{x-x_a}{w_a}, t_y = \frac{y-y_a}{h_a}  (12.3)
```
```
$t_w = \log\frac{w^*}{w_a}, t_h = \log\frac{h^*}{h_a}  (12.4)
```
```
$t_x^* = \frac{x^*-x_a}{w_a}, t_y^* = \frac{y^*-y_a}{h_a}  (12.5)
```
```
$t_w^* = \log\frac{w^*}{w_a}, t_h^* = \log\frac{h^*}{h_a}  (12.6)
```

### 12.3.2.3 Training with ZF/VGG/RESNET0

In this method, the fast R-CNN model is trained with different networks. First, the ZF network (without fully connected layers) is applied, using parameters like filters, the dimension of each filter, and stride values. For example, there are 96 convolution kernels with a dimension of $7 \times 7$ in the first and 256 kernels with a dimension of $7 \times 7$ in the second. Second is the VGG16 network with $3 \times 3$ convolutions. The ResNet50 convolutional network is trained on more than a million images from ImageNet database and the network is 50 layers deep and can classify images into 1,000–2,000 object categories, such as crack, root, deposit, and infiltration and the input length it can apply four stride convolutions and the filter size is 7, 3, 1.

### 12.3.2.4 RGB Image to HSV Image

The color represents Red, Green and Yellow. An HSV is a color space in which stands for Hue, S stands for Saturation and V stands for Value. Hue is the measure of color; average pipe detectors to have 200 different colors. Saturation is the relative purity of color, the brightness of an object is its intensity. Hue is defined as an angle: in 0 degrees is red, in 240 degrees are blue. The saturation value ranges from 0 to 1. Figure 12.5 shows the conversion of the RGB image to the HSV image. The angular relationship between tones around the color circle is easily identified. Equations (12.7)–(12.9) show Hue, Saturation and value, and produce the crack effectively.

Sewer Pipe Defect Detection in CCTV Images 229

![](img/f07153152e20646619066fcf6f1ecf5b_253_0.png)

Figure 12.5 RGB image converted to HSV image.

![](img/f07153152e20646619066fcf6f1ecf5b_253_1.png)

Figure 12.6 Crack detection.

```
$V=R\left(\frac{1}{3}\right)+G\left(\frac{1}{3}\right)+B\left(\frac{1}{3}\right)  (12.7)
```
```
$S=1-\frac{3}{(R+G+B)}[min(R,G,B)]  (12.8)
```
```
$H=\begin{cases} \theta & \text{if } B\le G \\ 360-\theta & \text{if } B>G \end{cases}  (12.9)
```

## 12.3.3 Crack Detection

Crack detection is used to identify cracks in an image and draw bounding boxes around them. This is a very important problem in computer vision in numerous applications. Figure 12.6 uses crack detection to identify crack roots, deposits, and infiltration.

## 12.4 Experimental Results

This proposed technique has been applied to detect defects, such as cracks, roots, deposits, infiltration, etc. This work takes 3,000 defects in various video images to prove experimental results. For defect detection, different sets of images are taken freely in different scenes, under various lighting conditions and they create defects in bounding boxes using faster R-CNN. Performance of the method is calculated using average precision (AP) and mean average precision (MAP) in overall defects and achieves better results. The proposed method applies some digital image processing techniques to produce better results. The dataset used in our experiments is a collection of sewer pipe inspection videos (CCTV footage), with that video converted into frames. The frames are more than 30,000–100,000 images depending upon CCTV videos.

### 12.4.1 Performance Analysis

The sewer pipe detects the defects such as cracks, roots, deposits, and infiltration performance of ZF networks. 12.7 (a) shows average result, 12.7 (b) shows the Resnet50 network gets better performance compared to ZF net, and 12.7 (c) shows that VGG16 gives better performance than the ZF and Resnet50 networks.

Our experimental results show that the proposed model based on the VGG network operates with a detection speed of 0.99 secs and training time of 8.573 secs better than the existing network of ZF and Resnet50. After training, this model is evaluated in terms of detection accuracy achieving MAP of 90 percent using the VGG network in the sewer pipe system. The defect detection MAP and the AP value are mentioned in Table 12.1.

### 12.4.2 Measure of Effectiveness

To calculate the AP and MAP for all the class, Eqs (12.10) and (12.11)

```
$AP = \frac{1}{11} \sum_{r\in\{0,0.1,...,1\}} \frac{\max p(p_r)}{P_r \geq r}  (12.10)
```

$p(\cdot)$ is the measured precision for recall $P_r$,

```
$MAP = \frac{1}{N_{cls}} \sum_{i} AP_i  (12.11)
```
