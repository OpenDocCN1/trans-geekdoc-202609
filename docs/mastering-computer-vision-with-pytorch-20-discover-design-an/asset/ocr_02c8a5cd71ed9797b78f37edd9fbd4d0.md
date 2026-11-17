```
plt.imshow(flipped_image)
plt.title('RandomVerticalFlip')
plt.axis('off')
plt.show()
```

# RandomVerticalFlip

![](bbox=[0.31, 0.212, 0.686, 0.497])

**Figure 6.3: VerticalFlip augmentation**

# ColorJitter

```
# Randomly changes the brightness, contrast, saturation, and hue of an image.
import matplotlib.pyplot as plt
from torchvision import transforms
from PIL import Image
# Load image
image = Image.open('test.png')
# ColorJitter
color_jitter = transforms.ColorJitter(brightness=0.5,
contrast=0.5, hue=0.5)
jittered_image = color_jitter(image)
# Display
plt.imshow(jittered_image)
```