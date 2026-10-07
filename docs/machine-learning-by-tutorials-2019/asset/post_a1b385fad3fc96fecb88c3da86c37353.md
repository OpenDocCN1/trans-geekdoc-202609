
- When building a dataset, prefer collecting less data from more sources over data from fewer sources.
- Inspect and clean your data before training any models to avoid wasting time on potentially invalid experiments. Be sure to check *all* your data — training, validation and testing.
- Try isolating data from a single source into one of the train, validation or test sets.
- Prefer a balanced class representation. In cases where that's not possible, evaluate your model with techniques other than accuracy, such as precision and recall.

## Where to go from here?

You have a bunch of motion data sequences organized into training, validation and test sets. Now it's time to make a model that can recognize specific gestures in them. In the next chapter, you'll use Turi Create to do just that.

# Chapter 12: Training a Model for Sequence Classification

By Chris LaPollo

> Update Note: Apple loves to keep us waiting. As of writing, the CoreML APIs needed to update this chapter weren't quite ready. As Apple releases new APIs, we'll continue to update this chapter. We'll also notify you and let you know how to access the updated versions.

In the previous chapter, you learned about collecting and analyzing sequences of data, both crucial parts of successfully using machine learning. This chapter introduces a new type of neural network specifically designed for sequential data, and you'll build one to classify the data you collected as device motions.

If you're jumping into this chapter without first gone through the previous one, you'll need a Python environment with access to Turi Create. We'll assume you have one named *turienv*, but if you don't then you can create it using the file at **projects/notebooks/turienv.yaml**. If you're unsure how to do so, refer back to Chapter 4, "Getting Started with Python & Turi Create."

# Creating a model

You've got access to a clean dataset — either the one you made in the previous chapter or we'll provide for you — and now you're ready to train a model. Or maybe several models until you find one that works well. This section shows how to use Turi Create's task-focused API to train a model for activity detection.

# Machine Learning Chapter 12: Training a Model for Sequence Classification

> **Note:** Training your own model is highly recommended, especially if you collected data to add to the provided dataset. But for whatever reason you skipped the previous chapter, you can find a trained model named **GestureClassifier.model** inside the **notebooks/pre-trained** subfolder of the chapter resources required for this chapter.

In this section you'll continue working with Jupyter in your **turienv** Anaconda environment. Create a new notebook in the **notebooks** folder of the chapter resources. If you like to see how we have trained our model, you can check out the completed notebook **notebooks/Model_Training_Complete.ipynb**.

Import the same packages as you used in the previous chapter's notebook:

```python
import turi as tc
import activity_detector_utils as utils
```

Then the following code will load your training, validation, and testing datasets:

```python
train_sf = tc.Sframe("data/cleaned_train_sframe")
valid_sf = tc.Sframe("data/cleaned_valid_sframe")
test_sf = tc.Sframe("data/cleaned_test_sframe")
```

As mentioned in the previous chapter, Turi Create stores data in SFrame objects. There are various ways to create such objects — here you load them directly from the files you previously saved. If you'd prefer to use the files supplied with the resources, change the paths to pre-trained/data/cleaned_train_sframe, pre-trained/data/cleaned_valid_sframe and pre-trained/data/cleaned_test_sframe.

Training any classifier involves multiple datasets for training, validation and testing. But dealing with sequences includes a few wrinkles that may require some explanation.

# Splitting sequence data

If you've ever trained an image classifier, you might have divided the images into training, validation and test sets randomly. Or maybe those sets were provided for you, in which case someone else divided them randomly.

This works because each image is its own sample — no one image relates or less to any other image. (See the upcoming Note for an important caveat to this statement.) But the very nature of sequences is that samples relate to each other.

# Machine Learning

# Chapter 12: Training a Model for Sequence Classification

Order and grouping matter — that's what makes them sequences! For example, if you're counting by — two, four, six, eight — and then randomly shuffle data — eight — and then randomly shuffle data — eight, four

# Machine Learning

# Chapter 12: Training a Model for Sequence Classification

![](img/5720be5c3cca252e1244868d25607b5_403_0.png)

Data collected from two users performing the same activity

These two plots show similar values for several features, but some features are quite different between users. A model trained on one of these users might have trouble recognizing the activity when presented with the more data you show your model from one, the other. It’s certainly good to collect lots of data from each source, but it’s more important to collect data from lots of sources.

If you have the chance of getting 1000 recordings from one person, versus 100 recordings from 10, the second will probably produce a better model. And 10 recordings from 100 people would probably be even better. By all means, get more data from each person you can, but definitely try to collect data as many people as possible.

And that’s the second rule for training with sequences, or really any data where the data’s source affects its features: use data from as many sources as possible. The more sources you have in your training set, the better your model should generalize to unseen examples.

But even if you have a great dataset full of examples from many different people, there’s another issue — how to split it into train, validation and test sets?

You might be tempted to split the data randomly (keeping in mind the earlier rule about maintaining samples as sequences, of course). However, you should avoid this. Remember how different recordings from the same person are similar to each other? Well, if you train with data from one person, then test with different data from the same person, your model may appear to perform better than it really does. That because it essentially trained on some of the test data.

So the third rule for training with sequences: don’t split your datasets by sequence, split them by source. Make sure you know the source of each of your data samples, and try to put all the data from any particular source into the same set: train, validation or test.
