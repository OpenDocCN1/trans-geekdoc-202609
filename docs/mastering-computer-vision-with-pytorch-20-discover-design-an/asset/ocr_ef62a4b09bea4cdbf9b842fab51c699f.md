```
transforms.RandomResizedCrop(size=(224, 224)),
transforms.RandomRotation(degrees=(0, 180)),
transforms.ColorJitter(brightness=0.5, contrast=0.5,
saturation=0.5, hue=0.5),
transforms.RandomVerticalFlip(p=0.5),
transforms.RandomHorizontalFlip(p=0.5),
transforms.ToTensor(),
transforms.RandomErasing(p=0.5, scale=(0.1, 0.33), ratio=
(0.3, 3.3), value='random'),
])
```

```
# Function to display images
def show_augmented_images(image_path, num_images=5):
    image = Image.open(image_path)
    plt.figure(figsize=(15, 3))

    for i in range(num_images):
        augmented_image = all_augmentations(image)
        ax = plt.subplot(1, num_images, i + 1)
        ax.imshow(transforms.ToPILImage()(augmented_image))
        ax.axis('off')
    plt.show()

show_augmented_images('test.png')
```

The type of augmentation and the extent to which their range and probability can be increased depend on the problem we are trying to solve with our model. It also depends on the data.

With the correct augmentations, we can achieve accuracy a lot higher than without any augmentation.

It also makes our model generalized to predict the correct output even when the inference data is slightly or very different from our training data.