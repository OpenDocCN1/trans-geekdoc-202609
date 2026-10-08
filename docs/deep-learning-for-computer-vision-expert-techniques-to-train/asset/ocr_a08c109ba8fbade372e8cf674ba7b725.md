# Similarity Learning

Here is a sample of the images present in the dataset:

![](bbox=[0.107, 0.149, 0.892, 0.458])

Proposed by Cao et al. and reproduced from http://www.robots.ox.ac.uk/~vgg/vgg_face2/web_page_img.png

The minimum, mean, and maximum number of images per unique person are 87, 362.6, and 843 respectively.

# Computing the similarity between faces

The computing of face similarities is a multi-step problem. The faces have to be detected, followed by finding the fiducial points. The faces can be aligned with the fiducial points for comparison. As I have mentioned earlier, face detection is similar to object detection. So, in order to find the similarities between faces, we will first import the required libraries and also the facenet library, with the help of the following code:

```
import scipy misc
import tensorflow as tf
import numpy as np
import os
import facenet
print facenet
from facenet import load_model, prewhiten
import align.detect_face
```