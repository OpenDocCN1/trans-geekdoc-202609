# RandomRotation

![](bbox=[0.31, 0.11, 0.69, 0.395])

Figure 6.5: RandomRotation augmentation

# RandomResizedCrop

```
# Crops the given image to a random size and aspect ratio.
import matplotlib.pyplot as plt
from torchvision import transforms
from PIL import Image

# Load image
image = Image.open('test.png')

# RandomResizedCrop
random_resized_crop = transforms.RandomResizedCrop(size=(224,
224))
resized_cropped_image = random_resized_crop(image)

# Display
plt.imshow(resized_cropped_image)
plt.title('RandomResizedCrop')
plt.axis('off')
plt.show()
```