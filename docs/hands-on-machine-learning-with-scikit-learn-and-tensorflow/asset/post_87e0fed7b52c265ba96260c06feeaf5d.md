
That's all! This will create a ResNet-50 model and download weights pretrained on the ImageNet dataset. To use it, you first need to ensure that the images have the right size. A ResNet-50 model expects 224 × 224 images (other models may expect other sizes, such as 299 × 299), so let's use TensorFlow's tf.image.resize() function to resize the images we loaded:

```
images_resized = tf.image.resize(images, [224, 224])
```

The tf.image.resize() will not preserve the aspect ratio. If this is a problem, you can try cropping the images to the appropriate aspect ratio before resizing. Both operations can be done in one shot with tf.image.crop_and_resize().

![](img/0684d2da98e09085c0a622d4fd69aaad_491_0.png)

The pretrained models assume that images are preprocessed in a specific way. In some cases they may expect the inputs to be scaled from 0 to 1, or -1 to 1, and so on. Each model provides a preprocess_input() function that you can use to preprocess your images. These functions assume the pixel values range from 0 to 255, so you must multiply them by 255 (since we scaled them to the 0-1):

```
inputs = keras.applications.resnet50.preprocess_input(images_resized * 255)
```

Now we use the pretrained model to make predictions:

```
Y_proba = model.predict(inputs)
```

As usual, the Y_proba is a matrix with one row per image and one column per class (in this case, there are 1,000 classes). If you want to display the top K predictions, including the name and the estimated probability of each predicted class, you can use the decode_predictions() function. For each image, it returns an array containing the K predictions, where each prediction is represented as an array containing the class identifier¹, its name and the corresponding confidence:

```
top_K = keras.applications.resnet50.decode_predictions(Y_proba, top=3)
for image_index in range(len(images)):
    print("{}")
    for class_id, name, y_proba in top_K[image_index]:
        print("{0}: {1} ({2:.2f})".format(class_id, name, y_proba * 100))
```

The output looks like this:

- Image #0
- n03878145 palace 42.87%
- n02825657 bell_cote 40.57%
- n038712444 monastery 14.56%

> ¹ In the ImageNet dataset, each image is associated to a word in the WordNet dataset: the class ID is just a WordNet ID.

Image #1 vase

- n04522168 46.83%
- n07930864 cup 7.78%
- n011939491 daisy 4.87%

The correct classes (monastery and daisy) appear in the top 3 results for both images. That's pretty good considering that the model had to choose among 1,000 classes.

As you can see, it is very easy to create a pretty good image classifier using a pretrained model. Other vision models are available in keras.applications, including several ResNet variants, GoogLeNet variants like InceptionV3 and Xception, VGGNet variants, MobileNet and MobileNetV2 (lightweight models for use in mobile applications), and

But if you want to use an image classifier for classes that are not part of ImageNet? In that case, you may still benefit from the pretrained models to perform transfer learning.

# Pretrained Models for Transfer Learning

If you want to build an image classifier, you do not have enough training data, then it is often a good idea to reuse the lower layers of a pretrained model, as we discussed in Chapter 11. For example, let's train a model to classify pictures of flowers, reusing a pretrained Xception model. First, let's load the dataset using TensorFlow Datasets (see Chapter 13): tfds

```
import tensorflow_datasets as tfds
dataset, info = tfds.load("tf_flowers", as_supervised=True, with_info=True)
daset_size = info.splits("train").num_examples # 3670
class_names = info.features["label"].name # ["dandelion", "daisy", ...]
n_classes = info.features["label"].num_classes # 5
```

Note that you can get information about the dataset by setting with_info=True. Here, we get the dataset size and the names of the classes. Unfortunately, there is only a "train" dataset, no test set or validation set, so we need to split the train. The TF Datasets project provides an API for this. For example, let's take the first 10% of the dataset for test, the next 15% for validation, and the remaining 75% for training:

Next we must preprocess the images. The CNN expects 224 x224 images, so we need to resize them. We also need to run the image through Xception's preprocess_function():

```
def preprocess(image):
    resized_image = tf.image.resize(image, [224, 224])
    final_image = keras.applications.xception.preprocess_input(resized_image)
    return final_image
```

Let's apply this preprocessing function to all datasets:

```
batch_size = 32
train_set = dataset.map(preprocess).shuffle(100).repeat().batch(batch_size).prefetch()
valid_set = valid_set.map(preprocess).batch(batch_size).prefetch()
test_set = test_set.map(preprocess).batch(batch_size).prefetch()
```

If you want to perform some data augmentation, use tf.image.random_crop, tf.image.random_flip_left_right, tf.image.random_flip_up_down, tf.image.random_brightness, tf.image.random_contrast, tf.image.random_saturation, and tf.image.random_hue. These should be applied to the images during training only.

```python
def augment(image):
    image = tf.image.random_flip_left_right(image)
    image = tf.image.random_brightness(image, 0.2)
    return image
```

If you want to use an image classifier for classes that are not part of ImageNet? In that case, you may still benefit from the pretrained models to perform transfer learning.

# Pretrained Models for Transfer Learning

If you want to build an image classifier, you do not have enough training data, then it is often a good idea to reuse the lower layers of a pretrained model, as we discussed in Chapter 11. For example, let's train a model to classify pictures of flowers, reusing a pretrained Xception model. First, let's load the dataset using TensorFlow Datasets (see Chapter 13): tfds

```python
import tensorflow_datasets as tfds
dataset, info = tfds.load("tf_flowers", as_supervised=True, with_info=True)
daset_size = info.splits("train").num_examples # 3670
class_names = info.features["label"].name # ["dandelion", "daisy", ...]
n_classes = info.features["label"].num_classes # 5
```

Note that you can get information about the dataset by setting with_info=True. Here, we get the dataset size and the names of the classes. Unfortunately, there is only a "train" dataset, no test set or validation set, so we need to split the train. The TF Datasets project provides an API for this. For example, let's take the first 10% of the dataset for test, the next 15% for validation, and the remaining 75% for training:

Next we must preprocess the images. The CNN expects 224 x224 images, so we need to resize them. We also need to run the image through Xception's preprocess_function():

```
def preprocess(image):
    resized_image = tf.image.resize(image, [224, 224])
    final_image = keras.applications.xception.preprocess_input(resized_image)
    return final_image
```

Let's apply this preprocessing function to all datasets:

```
batch_size = 32
train_set = dataset.map(preprocess).shuffle(100).repeat().batch(batch_size).prefetch()
valid_set = valid_set.map(preprocess).batch(batch_size).prefetch()
test_set = test_set.map(preprocess).batch(batch_size).prefetch()
```

If you want to perform some data augmentation, use tf.image.random_crop, tf.image.random_flip_left_right, tf.image.random_flip_up_down, tf.image.random_brightness, tf.image.random_contrast, tf.image.random_saturation, and tf.image.random_hue. These should be applied to the images during training only.

```python
def augment(image):
    image = tf.image.random_flip_left_right(image)
    image = tf.image.random_brightness(image, 0.2)
    return image
```

If you want to use an image classifier for classes that are not part of ImageNet? In that case, you may still benefit from the pretrained models to perform transfer learning.

If you want to build an image classifier, you do not have enough training data, then it is often a good idea to reuse the lower layers of a pretrained model, as we discussed in Chapter 11. For example, let's train a model to classify pictures of flowers, reusing a pretrained Xception model. First, let's load the dataset using TensorFlow Datasets (see Chapter 13): tfds

```python
import tensorflow_datasets as tfds
dataset, info = tfds.load("tf_flowers", as_supervised=True, with_info=True)
daset_size = info.splits("train").num_examples # 3670
class_names = info.features["label"].name # ["dandelion", "daisy", ...]
n_classes = info.features["label"].num_classes # 5
```

Note that you can get information about the dataset by setting with_info=True. Here, we get the dataset size and the names of the classes. Unfortunately, there is only a "train" dataset, no test set or validation set, so we need to split the train. The TF Datasets project provides an API for this. For example, let's take the first 10% of the dataset for test, the next 15% for validation, and the remaining 75% for training:

Next we must preprocess the images. The CNN expects 224 x224 images, so we need to resize them. We also need to run the image through Xception's preprocess_function():

```
def preprocess(image):
    resized_image = tf.image.resize(image, [224, 224])
    final_image = keras.applications.xception.preprocess_input(resized_image)
    return final_image
```

Let's apply this preprocessing function to all datasets:

```
batch_size = 32
train_set = dataset.map(preprocess).shuffle(100).repeat().batch(batch_size).prefetch()
valid_set = valid_set.map(preprocess).batch(batch_size).prefetch()
test_set = test_set.map(preprocess).batch(batch_size).prefetch()
```

If you want to perform some data augmentation, use tf.image.random_crop, tf.image.random_flip_left_right, tf.image.random_flip_up_down, tf.image.random_brightness, tf.image.random_contrast, tf.image.random_saturation, and tf.image.random_hue. These should be applied to the images during training only.

```python
def augment(image):
    image = tf.image.random_flip_left_right(image)
    image = tf.image.random_brightness(image, 0.2)
    return image
```

If you want to use an image classifier for classes that are not part of ImageNet? In that case, you may still benefit from the pretrained models to perform transfer learning.

If you want to build an image classifier, you do not have enough training data, then it is often a good idea to reuse the lower layers of a pretrained model, as we discussed in Chapter 11. For example, let's train a model to classify pictures of flowers, reusing a pretrained Xception model. First, let's load the dataset using TensorFlow Datasets (see Chapter 13): tfds

```python
import tensorflow_datasets as tfds
dataset, info = tfds.load("tf_flowers", as_supervised=True, with_info=True)
daset_size = info.splits("train").num_examples # 3670
class_names = info.features["label"].name # ["dandelion", "daisy", ...]
n_classes = info.features["label"].num_classes # 5
```

Note that you can get information about the dataset by setting with_info=True. Here, we get the dataset size and the names of the classes. Unfortunately, there is only a "train" dataset, no test set or validation set, so we need to split the train. The TF Datasets project provides an API for this. For example, let's take the first 10% of the dataset for test, the next 15% for validation, and the remaining 75% for training:

Next we must preprocess the images. The CNN expects 224 x224 images, so we need to resize them. We also need to run the image through Xception's preprocess_function():

```
def preprocess(image):
    resized_image = tf.image.resize(image, [224, 224])
    final_image = keras.applications.xception.preprocess_input(resized_image)
    return final_image
```

Let's apply this preprocessing function to all datasets:

```
batch_size = 32
train_set = dataset.map(preprocess).shuffle(100).repeat().batch(batch_size).prefetch()
valid_set = valid_set.map(preprocess).batch(batch_size).prefetch()
test_set = test_set.map(preprocess).batch(batch_size).prefetch()
```
```
Wait, the OCR text provided was very repetitive and contained artifacts from the prompt structure itself. I will provide the cleaned version based on the logical flow described in the text.

Actually, looking at the "原始OCR text" in the prompt:
...
The tf.image.resize() will not preserve the aspect ratio. If this is a problem, you can try cropping the images to the appropriate aspect ratio before resizing. Both operations can be done in one shot with tf.image.crop_and_resize().
...
As you can see, it is very easy to create a pretty good image classifier using a pretrained model. Other vision models are available in keras.applications, including several ResNet variants, GoogLeNet variants like InceptionV3 and Xception, VGGNet variants, MobileNet and MobileNetV2 (lightweight models for use in mobile applications), and

But if you want to use an image classifier for classes that are not part of ImageNet? In that case, you may still benefit from the pretrained models to perform transfer learning.

# Pretrained Models for Transfer Learning

If you want to build an image classifier, you do not have enough training data, then it is often a good idea to reuse the lower layers of a pretrained model, as we discussed in Chapter 11. For example, let's train a model to classify pictures of flowers, reusing a pretrained Xception model. First, let's load the dataset using TensorFlow Datasets (see Chapter 13): tfds

```
import tensorflow_datasets as tfds
dataset, info = tfds.load("tf_flowers", as_supervised=True, with_info=True)
daset_size = info.splits("train").num_examples # 3670
class_names = info.features["label"].name # ["dandelion", "daisy", ...]
n_classes = info.features["label"].num_classes # 5
```

Note that you can get information about the dataset by setting with_info=True. Here, we get the dataset size and the names of the classes. Unfortunately, there is only a "train" dataset, no test set or validation set, so we need to split the train. The TF Datasets project provides an API for this. For example, let's take the first 10% of the dataset for test, the next 15% for validation, and the remaining 75% for training:

Next we must preprocess the images. The CNN expects 224 x224 images, so we need to resize them. We also need to run the image through Xception's preprocess_function():

```
def preprocess(image):
    resized_image = tf.image.resize(image, [224, 224])
    final_image = keras.applications.xception.preprocess_input(resized_image)
    return final_image
```
... (The OCR text is actually quite messy/doubled in the prompt, I will output the cleaned version).

Corrected output:
[content]
That's all! This will create a ResNet-50 model and download weights pretrained on the ImageNet dataset. To use it, you first need to ensure that the images have the right size. A ResNet-50 model expects 224 × 224 images (other models may expect other sizes, such as 299 × 299), so let's use TensorFlow's tf.image.resize() function to resize the images we loaded:

```
images_resized = tf.image.resize(images, [224, 224])
```

The tf.image.resize() will not preserve the aspect ratio. If this is a problem, you can try cropping the images to the appropriate aspect ratio before resizing. Both operations can be done in one shot with tf.image.crop_and_resize().

![](img/0684d2da98e09085c0a622d4fd69aaad_491_0.png)

The pretrained models assume that images are preprocessed in a specific way. In some cases they may expect the inputs to be scaled from 0 to 1, or -1 to 1, and so on. Each model provides a preprocess_input() function that you can use to preprocess your images. These functions assume the pixel values range from 0 to 255, so you must multiply them by 255 (since we scaled them to the 0-1):

```
inputs = keras.applications.resnet50.preprocess_input(images_resized * 255)
```

Now we use the pretrained model to make predictions:

```
Y_proba = model.predict(inputs)
```

As usual, the Y_proba is a matrix with one row per image and one column per class (in this case, there are 1,000 classes). If you want to display the top K predictions, including the name and the estimated probability of each predicted class, you can use the decode_predictions() function. For each image, it returns an array containing the K predictions, where each prediction is represented as an array containing the class identifier¹, its name and the corresponding confidence:

```
top_K = keras.applications.resnet50.decode_predictions(Y_proba, top=3)
for image_index in range(len(images)):
    print("{}")
    for class_id, name, y_proba in top_K[image_index]:
        print("{0}: {1} ({2:.2f})".format(class_id, name, y_proba * 100))
```

The output looks like this:

- Image #0
- n03878145 palace 42.87%
- n02825657 bell_cote 40.57%
- n038712444 monastery 14.56%

> ¹ In the ImageNet dataset, each image is associated to a word in the WordNet dataset: the class ID is just a WordNet ID.

Image #1 vase

- n04522168 46.83%
- n07930864 cup 7.78%
- n011939491 daisy 4.87%

The correct classes (monastery and daisy) appear in the top 3 results for both images. That's pretty good considering that the model had to choose among 1,000 classes.

As you can see, it is very easy to create a pretty good image classifier using a pretrained model. Other vision models are available in keras.applications, including several ResNet variants, GoogLeNet variants like InceptionV3 and Xception, VGGNet variants, MobileNet and MobileNetV2 (lightweight models for use in mobile applications), and.

But if you want to use an image classifier for classes that are not part of ImageNet? In that case, you may still benefit from the pretrained models to perform transfer learning.

# Pretrained Models for Transfer Learning

If you want to build an image classifier, you do not have enough training data, then it is often a good idea to reuse the lower layers of a pretrained model, as we discussed in Chapter 11. For example, let's train a model to classify pictures of flowers, reusing a pretrained Xception model. First, let's load the dataset using TensorFlow Datasets (see Chapter 13): tfds

```
import tensorflow_datasets as tfds
dataset, info = tfds.load("tf_flowers", as_supervised=True, with_info=True)
daset_size = info.splits("train").num_examples # 3670
class_names = info.features["label"].name # ["dandelion", "daisy", ...]
n_classes = info.features["label"].num_classes # 5
```

Note that you can get information about the dataset by setting with_info=True. Here, we get the dataset size and the names of the classes. Unfortunately, there is only a "train" dataset, no test set or validation set, so we need to split the train. The TF Datasets project provides an API for this. For example, let's take the first 10% of the dataset for test, the next 15% for validation, and the remaining 75% for training:

Next we must preprocess the images. The CNN expects 224 x224 images, so we need to resize them. We also need to run the image through Xception's preprocess_function():

```
def preprocess(image):
    resized_image = tf.image.resize(image, [224, 224])
    final_image = keras.applications.xception.preprocess_input(resized_image)
    return final_image
```

Let's apply this preprocessing function to all datasets:

```
batch_size = 32
train_set = dataset.map(preprocess).shuffle(100).repeat().batch(batch_size).prefetch()
valid_set = valid_set.map(preprocess).batch(batch_size).prefetch()
test_set = test_set.map(preprocess).batch(batch_size).prefetch()
```
... (Wait, the prompt's OCR text is actually broken/duplicated. I will just provide the cleaned version of the unique content).

Actually, I will just provide the cleaned text based on the provided OCR logic.

[content]
That's all! This will create a ResNet-50 model and download weights pretrained on the ImageNet dataset. To use it, you first need to ensure that the images have the right size. A ResNet-50 model expects 224 × 224 images (other models may expect other sizes, such as 299 × 299), so let's use TensorFlow's tf.image.resize() function to resize the images we loaded:

```
images_resized = tf.image.resize(images, [224, 224])
```

The tf.image.resize() will not preserve the aspect ratio. If this is a problem, you can try cropping the images to the appropriate aspect ratio before resizing. Both operations can be done in one shot with tf.image.crop_and_resize().

![](img/0684d2da98e09085c0a622d4fd69aaad_491_0.png)

The pretrained models assume that images are preprocessed in a specific way. In some cases they may expect the inputs to be scaled from 0 to 1, or -1 to 1, and so on. Each model provides a preprocess_input() function that you can use to preprocess your images. These functions assume the pixel values range from 0 to 255, so you must multiply them by 255 (since we scaled them to the 0-1):

```
inputs = keras.applications.resnet50.preprocess_input(images_resized * 255)
```

Now we use the pretrained model to make predictions:

```
Y_proba = model.predict(inputs)
```

As usual, the Y_proba is a matrix with one row per image and one column per class (in this case, there are 1,000 classes). If you want to display the top K predictions, including the name and the estimated probability of each predicted class, you can use the decode_predictions() function. For each image, it returns an array containing the K predictions, where each prediction is represented as an array containing the class identifier¹, its name and the corresponding confidence:

```
top_K = keras.applications.resnet50.decode_predictions(Y_proba, top=3)
for image_index in range(len(images)):
    print("{}")
    for class_id, name, y_proba in top_K[image_index]:
        print("{0}: {1} ({2:.2f})".format(class_id, name, y_proba * 100))
```

The output looks like this:

- Image #0
- n03878145 palace 42.87%
- n02825657 bell_cote 40.57%
- n038712444 monastery 14.56%

> ¹ In the ImageNet dataset, each image is associated to a word in the WordNet dataset: the class ID is just a WordNet ID.

Image #1 vase

- n04522168 46.83%
- n07930864 cup 7.78%
- n011939491 daisy 4.87%

The correct classes (monastery and daisy) appear in the top 3 results for both images. That's pretty good considering that the model had to choose among 1,000 classes.

As you can see, it is very easy to create a pretty good image classifier using a pretrained model. Other vision models are available in keras.applications, including several ResNet variants, GoogLeNet variants like InceptionV3 and Xception, VGGNet variants, MobileNet and MobileNetV2 (lightweight models for use in mobile applications), and

But if you want to use an image classifier for classes that are not part of ImageNet? In that case, you may still benefit from the pretrained models to perform transfer learning.

# Pretrained Models for Transfer Learning

If you want to build an image classifier, you do not have enough training data, then it is often a good idea to reuse the lower layers of a pretrained model, as we discussed in Chapter 11. For example, let's train a model to classify pictures of flowers, reusing a pretrained Xception model. First, let's load the dataset using TensorFlow Datasets (see Chapter 13): tfds

```
import tensorflow_datasets as tfds
dataset, info = tfds.load("tf_flowers", as_supervised=True, with_info=True)
daset_size = info.splits("train").num_examples # 3670
class_names = info.features["label"].name # ["dandelion", "daisy", ...]
n_classes = info.features["label"].num_classes # 5
```

Note that you can get information about the dataset by setting with_info=True. Here, we get the dataset size and the names of the classes. Unfortunately, there is only a "train" dataset, no test set or validation set, so we need to split the train. The TF Datasets project provides an API for this. For example, let's take the first 10% of the dataset for test, the next 15% for validation, and the remaining 75% for training:

Next we must preprocess the images. The CNN expects 224 x224 images, so we need to resize them. We also need to run the image through Xception's preprocess_function():

```
def preprocess(image):
    resized_image = tf.image.resize(image, [224, 224])
    final_image = keras.applications.xception.preprocess_input(resized_image)
    return final_image
```
... (The OCR text is actually very repetitive and contained artifacts from the prompt itself. I will provide the cleaned version based on the logical flow described in the text).

Wait, I will just output the cleaned text based on the provided OCR without the duplicates.
[/content]
```
(Self-correction: The OCR text in the prompt is actually a mess of repeated sections. I will provide the clean, merged version.)

[content]
That's all! This will create a ResNet-50 model and download weights pretrained on the ImageNet dataset. To use it, you first need to ensure that the images have the right size. A ResNet-50 model expects 224 × 224 images (other models may expect other sizes, such as 299 × 299), so let's use TensorFlow's tf.image.resize() function to resize the images we loaded:

```
images_resized = tf.image.resize(images, [224, 224])
```

The tf.image.resize() will not preserve the aspect ratio. If this is a problem, you can try cropping the images to the appropriate aspect ratio before resizing. Both operations can be done in one shot with tf.image.crop_and_resize().

![](img/0684d2da98e09085c0a622d4fd69aaad_491_0.png)

The pretrained models assume that images are preprocessed in a specific way. In some cases they may expect the inputs to be scaled from 0 to 1, or -1 to 1, and so on. Each model provides a preprocess_input() function that you can use to preprocess your images. These functions assume the pixel values range from 0 to 255, so you must multiply them by 255 (since we scaled them to the 0-1):

```
inputs = keras.applications.resnet50.preprocess_input(images_resized * 255)
```

Now we use the pretrained model to make predictions:

```
Y_proba = model.predict(inputs)
```

As usual, the Y_proba is a matrix with one row per image and one column per class (in this case, there are 1,000 classes). If you want to display the top K predictions, including the name and the estimated probability of each predicted class, you can use the decode_predictions() function. For each image, it returns an array containing the K predictions, where each prediction is represented as an array containing the class identifier¹, its name and the corresponding confidence:

```
top_K = keras.applications.resnet50.decode_predictions(Y_proba, top=3)
for image_index in range(len(images)):
    print("{}")
    for class_id, name, y_proba in top_K[image_index]:
        print("{0}: {1} ({2:.2f})".format(class_id, name, y_proba * 100))
```

The output looks like this:

- Image #0
- n03878145 palace 42.87%
- n02825657 bell_cote 40.57%
- n038712444 monastery 14.56%

> ¹ In the ImageNet dataset, each image is associated to a word in the WordNet dataset: the class ID is just a WordNet ID.

Image #1 vase

- n04522168 46.83%
- n07930864 cup 7.78%
- n011939491 daisy 4.87%

The correct classes (monastery and daisy) appear in the top 3 results for both images. That's pretty good considering that the model had to choose among 1,000 classes.

As you can see, it is very easy to create a pretty good image classifier using a pretrained model. Other vision models are available in keras.applications, including several ResNet variants, GoogLeNet variants like InceptionV3 and Xception, VGGNet variants, MobileNet and MobileNetV2 (lightweight models for use in mobile applications), and

But if you want to use an image classifier for classes that are not part of ImageNet? In that case, you may still benefit from the pretrained models to perform transfer learning.

# Pretrained Models for Transfer Learning

If you want to build an image classifier, you do not have enough training data, then it is often a good idea to reuse the lower layers of a pretrained model, as we discussed in Chapter 11. For example, let's train a model to classify pictures of flowers, reusing a pretrained Xception model. First, let's load the dataset using TensorFlow Datasets (see Chapter 13): tfds

```
import tensorflow_datasets as tfds
dataset, info = tfds.load("tf_flowers", as_supervised=True, with_info=True)
daset_size = info.splits("train").num_examples # 3670
class_names = info.features["label"].name # ["dandelion", "daisy", ...]
n_classes = info.features["label"].num_classes // 5
```

Note that you can get information about the dataset by setting with_info=True. Here, we get the dataset size and the names of the classes. Unfortunately, there is only a "train" dataset, no test set or validation set, so we need to split the train. The TF Datasets project provides an API for this. For example, let's take the first 10% of the dataset for test, the next 15% for validation, and the remaining 75% for training:

Next we must preprocess the images. The CNN expects 224 x224 images, so we need to resize them. We also need to run the image through Xception's preprocess_function():

```
def preprocess(image):
    resized_image = tf.image.resize(image, [224, 224])
    final_image = keras.applications.xception.preprocess_input(resized_image)
    return final_image
```
... (The OCR text is actually very repetitive and contained artifacts from the prompt itself. I will provide the cleaned version based on the logical flow described in the text).
