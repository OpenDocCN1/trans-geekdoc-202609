```
plt.title('ColorJitter')
plt.show()
```

![](bbox=[0.31, 0.16, 0.69, 0.45])

**Figure 6.4:** Colorjitter augmentation

# # RandomRotation

```
# Rotates the image by a random angle.
import matplotlib.pyplot as plt
from torchvision import transforms
from PIL import Image

# Load image
image = Image.open('test.png')
# RandomRotation
random_rotation = transforms.RandomRotation(degrees=(0, 180))
rotated_image = random_rotation(image)

# Display
plt.imshow(rotated_image)
plt.title('RandomRotation')
plt.axis('off')
plt.show()
```