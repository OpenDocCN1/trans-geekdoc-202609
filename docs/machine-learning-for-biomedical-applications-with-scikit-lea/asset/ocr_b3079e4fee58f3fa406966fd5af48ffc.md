# 8.1.4 Classification of histological images

We will now demonstrate how we can classify histological images based on texture. We will use PatchCamelon dataset, which contains healthy and cancerous breast tissue histological samples (Fig. 8.3).

# Training data

We select 1,500 images to train a classifier, and another 150 for testing. These data are available in the file *histological_data.npz*⁴ We can load this data as follows:

```
import numpy as np
data = np.load('histological_data.npz')
The training images are of size 96 × 96 pixels and are stored in a 3D array X_train:
X_train.shape
>>> (1500, 96, 96)
```

The images contain intensity values between 0 and 1:

```
print(X_train.min(),X_train.max())
>>> 0 1
```

The binary training y_train indicate whether the sample is cancerous (label 1) or not (label 0).

# Feature extraction

We will now create a getGLCMfeatures to extract two texture descriptors, contrast and dissimilarity, from gray level co-occurrence matrix. First, we need to convert the image into type `uint8` with a small number of gray levels, which we choose to be 64. We calculate GLCM matrix glcm in the x-direction and choose the distance between pairs of values to three pixels. Finally, we calculate contrast and dissimilarity d:

```
from skimage.feature import graycomatrix, graycopops
def getGLCMfeatures(im):
  im = np.round(im*63).astype('uint8')
glcm = graycomatrix(im, [3], [0])
c = graycopops(glcm, 'contrast')[0, 0]
d = graycopops(glcm, 'dissimilarity')[0, 0]
  return c, d
```

We will now create these two descriptors from all training images and input them into the feature vector features_train:

⁴ Available from gin-g-node.org/MachineLearningBiomedApplications/data.