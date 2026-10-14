Networks.”2 In this 2015 paper, the authors show how to build a deep convolutional GAN to generate realistic images from a variety of datasets. They also introduce several changes that significantly improve the quality of the generated images.

![](bbox=[0.17, 0.16, 0.25, 0.24])

# Running the Code for This Example

The code for this example can be found in the Jupyter notebook located at notebooks/04_gan/01_dcgan/dcgan.ipynb in the book repository.

# The Bricks Dataset

First, you’ll need to download the training data. We’ll be using the Images of LEGO Bricks dataset that is available through Kaggle. This is a computer-rendered collection of 40,000 photographic images of 50 different toy bricks, taken from multiple angles. Some example images of Brickki products are shown in Figure 4-3.

![](bbox=[0.13, 0.4, 0.85, 0.44])

Figure 4-3. Examples of images from the Bricks dataset

You can download the dataset by running the Kaggle dataset downloader script in the book repository, as shown in Example 4-1. This will save the images and accompanying metadata locally to the /data folder.

# Example 4-1. Downloading the Bricks dataset

```
bash scripts/download_kaggle_data.sh joosthazelzet lego-brick-images
```

We use the Keras function image_dataset_from_directory to create a TensorFlow Dataset pointed at the directory where the images are stored, as shown in Example 4-2. This allows us to read batches of images into memory only when required (e.g., during training), so that we can work with large datasets and not worry about having to fit the entire dataset into memory. It also resizes the images to 64 × 64, interpolating between pixel values.

# Example 4-2. Creating a TensorFlow Dataset from image files in a directory

```
train_data = utils.image_dataset_from_directory(
"/app/data/lego-brick-images/dataset/",
labels=None,
color_mode="grayscale",
image_size=(64, 64),
batch_size=128,
)
```