# 11.3.5 CODE

```
import numpy as np
from skimage.metrics import structural_similarity
import cv2
import matplotlib.pyplot as plt
def plot_image(image, factor=1):
    figure = plt.subplots(nrows=1, ncols=1, figsize=(15, 15))
    if np.issubdtype(image.dtype, np.floating):
        plt.imshow(image * factor)
    else:
        plt.imshow(image)
# load input images
image2000 = cv2.imread('C:/Users/patil/Desktop/GANESH/Book Chapter/Change detector/Images/Amazon Rainforest/Amazon rainforest 2000.jpg')
plot_image(image2000)
print(image2000.shape)
image2021 = cv2.imread('C:/Users/patil/Desktop/GANESH/Book Chapter/Change detector/Images/Amazon Rainforest/Amazon rainforest 2021.jpg')
plot_image(image2021)
print(image2021.shape)
# converting images to grayscale
grayA = cv2.cvtColor(image2000, cv2.COLOR_BGR2GRAY)
grayB = cv2.cvtColor(image2021, cv2.COLOR_BGR2GRAY)
# Find structural similarity using structural_similarity method
(score, diff) = structural_similarity(grayA, grayB, full=True)
diff = (diff * 255).astype("uint8")
print("SSIM:", score)
# Find threshold difference image
thresh = cv2.threshold(diff, 0, 255, cv2.THRESH_BINARY_INV | cv2.THRESH_OTSU)[1]
thresh1 = cv2.cvtColor(thresh, cv2.COLOR_BGR2RGB)
plot_image(thresh1)
```