
Table 2 compares the proposed method's using the mean error rate of the datasets, which should ideally be as small as possible. Thus, we need to find the optimal number of dilated layers most suitable for our entire network. Table 2 shows the optimal number of dilated layers = 7. Increasing the number of layers beyond that does not significantly improve the mean error rate, while introducing more parameters for the network and aggressively widening the receptive field via dilation factors would be detrimental to local features of small objects.

### Algorithm 1 Dilated skip connection for facial landmark detection

```
for t ← 1 to Nstep
  for all training images (1, H) do
    Feed in FC-DenseNets and get the response M
    Obtain the density H^ using Equation (3)
    Using Equation (4) to calculate H^dc
    Regress H' to H^ by using Equation (6)
    Optimize parameter Θ in Equation (9) with RMSprop, using loss L and target correction H
end
```

To evaluate the proposed algorithms, various datasets were created to investigate the robustness of the algorithms for imitating independent variations in pose, expression, illumination, background, occlusion and image quality. For instance, the 300W dataset [22] consists of a wide range of head pose images and AFLW2000-3D [43] contained large-scale images in 3D. For training and validation, we used 300W-LP [23], a synthetically expanded version of 300W, as a basis to train our model. The model was fine-tuned with AFLW, HELEN and 300W datasets. To observe how the network was flexible with unseen datasets, we analyzed the AFLW2000-3D dataset without training it in, as presented in Table 3. In our experiments, we implemented our proposed algorithm (Algorithm 1) in “in-the-world” datasets follows:

- 300W-LP [23] Large Pose (300W-LP) consists of 61,225 images with 68 key points for each facial image in 2D landmarks and the 2D projections of landmarks. It is a synthetically-expanded version of the 300W for obtaining appearance in larger poses.
- LFPW: The Labeled Faces In-the-Wild (LFPW) dataset has 1035 images divided into two parts: 811 images for training and 224 images for testing.
- HELEN [21]: HELEN dataset consists of 503 faces and 318 images with high accuracy, detailed and consistent annotations of the primary and components. It uses annotated Flickers.
- 300W: The 300 faces-in-Wild(300W) dataset consists of 348 images points on each face for training sets from three wild datasets as LFPW [20], AFLW [47] and HELEN [21]. There are three subsets for testing: challenging, common and full for test. For the challenging subset, we collected 554 images from the testing sets of HELEN and LFPW datasets; for the full subset, we merged the challenging and common subsets (689 images).
- AFLW 2000-3D [23]: Annotated Facial Landmarks in the Wild with 2000 three-dimensional images (AFLW2000-3D) is a 3D dataset constructed with 28 landmarks from the first 2000 images with yaw angles between ±90° of AFLW [49]. It varies expression and illumination conditions. However, some annotations, especially larger poses or occluded faces, are not very accurate.

# Table 3. The list of face datasets used for training and testing.

| Dataset | Landmark | Pose | Image |
| --- | --- | --- | --- |
| Training | | | |
| HELEN | 68 | ±45° | 2000 |
| LFPW | 68 | ±45° | 811 |
| 300W | 68 | ±45° | 3148 |
| 300W-LP | 68 | ±90° | 61,225 |
| Testing | | | |
| HELEN | 68 | ±45° | 330 |
| LFPW | 68 | ±45° | 224 |
| 300W | 68 | ±45° | 689 |
| AFLW2000-D | 68 | ±90° | 2000 |

For augmentation (e.g., randomly flipping, resizing and cropping images, etc.), PyTorch framework [42] leaves the original images untouched, returning a changed copy at every batch generation.

To reduce overfitting in our model, we artificially expanded the amount of training data using random augmentation including cropping, rotation, flipping, coloring jitter, scale noise and noise occlusion. We rotated the input image with a rotation angle of ±50° and scale noise from 0.8 to 1.2. We also scaled the longest side to 256 resulting in a 256 × H or H × 256 image, where H $\le$ 256.

We implemented our model based on the open source PyTorch framework [42], which is a dynamic program that runs on a GPU. We cropped our input image 256 × 256 resolution and generated an output set of response maps with the same resolution. We transferred the image's facial key points to heatmap using 2D Gaussian kernel. In our method, the variance (sigma) of 2D Gaussian kernel in response map was set to 0.25. For training, we optimized the parameters by RMSprop with a momentum of 0.9 and a weight decay of $10^{-4}$. We trained our model for 100 epochs with an initial learning rate of $10^{-3}$. We reduced it subsequently to $10^{-5}$ after 50 epochs and to $10^{-6}$ after 80 epochs. For loss in our network, we use the Euclidean function for our network,

```
$L(\Theta) = \sum_{i=1}^{N} ||Z(X_i;\Theta) - Z^i||^2
```
where N is the size of training batch and $Z(X_i;\Theta)$ is the output generated by parameters $\Theta$. $X_i$ represents the input and $Z^i$ is the ground-truth result. During training, $L(\Theta)$ calculates the difference between the estimated and corresponding ground-truth feature map to update parameter $\Theta$. We evaluated accuracy with three metrics: the normalized mean error (NME), the error distribution (CED) and the area under the curve (AUC). The NME was evaluated by measuring the distance between detected landmark coordinates and ground-truth facial coordinates.

```
$NME = \frac{1}{n} \sum_{i=1}^{n} \frac{||x^i - x_i^t||^2}{d}$
```
where $x^i$ are predicted coordinates and $x_i^t$ are ground-truth coordinates for $i^{th}$ image, $d$ denotes inter-ocular distance (distance between two eyes) and $n$ is the total number of landmarks. The CED is the cumulative distribution of the normalized error which is larger than $l$ and is reported as failure. Thus, CED at error is defined as

$CED = \frac{N_{NME \le l}}{n}$ where $N_{NME}$ is the number of images in which NME is higher than $l$. AUC calculates the percentages of images that lie under certain thresholds.

$AUC = \int_{0}^{s} f(e)de$ where $e$ is the normalized error, $f(e)$ is the CED function and $s$ is the upper bound used to calculate the definite integration. In this study, we evaluate our evaluation using mean error and CED. We calculated additional statistics such as the AUC which is up to error of 0.07. CED curves for our experiments on 300W and AFLW2000-3D sets are illustrated in Figure 7. Furthermore, as clearly stated in the figure, the AUC of 300W dataset is 72.49% and 65.99% for AFLW2000-3D dataset.

![](img/601340ca74b738277ef45ff127492a_128_0.png)
Figure 7: Cumulative error distribution (CED) curve and area under the curve (AUC).

The goal of the LFPW dataset was to study the problem of unconstrained face conditions we were trained on 811 images and tested on 224 images. Images were collected from Google, Flickr and Yahoo using text queries. Comparisons of different methods versus the proposed method are listed in Table 4. Our proposed method substantially reduced the mean rate. The second-best mean error rate in the CFSS [51] method, which has a mean error of 4.87%. Our method is considerably superior with an error rate of 3.52%. Furthermore, compared to the SDM [5] method, which used cascaded regressions and an error rate of 5.67%, our method also prevails by 2.15%.

# Table 4. Mean error in LFPW dataset.

| Method | 68 pts |
|---|---|---|
| Zhu et al. [52] | 8.29 |
| DRMF [55] | 6.57 |
| RCPR [63] | 5.67 |
| SDM [1] | 5.67 |
| GN-DPM [54] | 5.92 |
| CFAN [25] | 5.44 |
| CFSS [51] | 4.87 |
| CFSS Practical [51] | 4.90 |
| Ours | 3.52 |

# 4.3.2. Comparison with HELEN Dataset

Similar to the LFPW dataset, images were taken under unconstrained conditions with high resolutions and collected from Flickr using text queries. The dataset contained 2000 images for training and 330 images for testing.

Mean error of different methods on the HELEN dataset are presented in Table 5. Our method successfully achieved the lowest mean error among all mentioned methods, with a mean error of 3.11% compared to the second-best, TCDCN [55], which achieved only a 4.60% error rate.

# Table 5. Mean error on HELEN dataset.

| Method | 68 pts |
|---|---|---|
| Zhu et al. [52] | 8.16 |
| DRMF [53] | 6.70 |
| ESRB [1] | 5.93 |
| RCPR [43] | 5.50 |
| SDM [5] | 5.69 |
| GN-DPM [54] | 5.53 |
| CFAN [25] | 4.63 |
| CFSS [51] | 4.72 |
| CFSS Practical [51] | 4.60 |
| TCDCN [55] | 3.11 |
| Ours | |

# 4.3.3. Comparison with 300W Dataset

The 300W is an extremely challenging dataset that is used to compare the performance of different algorithms for facial landmark detection under the evaluation protocol. Table 6 presents the comparison results of the mean error of the 300W dataset.
