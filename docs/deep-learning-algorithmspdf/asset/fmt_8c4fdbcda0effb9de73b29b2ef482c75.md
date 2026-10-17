
16.04 Linux server with a 3.40 GHz i7-3770 CPU (16 GB memory) and a GTX 1070 GPU (8 GB memory). The 100 samples of each class are split into 80 training samples and 20 test samples. Compared with conventional classification methods, data preprocess on deep learning approaches is much simpler. In this paper, the inputs to the network are RGB color images. All

`value` is divided by 255.

**Training Algorithm**

During the back propagation phase, the model parameter is trained by the stochastic gradient descent (SGD) algorithm, with the categorical cross entropy loss function as optimization object. The SGD can be expressed as follows:

```
(3)
```

where `sensitivity` is sensitivity, `multiplicative bias` is multiplicative bias, `³` indicates that `³` represents the weight update of the layer, and `learning rate` is the learning rate. The

`+ #`

本书版权归Arcler所有

![Image 848](index-190_1.jpg)

![Image 849](index-190_2.jpg)

![Image 850](index-190_3.png)

![Image 851](index-190_4.png)

![Image 852](index-190_5.png)

Deep Learning Algorithms

164

(4)

where `݂` is the `݆ ݂`.

`݆`

After some preliminary training experiments, the base learning rate is set to 0.001, which is gradually reduced at each epoch. The decay rate is 10\_

and the momentum is 0.9. Figure 4 shows the training process of ResNet26

after 40 epochs.

**Figure 4**

本书版权归Arcler所有

![Image 853](index-191_1.jpg)

![Image 854](index-191_2.png)

![Image 855](index-191_3.png)

![Image 856](index-191_4.png)

Deep Learning Algorithms

165

Compared to larger model, ResNet26 results in fast and robust convergence during SGD optimization, which prevents overfitting or falls into local optimum.

**RESNET26 ON FLAVIA DATASET**

To show the effectiveness of the proposed ResNet26 model, a series of experiments have been performed on the publicly available Flavia leaf

Some of the samples are shown in Figure 6. We randomly select 80% of the dataset for training and 20% for testing.

`value` is divided by the maximum value and subtracted the mean values of the data.

The training algorithm is exactly the same as that applied to the BJFU100 dataset. Figure 7 shows the training process of ResNet26 model.

epochs.

The test accuracy of each model is estimated by 10- fold cross-validation, as visualized in Figure 8. The ResNet18, ResNet34, and ResNet50 achieve a test accuracy of 99.44%, 98.95%, and 98.60%, respectively. The proposed

to 0.21%. Table 1 summarizes our result and other previously published results on Flavia leaf dataset. The ResNet26 model achieves a 0.28%

improvement compared with the best-performing method.

**Figure 6**

本书版权归Arcler所有

![Image 857](index-192_1.jpg)

![Image 858](index-192_2.png)

![Image 859](index-192_3.png)

![Image 860](index-192_4.png)

Deep Learning Algorithms

166

**Figure 7**

**CONCLUSION**

The first mobile device acquired BJFU100 dataset containing 10,000 images of 100 plant species which provides data pillar stone for further plant identification study. We continue to expand the BJFU100 dataset by wider coverage of species and seasons. The dataset is open for academic community, which is available at http://pan.baidu.com/s/1jILsypS.This work also studied a deep learning approach to automatically discover the representations needed for classification, allowing use of a unified end-to-end pipeline for recognizing plants in natural environment. The proposed model ResNet26 results in 91.78% accuracy in test set, demonstrating that deep learning is the promising technology for large-scale plant classification in natural environment.

In future work, the BJFU100 database will be expanded by more plant species at different phases of life cycle and more detailed annotations.

The deep learning model prediction, insect detection, disease segmentation, and so on.

本书版权归Arcler所有

![Image 861](index-193_1.jpg)

![Image 862](index-193_2.png)

![Image 863](index-193_3.png)

![Image 864](index-193_4.png)

![Image 865](index-193_5.png)

**Figure 8**

The first mobile device acquired BJFU100 dataset containing 10,000 images of 100 plant species which provides data pillar stone for further plant identification study. We continue to expand the BJFU100 dataset by wider coverage of species and seasons. The dataset is open for academic community, which is available at http://pan.baidu.com/s/1jILsypS.This work also studied a deep learning approach to automatically discover the representations needed for classification, allowing use of a unified end-to-end pipeline for recognizing plants in natural environment. The proposed model ResNet26 results in 91.78% accuracy in test set, demonstrating that deep learning is the promising technology for large-scale plant classification in natural environment.

In future work, the BJFU100 database will be expanded by more plant species at different phases of life cycle and more detailed annotations.

The deep learning model prediction, insect detection, disease segmentation, and so on.

