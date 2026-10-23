keys and the bounding boxes as values.

```
image_to_bbox = dict(zip(images, label_boxes))
```

To check if everything is ok we can grab the first item from our dictionary.

```
first = {k: image_to_bbox[k] for k in list(image_to_bbox)[:1]} first
```

```
{'000012.jpg': ([[155, 96, 351, 270]], ['car'])}
```

Here we want to get the same result for image 000012.jpg that we have seen above.

Now we have to create our getters for x and y values. Our model has two outputs. First the bounding box itself and second the label. In other words, our model returns a classification along with keypoint regression.

We need three getters. The first is a lambda function that grabs a given file: lambda o: path/'train'/o - the other two are looking for the bounding boxes along with the associated labels: lambda o: img2bbox[o][0], lambda o: img2bbox[o][1].

```
getters = [lambda o: path/'train'/o,
lambda o: image_to_bbox[o][0],
lambda o: image_to_bbox[o][1]]
```

For the item and batch-transforms we can use exactly the same that we have already used for our keypoint regression example.

```
item_tfms = [Resize(224)]
batch_tfms = [Rotate(),
Flip(),
Dihedral(),
Normalize.from_stats(*imagenet_stats)]
```

Now we have to get our items. We declare a noop function that stands for nooperator. With noop the function ignores any input value and always returns the same value. So with any input the function returns our list of images.

```
def get_train_images(noop): return images
```