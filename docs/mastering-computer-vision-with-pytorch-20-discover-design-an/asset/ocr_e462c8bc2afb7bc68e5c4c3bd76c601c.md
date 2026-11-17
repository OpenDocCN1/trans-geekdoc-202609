# RandomAffine

![](bbox=[0.312, 0.111, 0.688, 0.396])

# Figure 6.7: RandomAffine augmentation

# GaussianBlur

```
# Blurs the image with a Gaussian filter.
import matplotlib.pyplot as plt
from torchvision import transforms
from PIL import Image

# Load image
image = Image.open('test.png')

# GaussianBlur
gaussian_blur = transforms.GaussianBlur(kernel_size=(5, 9),
                                       sigma=(0.1, 5))
blurred_image = gaussian_blur(image)

# Display
plt.imshow(blurred_image)
plt.title('GaussianBlur')
plt.axis('off')
plt.show()
```