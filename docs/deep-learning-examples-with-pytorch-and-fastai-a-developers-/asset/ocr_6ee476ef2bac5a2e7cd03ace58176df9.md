We will have to clean the dataset so that we can easily work with it.

First, let’s analyse the dataset. If we open the dataset-folder we can see two files for each cat image. One file with a .jpg extension and one with a .cat extension. The first contains the image and the second contains the coordinates of the keypoints.

Now we can grab those files into our list of files and corresponding labels.

```
labels = get_files(cat_folder, extensions='.cat')
images = get_image_files(cat_folder)
```

We should have the same number of image-files and label-files: `assert len(labels)==len(images)`

# 14.2 Visualize some of the Images

First we want to create a function to get the keypoints filename that corresponds to an image filename.

```
def image_to_keypoints(f): return f'{str(f)}.cat'
```

```
fname = images[0]
image = PILImage.create(fname)
image.show()
```

<matplotlib.axes._subplots.AxesSubplot at 0x7fc22e753250>