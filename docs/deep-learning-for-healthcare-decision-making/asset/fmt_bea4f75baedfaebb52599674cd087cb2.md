
![Figure 5.4 Diagram of a depthwise spatio-temporal separate module. In the diagram, BN is a batch normalization module that contributes the network's stability and improves training speed; and ReLU is the activation function rectified linear unit that adds non-linearity to the sequence of convolutions.](images/fig5_4_C.jpg)

[Figure 5.4 Diagram of a depthwise spatio-temporal separate module. In the diagram, BN is a batch normalization module that contributes the network's stability and improves training speed; and ReLU is the activation function rectified linear unit that adds non-linearity to the sequence of convolutions.](#ch5.xhtml#R_fig5_4)

### 5.2.6 U-net

U-Net is a convolutional neural network (CNN) created to segment biomedical images that improved accuracy and training speed of previous segmentation methods by creating the entire segmentation mask instead of classifying small patches of the image at a time. It also benefits heavily from data augmentation explained in [Section 5.4.3](#ch5.xhtml#sec5_4_3) and, therefore, can be trained on a small dataset ([Ronneberger *et al*. \[2015](#ch5.xhtml#ref5_29)]).

[Figure 5.5](#ch5.xhtml#fig5_5) shows a diagram of the U-Net model. The left side of the architecture shrinks the image dimensions and increases its depth (encoder), whereas the right side expands the image to create the segmentation map (decoder). The horizontal blue arrows represent shortcuts on the model, which combine previous layers from the encoder to the decoder. The layers are combined using a concatenation operator that simply append the feature maps along their channels.

![Figure 5.5 Diagram of the U-Net segmentation architecture.](images/fig5_5_C.jpg)

[Figure 5.5 Diagram of the U-Net segmentation architecture.](#ch5.xhtml#R_fig5_5)

### 5.2.7 EfficientNet

[Tan and Le \[2019](#ch5.xhtml#ref5_32)\] observed that models that balanced their depth, width, and resolution reached a higher accuracy for the same computational cost than models that favored only one of these coefficients. With that in mind, they proposed a compound scaling method that balances these three coefficients, given a target computational constraint. In their experiments, they chose the number of floating point operations (`FLOPs`) to determine the model size and used the accuracy on `ImageNet` to measure its performance.

The baseline coefficients were discovered through a grid search with a target of 400M `FLOPs`. Notably, the scaling factor of the network depth is linear, while the scaling factor of width and resolution is quadratic. In other words, doubling the network depth doubles the number of `FLOPs`, while doubling either the width or the resolution quadruples the number of `FLOPs`. The base model uses the mobile inverted bottleneck from [Howard *et al*. \[2017](#ch5.xhtml#ref5_16)\] coupled with squeeze-and-excitation module from [Hu *et al*. \[2018](#ch5.xhtml#ref5_17)\] as a building block.

### 5.2.8 Loss function

A loss function guides how the weights within the learning method are updated. It can be formulated either from the difference between expected output and predicted output or based on a desired feature that the output must present. The former can only be used in supervised training, whereas the latter is used in unsupervised training or as a complementary loss to a supervised training. The most common loss functions used for image segmentation architectures are weighted cross entropy (`WCE`), Dice distance, and Jaccard distance.

The Dice distance and Jaccard distance are very similar, as both originate from metrics used to measure the segmentation quality. The Dice distance is based on the Sorensen–Dice coefficient, whereas the Jaccard distance is based on the Jaccard index. The Dice coefficient is equal to twice the size of the intersection between sets `Y` and `Ŷ` divided by the sum of the elements on both sets:

$$Dice = \frac{2 \cdot \left| {Y \cap \hat{Y}} \right|}{\left| Y \right| + \left| \hat{Y} \right|}$$

In order to use the Dice equation as a loss function for supervised training of a neural network, it is necessary to adapt its formula, since the function was proposed to work with discrete data. The following equation is the Dice loss function adapted for a minimization problem that allows gradient backpropagation:

$$Dice\ distance = 1 - \frac{2 \cdot {\sum\limits_{i = 1}^{N}{y_{i} \cdot {\hat{y}}_{i}}}}{\sum\limits_{i = 1}^{N}{{\hat{y}}_{i}^{2} + {\hat{y}}_{i}^{2}}}$$

### 5.2.9 Metrics

We present in the following sections the metrics used to evaluate the segmentation performance; those metrics were chosen because they are standard on image segmentation and were used for performance comparison on the Liver tumor segmentation competition (LiTS).

#### 5.2.9.1 Overlapping metrics

Overlapping-based methods can determine whether voxels from the predicted segmentation appear in the ground-truth segmentation. On the other hand, they cannot calculate the distance between the voxels that are present in one set and not in the other.

Dice similarity coefficient: [Dice \[1945](#ch5.xhtml#ref5_8)\] proposed a metric to quantify the matches between two sets. Many other researchers have adopted the metric to evaluate the performance of medical segmentation. The Dice metric compares the overlapping ratio between the predicted mask and a manual segmentation done by a specialist.

Given two sets of voxels `A` and `B`, where `A` denotes a predicted segmentation of liver tumors and `B` denotes the ground-truth of liver tumors, we can calculate the Dice similarity coefficient through eqn (5.2), where `|A ∩ B|` is the intersection size between the two sets, and `|A|` and `|B|` are the sizes of the respective sets:

(5.2)

$$Dice\left( {A,B} \right) = \frac{2 \cdot \left| {A \cap B} \right|}{\left| A \right| + \left| B \right|}$$

Jaccard volume overlap error: The Jaccard similarity coefficient ([Jaccard \[1901](#ch5.xhtml#ref5_18)\]) of two sets is defined as their intersection size over their union size.

The Jaccard volume overlap error (`VOE`) is the complement of the Jaccard coefficient. Using `A` and `B` as the same pair of sets of the Dice similarity coefficient, `VOE` can be written in terms of `A` and `B`, as shown in eqn (5.3):

(5.3)

$$VOE = 1 - \frac{\left| {A \cap B} \right|}{\left| {A \cup B} \right|}$$

It is possible to observe that `VOE` measures the difference between two sets, so that similar sets have low `VOE` values, which is the opposite of the Dice similarity coefficient.

Surface distance metrics: Before describing a number of surface-distance-based metrics, it is important to introduce some important concepts. Let `x` be the distance between a voxel and a set of voxels `Y`, defined as

(5.4)

$$distance\left( {x,Y} \right) = \min\limits_{\forall y \in Y}distance\left( {x,y} \right)$$

The function `distance` in eqn (5.4) is the Euclidean distance between the coordinates of voxels `x` and `y`. Let `B[A]` be the set of all voxels in `A`’s border and `B[B]` denote the set of all voxels in the `B`’s border.

Metrics based on surface distance consider only voxels that belong to the segmentation surface. This characteristic can mask large volume errors that do not deform the segmentation surface.

Average symmetric surface distance: The average symmetric surface distance (`ASSD`) metric averages the distance between all voxels in `B[A]` to `B[B]` and all voxels in `B[B]` to `B[A]`. This metric gives a general idea of how close the borders are in their entire extension. However, due to its robustness to outliers, it masks any isolated δ mistakes. Since a variation δ over a single distance has the same effect as a variation of $\frac{\delta}{\left| B_{A} \right| + \left| B_{B} \right|}$ spread over all distances, consequently, a large surface has a smaller variation in `ASSD` value:

(5.5)
