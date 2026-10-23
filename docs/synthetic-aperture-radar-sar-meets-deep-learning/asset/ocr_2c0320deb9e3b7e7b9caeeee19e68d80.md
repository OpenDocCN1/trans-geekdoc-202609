![](bbox=[0.12, 0.12, 0.85, 0.3])

Figure 6. Per image tile statistics for the training set, normalized. (a) shows the distribution of positive samples compared to the total number of pixels in an image tile and 20% of tiles have less than 1% of total pixels categorized as buildings. (b) shows the number of buildings count for each image tile. Most tiles (17.5%) contain less than 5 buildings.

# 2.5. Ablation Study

First, we studied the impact of each augmentation method in an ablation study, applying the same model and training configuration but applying different transformations to the dataset. To speed up this process, we trained and validated only a subset of our main training set. We divided it into 5 identical columned regions. The first and second columns were used as the mini-training dataset, while the last column was for the mini-validation dataset. We did not include the middle area in the mini training set to create a buffer (notice the high overlapping of tiles in Figure 2a) which prevents data leakage between both sets. The mini-training set and the mini-validation set contain 37% and 23% images of the main training set, respectively. After concluding which augmentation works well for the mini dataset in the ablation study, we applied combinations of positively impactful transformations to the main dataset.

# 3. Data Augmentation

This section describes the data augmentations used in this study and how they were implemented during the model's development. In general, the geometric transformations (including reduce transformation) were applied using TensorFlow operations, while pixel transformations were applied using the help of the Albumentation library [37].

# 3.1. Types of Data Augmentation

# 3.1.1. Reduce Transformation

Cropping the no-data regions result in a varying aspect ratio for each tile that must be addressed. Square-shaped images are preferred as data input to simplify spatial compression and expansion of the image inside the model. The image size also needs to be reduced to fit into the GPU's memory. We decided on the target resolution of 320 pixels by 320 pixels, which allowed the batch size of eight for the single P100 GPU. All resizing methods used the bilinear interpolation. Two main resize methods were tested:

+   - Pad Resize: no-data regions are added back to create a square aspect ratio, taking the minimum pixel value of 0.0. This is similar to the original tile, but now the raster is centered with no jagged borders. Next, the image is downsampled to the target resolution.
+   - Distorted Resize: rectangle shape tile is resized to the square target resolution, distorting the shape of the image, but no black regions are present.

This downsampling process can be exploited to introduce randomness that further increases the diversity of the training samples. Cropping at random locations gave better