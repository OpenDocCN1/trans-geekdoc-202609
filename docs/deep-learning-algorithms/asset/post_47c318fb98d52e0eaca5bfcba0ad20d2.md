

y = F(x, {W_i}) + x,
F = W_2\sigma(W_1x),
\sigma(a) = max(0,a),
(1)

where x and y are the input and output vectors of stacked layers, respectively. The function (x, {Wi}) represents the residual mapping that needs to be learned. The function (a) denotes ReLU [26] and the biases are omitted for simplifying notations. The dimensions of x and F must be equal to perform the element-wise addition. If this is not the case, a linear projection Ws is applied to match the dimensions of x and F:

```
y = F(x,{W_i}) + W_sx.
(2)
```

The baseline building block is shown in Figure 2(a). A shortcut connection is added to each pair of 3 x 3 filters. Concerning the training time on deeper nets, a bottleneck building block is designed as in Figure 2(b). The three layers are 1 x 1, 3 x 3, and 1 x 1 convolutions, where the 1 x 1 layers are responsible for reducing and then restoring dimensions, leaving 3 x 3 layer a bottleneck with smaller input/output dimensions [23]. Bottleneck building blocks use fewer parameters to obtain more abstraction of layers.

The overall network architecture of our 26-layer ResNet, that is, ResNet26, model is depicted in Figure 3. As Figure 3 shows, the model is mainly designed by using bottleneck building blocks. The input image is fed into a 7 x 7 convolution layer and a 3 x 3 max pooling layer followed by 8 bottleneck building blocks. When the dimensions increase, 1 x 1 convolution is used in bottleneck to match dimensions. The 1 x 1 convolution enriches the level of abstraction and reduces the time complexity. The network ends with a global average pooling, a fully connected layer, and a softmax layer. We adopt batch normalization (BN) [27] right after each convolution layer and before ReLU [26] activation layer. Downsampling is performed by the first convolution layer, the max pooling layer, and the 3, 5, and 7 bottleneck building blocks.

## EXPERIMENTS AND RESULTS

### Implementation and Preprocess

The model implementation is based on the open source deep learning framework keras [28]. All the experiments were conducted on a Ubuntu 16.04 Linux server with a 3.40 GHz i7-3770 CPU (16 GB memory) and a GTX 1070 GPU (8 GB memory). The 100 samples of each class are split into 80 training samples and 20 test samples. Compared with conventional classification methods, data preprocess on deep learning approaches is much simpler. In this paper, the inputs to the network are RGB color images. All the images only need to be rescaled to 224 × 224 pixels and then per-pixel value is divided by 255.

![](img/1752b062af2760b8561f6faaf183b3d0_188_0.png)

Figure 4. Evolution of classification accuracy in the test set.

### Training Algorithm

During the back propagation phase, the model parameter is trained by the stochastic gradient descent (SGD) algorithm, with the categorical cross entropy loss function as optimization object. The SGD can be expressed as follows:

```
δ_x = w_{x+1} ( σ' ( w_{x+1} • c_x + b_{x+1} ) ◦ up ( δ_{x+1} ) ),

Δw_x = -η • Σ_{i,j} ( δ_x ◦ down ( S_{x-1} ) ),
```

where δx is sensitivity, wx+1 is multiplicative bias, ◦ indicates that each element is multiplied, up is upsampling, down is downsampling, Δwx represents the weight update of the layer, and η is the learning rate. The cross-entropy loss function is defined to be

\( L_i = -\log \left( \frac{e^{f_{y_i}}}{\sum_j e^{f_j}} \right), \) (4)

where \( f_j \) is the \( j \)th element in the classification score vector \( f \).

After some preliminary training experiments, the base learning rate is set to 0.001, which is gradually reduced at each epoch. The decay rate is \( 10^{-6} \) and the momentum is 0.9. Figure 4 shows the training process of ResNet26 model. Test accuracy improves quickly since the first epochs and stabilizes after 40 epochs.

![](img/1752b062af2760b8561f6faaf183b3d0_189_0.png)

Figure 5. Test accuracy of the ResNet18, ResNet34, ResNet50 [23], and ResNet26 model. The proposed ResNet26 outperforms the best reference ResNet by 2.51%.

### Results Analysis

To find the best deep residual network, a series of experiments have been conducted on BJFU100 dataset. Figure 5 shows the comparison of test accuracy among the proposed ResNet26 model and the original ResNet model of 18, 34, and 50 layers [23] designed for ImageNet. The ResNet18, ResNet34, and ResNet50 yield a test accuracy of 89.27%, 88.28%, and 86.15%, respectively. The proposed ResNet26 results in 91.78% accuracy which increases the overall efficiency up to 2.51%.

The ResNet26 is the best tradeoff between model capacity and optimization difficulty. For the size of BJFU100, ResNet26 contains enough trainable parameter to learn the discriminative features, which prevents underfitting.

Compared to larger model, ResNet26 results in fast and robust convergence during SGD optimization, which prevents overfitting or falls into local optimum.

## RESNET26 ON FLAVIA DATASET

To show the effectiveness of the proposed ResNet26 model, a series of experiments have been performed on the publicly available Flavia [29] leaf dataset. It comprises 1907 images of 1600 × 1200 pixels, with 32 categories. Some of the samples are shown in Figure 6. We randomly select 80% of the dataset for training and 20% for testing.

All the images are doubled and resized to 224 × 224 pixels. Per-pixel value is divided by the maximum value and subtracted the mean values of the data.

The training algorithm is exactly the same as that applied to the BJFU100 dataset. Figure 7 shows the training process of ResNet26 model. Test accuracy improves quickly since the first epochs and stabilizes after 30 epochs.

The test accuracy of each model is estimated by 10-fold cross-validation, as visualized in Figure 8. The ResNet18, ResNet34, and ResNet50 achieve a test accuracy of 99.44%, 98.95%, and 98.60%, respectively. The proposed ResNet26 gains 99.65% accuracy which increases the overall efficiency up to 0.21%. Table 1 summarizes our result and other previously published results on Flavia [29] leaf dataset. The ResNet26 model achieves a 0.28% improvement compared with the best-performing method.

![](img/1752b062af2760b8561f6faaf183b3d0_190_0.png)

Figure 6. Example images of the Flavia dataset.

![](img/1752b062af2760b8561f6faaf183b3d0_191_0.png)

Figure 7. Evolution of classification accuracy in the test set.

## CONCLUSION

The first mobile device acquired BJFU100 dataset containing 10,000 images of 100 plant species which provides data pillar stone for further plant identification study. We continue to expand the BJFU100 dataset by wider coverage of species and seasons. The dataset is open for academic community, which is available at http://pan.baidu.com/s/1jILsyspS. This work also studied a deep learning approach to automatically discover the representations needed for classification, allowing use of a unified end-to-end pipeline for recognizing plants in natural environment. The proposed model ResNet26 results in 91.78% accuracy in test set, demonstrating that deep learning is the promising technology for large-scale plant classification in natural environment.

In future work, the BJFU100 database will be expanded by more plant species at different phases of life cycle and more detailed annotations. The deep learning model will be extended from classification task to yield prediction, insect detection, disease segmentation, and so on.

![](img/1752b062af2760b8561f6faaf183b3d0_192_0.png)

Figure 8. Test accuracy of the ResNet18, ResNet34, ResNet50 [23], and ResNet26 model on Flavia dataset. The proposed ResNet26 outperforms the best reference ResNet by 0.21%.

Table 1. Recognition rate comparison on Flavia dataset

| Method | Recognition rate |
|---|---|
| PBPNN [21] | 93.82% |
| SVM [22] | 96.00% |
| DBNs (with “dropout”) [9] | 99.37% |
| Our work | 99.65% |

## ACKNOWLEDGMENTS

This work was supported by the Fundamental Research Funds for the Central Universities: YX2014-17 and TD2014-01.

