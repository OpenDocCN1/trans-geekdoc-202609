
# Machine Learning Chapter 8: Advanced Convolutional Neural Networks

Recall for banana is high, 0.96, so the images that contained bananas were often correctly found by the model. The recall for ice cream is low at 74%, so over one-fourth of the ice cream images were classified as something else. To verify this in Python:

```python
# Get the class index for ice cream
idx = test_generator.class_indices["ice cream"]

# Find how many images are supposed to be ice cream
total_expected = np.sum(target_labels == idx)

# How many ice cream images did we find?
correct = conf[idx, idx]

# The recall is then the true positives divided by
# the true positives + false negatives
recall = correct / total_expected
print(recall)
```

This should print 0.74. The more false negatives are there, i.e., things that are wrongly predicted to not be class X, the lower the recall for X.

The classification report also includes the F1-score. This is a combination of precision and recall and is useful if you want to get an average of the two.

The classes with the highest F1-score are grape and juice, but at 0.95. You can safely say that this classifier works very well for images with grapes or juices. The class with the lowest F1-score, 0.73, is cake. If you wanted to improve this classifier, the first thing you might want to find is more and better training images for the cake category.

> Note: It's useful to be able to write a bit of Python code. Often you'll need to write short code snippets like the above to take a closer look at the predictions. Get comfortable with Python if you're interested in building your own models!

# What are the worst predictions?

The confusion matrix and precision-recall report can already give hints about things you can do to improve the model. There are other useful things you can do. You've already seen that cake category is the worst overall. It can also be enlightening to look at images that were predicted wrongly but have very high confidence scores. The "most wrong" predictions. Why is the model so confident, yet so wrong about these images?

For example, you can use the following code to find the images that was the most wrong about. It uses some advanced NumPy sorcery:

```python
# Find which images the predicted class is wrong
wrong_images = np.where(predicted_labels != target_labels)

# For every prediction, find the largest probability value;
# this is the probability of the winning class for this image
probs_max = np.max(probabilities, axis=-1)

# Sort the predictions from the wrong images from low to high
idx = np.argsort(probs_max[wrong_images])

# Reverse the order (high to low), and keep the 5 highest ones
idx = idx[::-1][:5]
```

index2class = {v:k for k,v in test_generator.class_indices.items()}

```python
for i in worst_predictions:
   print("%s was predicted as '%s' %.4f" % (
      test_generator.filenames[i],
      index2class[predicted_labels[i]],
      probs_max[i]))
```

This will output:

strawberry/09d01416c00b309.jpg was predicted as 'salad' 0.9999
apple/61792276d92cee4.jpg was predicted as 'pineapple' 0.9907
muffin/3b25998aa3c7fab7ac.jpg was predicted as 'cake' 0.9889
papple/0eebbf643d79a23.jpg was predicted as 'banana' 0.9897
pake/bc41ce2f8c783cd5.jpg was predicted as 'waffle' 0.9885

It can also be instructive to actually look at those images:

```python
from keras.preprocessing import image
img = image.load_img(test_data_dir + 
test_generator.filenames[worst_predictions[0]])
plt.imshow(img)
```

Yep, it's not hard to see why the model got confused, here. You could make a good case that this image is labeled wrong in the test set — or at least is very misleading:

![](img/5720be5c3cca252e12448e68d25607b5_299_0.png)

The worst prediction... or is it?

# A note on imbalanced classes

There is much more to say about image classifiers than we have room for this book. One topic that comes up a lot is how to deal with imbalanced data.

In a binary classifier that needs to distinguish between disease present (positive) and not present (negative) in X-ray images, most X-rays will not show any disease at all. That's good for the patients, but it also makes a harder job for the classifier. If the disease happens to happen 1% of the patients, the classifier could simply always predict “disease not present” and it would be correct 99% of the time. But such a classifier is pretty useless... 99% correct sounds impressive, but it's not always good enough.

Or say you want to train a classifier that can distinguish between the following: cat, dog, neither cat or dog. In order to train such a classifier, you obviously need pictures of cats and dogs, but also pictures of things that are not cats and dogs. This last category must be much larger because it needs to cover a wide variety of objects, and the classifier will need to lump all of them into the “not cat or dog” category. The risk is that the classifier will only learn about one big category and not about the cat and dog categories, which have many fewer images.

There are various techniques you can use to deal with class imbalance, such as oversampling you use the images from the smaller categories more often, undersampling where you use fewer images from the larger categories, or setting weights on the classes so that the bigger category has a smaller effect on the loss.

Turi Create Create ML currently have no options for this, so if you need to build a classifier for an imbalanced dataset, Keras is a better choice.

Here ends our discussion of how to train image classifiers. Next up, you'll learn how to convert the trained Keras model to a Core ML model that you can use in your iOS and macOS apps.

# Converting to Core ML

When you write model.save("name.h5") or use theCheckpoint callback, Keras saves the model in its own format, HDF5. In order to use this model from Keras, you have to convert it to a .model file first. For this you'll need to use the coremltools Python package.

The kerasenv environment already has coremltools installed. Just in case you need to install it by hand, type this into a command prompt:

```bash
pip install -U coremltools
```

You can enter the following commands into the Lypter notebook, or follow along MobileNet.ipynb. This chapter's resources also include a separate Python script, convert-to-coreml.py that loads the model from.

First, import the package:

```python
import coremltools
```

You may get some warning messages at this point about incompatible versions. These tools change quite than coreml can keep up with, but usually, these warnings are not a problem.

# Machine Learning Chapter8: Advanced Convolutional Neural Networks

Since this is a classifier model, coreml needs to know what the label names are. It's important that they are in the same order as train_generator.class_indices:

```python
labels = ["apple", "banana", "cake", "candy", "carrot", "cookie", "doughnut", "grape", "hot dog", "ice cream", "juice", "muffin", "orange", "pineapple", "popcorn", "salad", "waffle", "watermelon"]
```

Now, you can use Keras converter to create a Core ML model:

```python
coreml_model = coremltools.convert.keras.convert(best_model, 
    input_names="image", 
    image_input_names="image", 
    output_names="labelProbability", 
    predicted_feature_name="label", 
    red_bias=-1, 
    green_bias=-1, 
    blue_bias=-1, 
    image_scale=2/255.0, 
    class_labels=labels)
```
