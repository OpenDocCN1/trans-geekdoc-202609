# ### 4.1. Datasets and Data Augmentation

Three public datasets, ShanghaiTech, UCF_CC_50, and UCF-QNRF, were used in our experiments. The statistics of samples and annotations in the datasets are shown in Table 5. ShanghaiTech includes samples of different scenes and crowd density levels, which are divided into two parts, Part_A and Part_B. The resolution of the images in Part_B is the same. The UCF_CC_50 dataset contains 50 grayscale images with different resolutions and scenes, including sports events, political processions, religious events, etc. The number of people in the images varies significantly, and some images are of extremely dense scenes. The UCF-QNRF dataset contains high-resolution images of outdoor surroundings with green plantation, buildings, streets, the sky and so on. Therefore, UCF-QNRF is of great significance to the dense crowd counting model against background interference.

**Table 5.** The statistics of samples and annotations in datasets.

| Dataset | Number of Samples (Total) | Number of Samples (Training Set) | Number of Samples (Test Set) | Average Resolution (Training Set) | Average Resolution (Test Set) | Annotations (Total) | Annotations (Ave) | Annotations (Max) |
|:--------|:-------------------------:|:-------------------------------:|:---------------------------:|:---------------------------------:|:-----------------------------:|:-------------------:|:-----------------:|:-----------------:|
| ShanghaiTech_Part_A | 482 | 300 | 182 | 872 × 598 | 861 × 574 | 241,677 | 501 | 3139 |
| ShanghaiTech_Part_B | 716 | 400 | 316 | 1024 × 768 | | 88,488 | 123 | 578 |
| UCF_CC_50 | 50 | - | - | 902 × 653 | | 63,974 | 1279 | 4633 |
| UCF-QNRF | 1535 | 1201 | 334 | 2896 × 2006 | 2910 × 2038 | 1,251,642 | 815 | 12,865 |

In ShanghaiTech and UCF-QNRF, samples were divided into a training set and a test set, but the size of three training sets was not large enough. The training sets and UCF_CC_50 were expanded. In order to compare them with other counting models under the same conditions, we used the general data enhancement method [16]. Nine patches of 1/4 size were cropped from an original image; four of them were nonoverlapping areas (top left, bottom left, top right, and bottom right), and the other five patches were randomly cropped. All patches and the original image were then mirrored. Finally, the sample size was expanded to 20 times the original ones. After expansion, UCF_CC_50 contained only 1000 samples, so we randomly cropped the very dense and high-resolution samples to expand the dataset to 7500 samples in total. A fivefold cross-validation was conducted, in which 6000 images were used for training and 1500 images were used for testing.

# ### 4.2. Evaluation Metrics

We used the commonly used measures of crowd counting [25], the mean absolute error (MAE) and mean squared error (MSE), which are defined as follows:

```
$MAE = \frac{1}{N}\sum_{i=1}^{N}\left|C_i - \hat{C}_i\right|, \: \: MSE = \sqrt{\frac{1}{N}\sum_{i=1}^{N}\left|C_i - \hat{C}_i\right|^2}$  (1)
```

where $N$ is the number of input images, $C_i$ is the actual number of people in the $i$ th image, and $\hat{C}_i$ is the estimated number of people in the $i$ th image. The lower the MAE is, the higher is counting accuracy; the lower the MSE is, the better the network's robustness is.

# ### 4.3. Network Training

The MSDKNet consists of three parts, and we train them separately from easy to difficult as follows:

+   1. Training the back-end network. The dimensions of MFE Net's input and output are same ($\mathbf{H}/8 \times \mathbf{W}/8 \times 512$), so we can remove it first and connect the back end to the front end directly. The front-end network adopts VGG16's pretrained model on