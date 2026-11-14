![](bbox=[0.17, 0.1, 0.89, 0.44])

Figure 1: Proposed model architecture for stroke prediction.

# 3.3.1 Deep CNN for Imaging Data

A 3D CNN is used to scan volumetric CT/MRI images and obtain high-level spatial features related to ischemic lesions and cerebral abnormalities. The imaging data is processed in the CNN using several layers of 3D convolutions, batch normalization, and ReLU activation and captures hierarchical features like lesion size, location, and intensity. The last convolutional outputs are flattened and fed into a fully connected (FC) layer to generate a fixed-size image-derived embedding vector z_img, which is the learned representation of the patient's neuroanatomical state. This vector contains imaging-derived information critical to stroke severity and recovery prediction [24]. To mathematically represent the 3D CNN for imaging data formally, define the process in a layer-wise abstraction that captures the transformation from raw CT/MRI volumes to the embedding vector z_img: Let the volume of the input image be

```
X_{img} \in \mathbb{R}^{H*W*D} (1)
```

where H, W, and D are the height, width and depth of the CT.MRI scan. For each convolutional layer l, the transformation is represented as follows

```
X^{(l)} = \sigma(BN(W^{(l)} * X^{(l-1)} + b^{(l)})) (2)
```