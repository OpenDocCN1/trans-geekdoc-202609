# Listing 12.30 Getting the CelebA data

```
!mkdir celeba_gan
!gdown --id 107m1010EJjLE5QxXLZiM9FpjSj70je684 -O celeba_gan/data.zip
!unzip -qq celeba_gan/data.zip -d celeba_gan
```

Once you’ve got the uncompressed images in a directory, you can use image_data- set_from_directory to turn it into a dataset. Since we just need the images—there are no labels—we’ll specify label_mode=None.

# Listing 12.31 Creating a dataset from a directory of images

```
from tensorflow import keras
dataset = keras.utils.dataset_from_directory(
    "celeba_gan",
    label_mode=None,
    image_size=(64, 64),
    batch_size=32,
    smart_resize=True)
```

Finally, let’s rescale the images to the [0-1] range.

# Listing 12.32 Rescaling the images

```
dataset = dataset.map(lambda x: x / 255.)
```

You can use the following code to display a sample image.

# Listing 12.33 Displaying the first image

```
import matplotlib.pyplot as plt
for x in dataset:
    plt.axis("off")
    plt.imshow((x.numpy() * 255).astype("int32")[0])
    break
```

# 12.5.4 The discriminator

First, we’ll develop a discriminator model that takes as input a candidate image (real or synthetic) and classifies it into one of two classes: “generated image” or “real image that comes from the training set.” One of the many issues that commonly arise with GANs is that the generator gets stuck with generated images that look like noise. A possible solution is to use dropout in the discriminator, so that’s what we will do here.