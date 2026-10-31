Table 3. The proposed data augmentation parameters as an alternative to the default values.

| Parameter | Default Value | Proposed Value |
|---|---|---|
| Rotation_range | 20 | 15 |
| Width_shift_range | 0.10 | 0.05 |
| Height_shift_range | 0.10 | 0.05 |
| Rescale | 1/255 | 1/255 |
| Shear_range | 0.1 | 0.75 |
| Zoom_range | 0.1 | Zoom in by 10% max |
| Horizontal_flip | True | True, Vertical_flip = True |
| Fill_mode | nearest | Brightness_range=[0.1, 1.5] |

# Data Augmentation with Image Fusion

The quality of the medical images affects the diagnostic result; Different sensors produce different characteristics or marks. The IF allows us to recover these different characteristics and to group them in a single image that presents a lot of useful information. It is very difficult to describe the morphological structure of an organ with only one type of image.

To establish an efficient solution to extract the important information from the images and then inject them into a single image as shown in Fig. (11), first, an auto encoder is used for code generation, continuing the important information of each images, then NSST is used to decompose the source image into LFS and HFS, then fusion is performed based on fuzzy logic system (FLS) and new sum-modified-laplacian (NSML) fusion rules respectively, and finally the membership functions (MFs) of The FLSs are optimized by particle swarm optimization (PSO) to get the optimal fusion result.

# Auto-Encoder Architecture

The auto-encoder (Fig. 12) is a specific architecture of a neural network; it is composed of two sub-networks, the first one for encoding the images and the second one for decoding.