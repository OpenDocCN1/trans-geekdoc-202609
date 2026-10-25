```
# average across images
is_avg, is_std = mean(scores), std(scores)
return is_avg, is_std

# pretend to load images
images = ones((50, 299, 299, 3))
print('loaded', images.shape)
# calculate inception score
is_avg, is_std = calculate_inception_score(images)
print('score', is_avg, is_std)
```

Listing 12.16: Example of calculating conditional probabilities with the Inception model and calculating the inception score.

Running the example first defines the 50 fake images, then calculates the inception score on each batch and reports the expected inception score of 1.0, with a standard deviation of 0.0.

> Note: the first time the InceptionV3 model is used, Keras will download the model weights and save them into the ~/.keras/models/ directory on your workstation. The weights are about 100 megabytes and may take a moment to download depending on the speed of your internet connection.

```
loaded (50, 299, 299, 3)
score 1.0 0.0
```

Listing 12.17: Example output from calculating conditional probabilities with the Inception model and calculating the inception score.

We can test the calculation of the inception score on some real images. The Keras API provides access to the CIFAR-10 dataset (described in Section 8.2). These are color photos with the small size of 32 × 32 pixels. First, we can split the images into groups, then upsample the images to the expected size of 299 × 299, pre-process the pixel values, predict the class probabilities, then calculate the inception score. This will be a useful example if you intend to calculate the inception score on your own generated images, as you may have to either scale the images to the expected size for the inception v3 model or change the model to perform the upsampling for you. First, the images can be loaded and shuffled to ensure each split covers a diverse set of classes.

```
...
# load cifar10 images
(images, _), (_, _) = cifar10.load_data()
# shuffle images
shuffle(images)
```

Listing 12.18: Example of loading and shuffling the CIFAR-10 training dataset.

Next, we need a way to scale the images. We will use the scikit-image library to resize the NumPy array of pixel values to the required size. The scale_images() function below implements this.

```
# scale an array of images to a new size
def scale_images(images, new_shape):
    images_list = list()
    for image in images:
```