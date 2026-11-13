
## 3.8.1 Computational resources and software

As the generator and discriminator can consist of several million trainable parameters each, a high amount of computational power was inevitable. The training of the GAN was therefore performed on the Baden-Württemberg High Performance Computing (bwHPC) resources and in particular on the GPU x4 partition of bwUniCluster 2.0. Its hardware and architecture is shown in Table 3.4 below.

Table 3.4: Specification of the GPU x4 partition compute nodes on bwUniCluster 2.0. Based on [299].

| GPU x4 partition resources |
| --- |
| Processors | Intel Xeon Gold 6230 |
| Number of sockets | 2 |
| Processor frequency | 2.1 GHz |
| Total number of cores | 40 |
| Main memory | 384 GB |
| Accelerators | 4x NVIDIA Tesla V100 |
| Accelerator memory | 32 GB |
| Interconnect | IB HDR |

While the CNN in Section 3.4.2.3 was solely trained via the Jupyter web access (JupyterLab 3.6.2), this approach was only used for the GAN for less computationally expensive jobs as only a limited amount of resources is available in this case. For all jobs requiring either high random-access memory (RAM), multi graphics processing unit (GPU) usage (NVIDIA CUDA) or a longer computing time, direct remote access through the command prompt with the standard Secure Shell protocol (SSH) was used to access the bwUniCluster 2.0.

The entire code is written in Python using both native Python files (.py) and Jupyter notebooks (.ipynb). The Fiji application of ImageJ2 was helpful for image visualization [300]. The following Python libraries and modules have been made use of in a virtual environment:

- PyTorch 1.10.1 and the Torchvision 0.11.2 library [301, 302]
- Numpy 1.19.5 [277]
- The OpenCV cv2 4.7.0.72 library for image editing [278]
- Matplotlib 3.3.4 for creating plots [279]
- TorchMetrics 0.8.2 for evaluating the image quality [303]
- Torchinfo 1.5.4 for structure information about the models [304]
- IPython 7.16.3 for live progress in Jupyter notebooks [305]
- tqdm 4.64.1 to show progress bars [306]
- Mahotas 1.4.13 to calculate Haralick features [307]
- SimpleITK 2.2.1 for image editing [284]

The Jupyter web access ran with Python 3.9.7, whereas the older Python 3.6.8 was installed on the cluster itself requiring some modifications when switching.

## 3.8.2 Image pre-processing

The scans of the nine specimens of Plate 3 were used along with the scans of nine specimens at identical positions of another CF-PA6 plate. The only difference of the latter, which is not pictured or numbered in Section 3.1.6 and Figure 3.4, was the insertion of the plastificate rotated through 180° to find possible changes in the fiber orientation drift. However, the overall fiber orientation and material behavior is identical. In addition, very similar scan parameters were used. The further processing of these 18 raw images is summarized in Figure 3.23 and will be described shortly in the following paragraphs.

![](img/332d06e0447dbfd85ea7d2fb553468f3_197_0.png)

**Figure 3.23:** Schematic depiction of the image pre-processing procedure from CT scans to training images.

### 3.8.2.1 Dropping border layers

The 18 3D scans have slightly varying width, height and layers (thickness) with minimum values of width × height × layers = 1366 × 1346 × 155 voxel. They are sliced in thickness direction to obtain 2D images with the largest dimensions and most information per slice. For every of those raw images, the first and last 30 layers were dropped. They were especially prone to portraying artifacts or air-rich areas (cf. Figure 3.24(a)). While these outer layers close to the specimen surface also show below average fiber volume contents due to the manufacturing process (cf. Figure 3.24(b)), varying FVC in the images was actually desired. Variety in realistic (not artifact based) microstructure depictions allows for the network to actually reproduce diverse output. Fortunately, even with the cut of the first and last 30 layers, still enough variety of FVC was given both within one scan and between the different scans.

### 3.8.2.2 Cutout images

In order to avoid dark border regions in the 2D images, specific cutout sections were considered. To further increase the amount of training images from the available scans, it was decided to use multiple cutout sections. Therefore, four 1,024 px × 1,024 px regions of interest were cut out of every of the remaining layers, each with a given arbitrarily chosen offset of 128 px from the center in x- and y-direction (cf. Figure 3.25). While it can be chosen arbitrarily as well, the size of the cutout section had the advantage of being a multiple of the later

![](img/332d06e0447dbfd85ea7d2fb553468f3_198_0.png)

![](img/332d06e0447dbfd85ea7d2fb553468f3_198_1.png)

(a) An exemplary first layer with surface roughness and air inclusions

(b) An exemplary ninth layer with low FVC

Figure 3.24: Two exemplary outer layers of different scans showing air-rich areas and a patchy surface (a) and a low FVC (b).

### 3.8.2.3 Downsizing and image smoothing

Considering downsizing, a balance between computation time and sufficient level of detail in both input and generated images was sought. After initially setting a size of 128 px × 128 px, finally, a size of 256 px × 256 px was chosen. The downsizing operation was performed with the recommended INTER_AREA interpolation from cv2. While this higher resolution allowed for the recognition of smaller fiber bundles and other details, it also conveyed a fair amount of salt-and-pepper noise. In order to avoid the generator learning this noise as desirable feature and applying it to the output images, the cutout images were blurred using a median filter before resizing them to the desired input resolution. A kernel size of 5 px × 5 px was chosen. Figure 3.26 exemplary shows an image of a CT scan slice with (a) and without (b) median filter.

The blurring effect is visible but still most details are recognizable. In fact the average signal-to-noise ratio (SNR) of all input images without median filter is

![](img/332d06e0447dbfd85ea7d2fb553468f3_199_0.png)

Figure 3.25: Exemplary layer with center (green) and offset (yellow) by ± 128 px in x- and y-direction cutout sections of 1.024 px × 1.024 px superimposed.

![](img/332d06e0447dbfd85ea7d2fb553468f3_199_1.png)

Figure 3.26: An example image of a CT scan slice with (a) and without (b) median filter.

with a value of 5.27 lower than the average SNR of all input images with median filter of 5.90. The latter were hence used as input images for the training.

### 3.8.2.4 Image augmentation

As most neural networks, GANs require a large training data set to be able to detect reoccurring image features. Figures of 10⁵–10⁶ images are suggested for modern, high-resolution GANs [308]. The high number of images is particularly relevant to reduce overfitting [309], which leads to the discriminator feedback becoming meaningless for the generator and finally the training diverging [308]. As reaching such a high amount of original training data is cumbersome and at times impossible, image augmentation has developed as the default solution to multiply the dataset [308, 309]. Augmentation refers to a deliberate, slight change to existing training images in order to create new training images that expand the original images within a meaningful scope to increase input dataset variety and improve training. Augmentation strategies for gray value images include but are not limited to rotation, flipping, translation, scaling and modifications of brightness and contrast [308]. In the case of the GAN presented in this thesis, every cutout image was rotated by 180° (corresponding to a point reflection) and additionally mirrored both horizontally and vertically, which can be seen in Figure 3.27.

A simultaneous mirroring at the horizontal and vertical axis was omitted due to being a duplicate to the 180° rotation. Furthermore, rotations by ± 90° were also left out to preserve the preferred fiber orientation resulting from the compression molding material flow. After all cutting and augmentation steps, this results in a total of 29,280 2D training images that are fed into the network as input.
