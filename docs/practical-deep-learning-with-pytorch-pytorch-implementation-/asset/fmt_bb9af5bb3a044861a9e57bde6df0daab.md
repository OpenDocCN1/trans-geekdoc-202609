
# GANs Common Datasets and DCGAN Implementation

GANs are commonly used in various applications, including image generation, data augmentation, and style transfer. Here are three popular datasets often used for training GANs:

## CIFAR-10 and CIFAR-100

The CIFAR-10 dataset contains 60,000 32x32 color images in 10 different classes, with 6,000 images per class. It is commonly used for image classification, but it is also a popular choice for GANs.

The CIFAR-100 dataset is an extension of CIFAR-10, with 100 different classes, each containing 600 images. It provides a more diverse set of objects for GAN training.

## Modified National Institute of Standards and Technology database (MNIST)

The MNIST dataset is a classic choice for GANs and other ML tasks. It consists of 28x28 grayscale images of handwritten digits (0-9). MNIST is relatively small, making it suitable for quick experimentation.

## ImageNet

The ImageNet dataset is one of the largest and most widely used datasets for GANs and image-related tasks. It contains millions of images across thousands of classes, providing a vast and diverse set of images. While it is more challenging to work with due to its size, it is suitable for training advanced GANs for various applications.

These datasets cover a range of complexities, from simple black-and-white digits in MNIST to high-resolution, colorful images in ImageNet. The choice of dataset depends on your specific application and the level of complexity required for your GAN project. Additionally, there are other datasets like CelebA, LSUN, and more that are also popular for GAN training, depending on the domain and task at hand.

## Code Example

Creating a DCGAN to generate image data for training is a complex task that often requires a deep learning framework like PyTorch. Here is a high-level outline of how you can create a DCGAN to generate image data using PyTorch:

The code below defines the core components of a DCGAN using PyTorch for generating images. It includes the `Generator` and `Discriminator` models, both built as subclasses of `nn.Module`. The `Generator` takes a latent vector as input and uses transposed convolutions, batch normalization, and ReLU activations to upscale the vector into an image, applying `Tanh` at the end for pixel normalization. The `Discriminator` processes real or generated images using convolutional layers, Leaky ReLU activations, and batch normalization to output a probability using `Sigmoid` indicating whether an image is real or fake.

```python
import torch

import torch.nn as nn

import torch.optim as optim

import torchvision

import torchvision.transforms as transforms

from torchvision.utils import make_grid, save_image

import matplotlib.pyplot as plt

import os

# Generator model for DCGAN

class Generator(nn.Module):

    def __init__(self, latent_dim):

        super(Generator, self).__init__()

        self.model = nn.Sequential(

            nn.ConvTranspose2d(latent_dim, 128, 7, 1, 0, bias=False),

            nn.BatchNorm2d(128),

            nn.ReLU(True),

            nn.ConvTranspose2d(128, 64, 4, 2, 1, bias=False),

            nn.BatchNorm2d(64),

            nn.ReLU(True),

            nn.ConvTranspose2d(64, 1, 4, 2, 1, bias=False),

            nn.Tanh()

        )

    def forward(self, x):

        return self.model(x)

# Discriminator model for DCGAN

class Discriminator(nn.Module):

    def __init__(self):

        super(Discriminator, self).__init__()

        self.model = nn.Sequential(

            nn.Conv2d(1, 64, 4, 2, 1, bias=False),

            nn.LeakyReLU(0.2, inplace=True),

            nn.Conv2d(64, 128, 4, 2, 1, bias=False),

            nn.BatchNorm2d(128),

            nn.LeakyReLU(0.2, inplace=True),

            nn.Conv2d(128, 1, 7, 1, 0, bias=False),

            nn.Sigmoid()

        )

    def forward(self, x):

        return self.model(x).view(-1, 1)
```

The code snippet below sets up parameters and data for training a GAN on the MNIST dataset. Key configurations include:

- Training parameters: `latent_dim` defines the dimensionality of the random noise vector for the generator, `batch_size` specifies the number of images processed in each training batch, and `epochs` limits training to a short duration.
- Data preparation: Downloads the MNIST dataset, applying transformations to convert images to tensors and normalize pixel values to a range of -1 to 1. The dataset is then loaded in batches, shuffled for randomness.

```python
# Training parameters

latent_dim = 64

batch_size = 32

epochs = 3 # Train for a limited number of epochs to keep training short

# Device configuration

device = torch.device("cuda" if torch.cuda.is_available() else "cpu")

# Load MNIST dataset

transform = transforms.Compose([

    transforms.ToTensor(),

    transforms.Normalize([0.5], [0.5])

])

train_dataset = torchvision.datasets.MNIST(root='./data', train=True, transform=transform, download=True)

train_loader = torch.utils.data.DataLoader(train_dataset, batch_size=batch_size, shuffle=True)

# Initialize models and optimizers

generator = Generator(latent_dim).to(device)

discriminator = Discriminator().to(device)

optimizer_G = optim.Adam(generator.parameters(), lr=0.0002, betas=(0.5, 0.999))

optimizer_D = optim.Adam(discriminator.parameters(), lr=0.0002, betas=(0.5, 0.999))

criterion = nn.BCELoss()
```

The code below implements a GAN training loop where the generator (`G`) and discriminator (`D`) are trained alternately. For each epoch, real images are loaded, and label tensors are created (valid for real, fake for generated images). The generator generates synthetic images from random noise to fool the discriminator, and its loss (`g_loss`) is calculated by comparing the discriminator’s predictions with valid labels. The discriminator then distinguishes real from fake images, computing real and fake losses, combined as `d_loss`. Gradients are backpropagated, and weights updated for both models. After each epoch, `d_loss` and `g_loss` is printed for progress tracking.

```python
# Training loop

for epoch in range(epochs):

    for i, (real_imgs, _) in enumerate(train_loader):

        real_imgs = real_imgs.to(device)

        batch_size = real_imgs.size(0)

        # Create labels

        valid = torch.ones(batch_size, 1, device=device)

        fake = torch.zeros(batch_size, 1, device=device)

        # Train Generator

        optimizer_G.zero_grad()

        z = torch.randn(batch_size, latent_dim, 1, 1, device=device)

        generated_imgs = generator(z)

        g_loss = criterion(discriminator(generated_imgs), valid)

        g_loss.backward()

        optimizer_G.step()

        # Train Discriminator

        optimizer_D.zero_grad()

        real_loss = criterion(discriminator(real_imgs), valid)

        fake_loss = criterion(discriminator(generated_imgs.detach()), fake)

        d_loss = (real_loss + fake_loss) / 2

        d_loss.backward()

        optimizer_D.step()

        print(f"Epoch [{epoch+1}/{epochs}] | D Loss: {d_loss.item():.4f} | G Loss: {g_loss.item():.4f}")

print("Training complete!")
```

![](images/Figure_5.8.png)

The code below generates synthetic images using random noise as input to the generator model. The images are saved in the `synthetic_data` directory, displayed in a grid format with `save_image` and `make_grid`. Finally, `matplotlib.pyplot` displays the images without axes for easy visualization.

```python
# Generate synthetic images

os.makedirs("synthetic_data", exist_ok=True)

z = torch.randn(64, latent_dim, 1, 1, device=device)

with torch.no_grad():

    generated_imgs = generator(z).cpu()

# Save and display generated images

save_image(generated_imgs, "synthetic_data/synthetic_images.png", nrow=8, normalize=True)

grid = make_grid(generated_imgs, nrow=8, normalize=True)

plt.figure(figsize=(10, 10))

plt.imshow(grid.permute(1, 2, 0).squeeze(), cmap="gray")

plt.axis('off')

plt.show()
```

![](images/Figure_5.9.png)

In this code:

- We define a generator and discriminator model.
- We specify the loss functions for the generator and discriminator.
- We create optimizers for both models.
- We load and preprocess real training data (MNIST dataset).

## Evaluating a generative adversarial network
