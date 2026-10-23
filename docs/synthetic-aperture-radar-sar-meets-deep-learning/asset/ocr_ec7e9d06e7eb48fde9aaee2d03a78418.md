Step 5: Roads segmented. For the road extraction results of optical remote sensing image and SAR image, the road segments are obtained by segment method, and the attributes of each segment are recorded;
Step 6: Decision level fusion. Taking the line segment as the basic unit, the final road distribution map is obtained by decision-making level fusion of the roads extracted from the optical remote sensing image and SAR image.

# 3. Experiments

Our network experiments are performed on the Massachusetts Roads Dataset, and we test the fusion method in our own dataset that came from WorldView-2, WorldView-4, and TerraSAR-X. The TensorFlow platform was selected as the deep learning framework to train and test all networks. All models are trained on one NVIDIA GTX 2080 Ti GPU.

# 3.1. Dataset and Data Augmentation

Three sets of satellite images were applied to evaluate the Low-Grade road extraction method. To verify the effectiveness of the proposed SDG-DenseNet network on public datasets, we tested the SDG-DenseNet on the Massachusetts dataset. In addition, we conducted low-grade road extraction experiments on the self-built Chongzhou-Wuzhen dataset. Finally, we conducted decision-level fusion experiments on two sets of large-scale images from the Chongzhou and Wuzhen regions including optical and SAR images.

We trained and tested our SDG-DenseNet network model on the Massachusetts Roads Dataset [44], which consists of 1108 training images, 14 validation images, and 49 test images. The size of each image is 1500 × 1500. We cut each 1500 × 1500 image into four 1024 × 1024 images. Therefore, we obtained 4432 training images, 56 validation images, and 196 test images. Further, we performed data augmentation on the training set, including rotation, flipping, cropping, and color jittering, which could prevent the training set from overfitting. After data augmentation, we obtained 22,160 training images in total. Finally, we obtained 22,160 training images, 56 validation images, and 196 test images.

In order to test the proposed SDG-DenseNet network of low-grade road extraction, this paper also tests the SDG-DenseNet on the self-built dataset: The Chongzhou-Wuzhen dataset. Table 1 displays the three source images of the self-built dataset. We cut the three source images into 13,004 512 × 512 images. Therefore, we obtained 11,788 training images, 204 validation images, and 1012 test images. After the data augmentation of the training set, we got 47,152 training images. Finally, we obtained 47,152 training images, 204 validation images, and 1012 test images.

Table 1. The three source images of the self-built low-grade road dataset.

| Data | Satellites | Resolution Ratio | Date | Scale | Area |
|---|---|---|---|---|---|
| 1 | WorldView-4 | 0.6 m | 13 May 2018 (optical) | 3469 × 4786 | Chongzhou, Sichuan |
| 2 | WorldView-2 | 0.5 m | 27 July 2018 (optical) | 2800 × 3597 | Wuzhen, Zhejiang |
| 3 | WorldView-2 | 0.5 m | 27 July 2018 (optical) | 2800 × 1798 | Wuzhen, Zhejiang |

We also test our decision-level fusion experiments on two sets of large-scale images from the Chongzhou and Wuzhen regions including optical and SAR images. The optical images came from WorldView-2 and WorldView-4, while we got the SAR images from TerraSAR-X. As shown in Table 2, in order to test the effect under application conditions, the decision-level fusion experiment is mainly tested on the two large-scale images.