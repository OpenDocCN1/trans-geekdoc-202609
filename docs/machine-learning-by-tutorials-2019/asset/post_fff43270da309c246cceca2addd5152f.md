
```python
train_data["label"] = 
train_data["path"].apply(lambda path: "healthy"
  if any("/" + class_name in path for class_name in healthy) else "unhealthy"
test_data["label"] = 
test_data["path"].apply(lambda path: "healthy"
  if any("/" + class_name in path for class_name in healthy) else "unhealthy")
```

First, assign each class into a healthy or unhealthy array — there are 10 classes
in each array. Then, you set image's label column to "healthy" or
"unhealthy", depending on which image's path name is in. The result is,
you've divided 20 classes of images into two classes, based on the name of the
directory they're in.

> Note: The process to do this exercise in Create ML is much more manual.
You'd have to create a new train folder with subfolders healthy and
unhealthy, then copy or move all the images from each of the 20 food-labelled
folders into the correct healthy or unhealthy folder. You could do either in
Finder or Terminal.

Verify that the resulting model gets about 80% accuracy on the test dataset.

You may wonder why you can't use the multi-class model for this, and simply
look if the predicted category is in the list of healthy or unhealthy classes. This is
possible but, by training from scratch on just these two categories, the model has a
chance to learn what healthy/unhealthy means, and it means to use a more intricate
rule than just "this class label is in the list of healthy categories"

If you want to be sure which approach works best, use the 20-class model to
classify(the healthy/unhealthy test dataset, and merge its output with
test_data as before. The label column contains "healthy" or "unhealthy", while the
class column contains "apple," "banana," etc.

Then filter_by(healthy, "class") to find the models to predict in a
class listed the healthy array. Filter these images with
filter_by(["unhealthy"], "label") to find images that are really in unhealthy
classes. Manually calculate the accuracy of the 20-class model in predicting healthy/
unhealthy. I got 47%.

# Challenge 2: ResNet50-based model

Train the 20-class classifier using the ResNet-50 model and see if that gets a better validation and test set score. Use l_type="resnet-50" when creating the classifier object. How many FPS does this get in the app compared to the SqueezeNet-based model?

# Challenge 3: Use another dataset

Create your own training, validation, and test datasets from Google Images or some other image source. I suggest keeping the number of categories limited.

# Key points

- In this chapter, you've gotten a taste of training your Core ML model with Turi Create. In fact, this is exactly how the models were trained that you used in chapter 2, "Getting Started with Image Classification".
- Turi Create is pretty easy to use, especially from a Jupyter notebook. It only requires a little bit of Python code. We weren't able to create a super accurate model. This is partly due to the limited dataset.
- More images is better. We use 4,800 images, but 48,000 would have been better, and 4.8 million would have been better. However, there is a real cost associated with finding and annotating training images, and for most projects, a few hundred images or at most a few thousand per class may be all you can afford. Use what you got — you can always retrain the model at a later date once you've collected more training data. Data is king in machine learning, and who has the most wins.
- Another reason why Turi Create wasn't super is that SqueezeNet is a small feature extractor, which makes it fast and memory-friendly, but this also comes with a cost: It's not as accurate as bigger models. But it's not just SqueezeNet's fault — instead of training a basic logistic regression on top of SqueezeNet's extracted features, it's possible to create more powerful classifiers too.

Machine Learning

- Turi Create lets you tweak a few hyperparameters. With regularization, we can get a grip on the overfitting. However, Turi Create does not allow us to fine-tune the feature extractor or use data augmentation. Those are more advanced features, and they result in slower training times, but also in better models.

In the next chapter, we'll look at fixing all of these issues when we train our image classifier again, but this time using Keras. You'll also learn more about what all the building blocks are in these neural networks, and why we use them in the first place.

# Chapter 6: Taking Control of Training with Keras
By Matthijs Hollemans

**Update Note:** This chapter has been updated to iOS 13, Xcode 11 and Swift 5

In the previous chapters, you've learned how to train your models using Create ML and Turi Create. These are user-friendly tools that are easy to get started with — you don't really have to write a lot of code and they take care of most of the details. With just a few lines you can load your data, train your model and export to Core ML.

The downside of this approach is that Create ML and Turi Create only let you build a few model types and you don't have much control over the training process. This is fine if you're just getting your feet wet with machine learning. But once you know what you're doing and you want to get more of ML, you're going to need more powerful tools.

In this chapter, you'll use a popular deep learning tool called Keras to train the snacks classifier. Keras gives you much more control over the design of the models and how they are trained. You now know your way around Keras, you'll be able to build any kind of neural network you want.

> **Note:** You should be able to train the models on your Mac, even on older, slower machines. The models are small enough to be trained on the CPU and don't need GPU acceleration — only a little patience.

# Machine Learning Chapter 6: Taking Control of Training with Keras

Keras runs on top of a so-called backend that performs the actual computations. The most popular of these are TensorFlow, and so that is what you'll be using. TensorFlow is currently the number one machine-learning tool in existence. However, it can be a little tricky to use due to its low-level nature. Keras makes using TensorFlow a lot easier.

TensorFlow is a tool for building any computational graph, not just neural networks. It deals with rudimentary operations such as matrix multiplications and derivatives. There are higher-level abstractions in TensorFlow, but many people prefer to use Keras as it's just more convenient.

## Getting started

First, you need to set up a environment for running Keras. The quickest way is to perform these commands from a Terminal:

```bash
$ cd /path/to/resources
$ conda env create --file=kerasenv.yaml
$ conda activate kerasenv
$ jupyter notebook
```

If you downloaded the datasets for a previous chapter, copy or move it into the starter folder. Otherwise, double-click snacks-link to download and unzip the snacks in default location.

> Note: In this book we're using Keras version 2.2.4 and TensorFlow version 1.14. Keras, like many open source projects, changes often and sometimes versions are incompatible with older ones. If you're using a newer version of Keras and you get error messages, install version 2.2.4 into your environment.

**Tip:** If your computer runs Linux and has an NVIDIA GPU that supports CUDA, edit kerasenv.yaml and replace tensorflow=1.14 with tensorflow-gpu=1.14. Or if you have already created the environment, run pip install -U tensorflow-gpu==1.14. This will install the GPU version of TensorFlow, which runs faster.

# Back to basics with logistic regression

One of the keys in this book is transfer learning: a logistic regression model is trained on top of features extracted from the training images. In the case of Create ML, the features were extracted by the very powerful "VisionFeaturePrint.Scene" neural network that is built into iOS 12. In the case of Turi Create, the feature extractor you used was much less powerful SqueezeNet.

The big advantage of transfer learning is that it is much quicker than training from scratch, because your model can take advantage of the knowledge that is already contained in the pre-trained feature extractor. Hence, you are transferring knowledge from one problem domain to another. In this case, the feature extractors are trained on the general problem of recognizing objects in photos, and you'll adapt them to the specific problem of recognizing 20 different types of snacks.

We also claimed that this approach of using a feature extractor works better than training the logistic regression classifier on the image pixels directly. To demonstrate the difference, you'll use Keras to build a logistic regression model that skips the feature extraction part and works directly on pixels.

This is a good way to get started with Keras, and doing this will prove that it's very hard for a logistic regression model to learn to classify directly from pixel data. Over the course of this chapter and the next, you'll make the model more and more capable, until the end you have a classifier that is pretty darn accurate.
