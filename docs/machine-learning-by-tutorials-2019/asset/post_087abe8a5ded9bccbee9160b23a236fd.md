
First, turn your model into a valid ImageClassifier object:

```
from turicreate.toolkits.image_classifier import ImageClassifier

state = {
    'classifier': lr_model,
    'model': ptModel.name,
    'max_iterations': lr_model.max_iterations,
    'feature_extractor': feature_extractor,
    'input_shape': ptModel.input_image_shape,
    'target': lr_model.target,
    'feature': 'image',
    'num_features': 1,
    'num_classes': lr_model.num_classes,
    'classes': lr_model.classes,
    'num_examples': lr_model.num_examples,
    'training_time': lr_model.training_time,
    'training_loss': lr_model.training_loss
}
model = ImageClassifier(state)
```

This combines the base model with the classifier you trained in the state structure, and creates an ImageClassifier object from this.

Calculate the test set metrics for:

```
metrics = model.evaluate(test_data)
print("Accuracy: ", metrics["accuracy"])
print("Precision: ", metrics["precision"])
print("Recall: ", metrics["recall"])
```

This prints out:

| Accuracy | 0.67128487394955 |
| Precision | 0.675591486674352 |
| Recall | 0.669818022712084 |

Regularization and hyperparameter tuning won't always work miracles, but they can improve the model, even by a little bit.

> Note: model.evaluate() performs feature extraction on the test set each time you run it. Exercise for the adventurous reader: Try digging into the Turi Create source code to see if you can make a SFrame with already extracted features. Hint: type model.evaluate?? into a new cell (yes, two question marks) to view the source code of this method.

# Saving the model

You can save the model as a Turi Create model:

```
model.save("MultiSnacks_regularized.model")
```

Or export a Core ML model:

```
model.export_coreml("MultiSnacks_regularized.mlmodel")
```

To learn more about the model, run the following:

```
model
```

This shows you some high-level information about the model and its training:

| Class | :ImageClassifier |
| --- | --- |
| Number of classes | 20 |
| Number of feature columns | 1 |
| Input image shape | (3, 227, 227) |
| Training summary | |
| Number of examples | 4838 |
| Training loss | 3952.4993 |
| Training time (sec) | 59.2703 |

Training loss — the overall error over the training dataset — changes when you change the hyperparameters. Enter and run this to see a bit more information:

```
model.classifier
```

This shows you information about the classifier portion of the model:

| Class | :LogisticClassifier |
| --- | --- |
| Number of coefficients | 19019 |
| Number of examples | 4838 |
| Number of classes | 20 |
| Number of feature columns | 1 |
| Number of features | 1000 |

# Hyperparameters

| L1 penalty | 0.0 |
| L2 penalty | 10.0 |

# Training Summary

```
Solver : lbfgs
Solver iterations : 200
Solver status : Completed (Iteration limit reached).
Training time (sec) : 59.2703
```

# Settings

| Log-likelihood | 3952.4993 |

# Highest Positive Coefficients

```
(intercept) : 1.8933
(intercept) : 1.4506
(intercept) : 0.6717
(intercept) : 0.5232
(intercept) : 0.4072
```

# Lowest Negative Coefficients

```
(intercept) : -1.6521
(intercept) : -1.5588
(intercept) : -1.4143
(intercept) : -0.8959
(intercept) : -0.5863
```

This information is mostly useful for troubleshooting or when you're just curious about how the logistic regression works. Notable is **Number of coefficients — 19019** — the number of parameters this model learned in order to classify snacks into 20 possible categories. Here's where that number comes from: each input feature has 1000 numbers, and there are 20 possible outputs, so that is 1000 × 20 = 20000 numbers, plus 20 "bias" values for each output, making 20020 coefficients. However, if there are 20 possible classes you actually only need to learn about 19 of those classes, giving 19019 coefficients. If the prediction is one of these 19 classes, then it must be the 20th class. Interestingly, in .mlmodel, the logistic regression layer has 20020 parameters. You can see this for yourself with Netron in the next section.

img/5720be5c3cca252e1244e68d25607b5_192_0.png

# Chapter 5: Digging Deeper into Turi Create

Under the Settings, Log-likelihood is the mathematical term for Training loss. Below are the highest and lowest coefficients — remember, the purpose of regularization is to reduce the size of coefficients. To compare with the coefficients of the original no-regularization model, enter and run these lines:

```
no_reg_model = tc.load_model("MultiSnacks.model")
no_reg_model.classifier
```

The pre-trained model (see the starter/notebook), and you inspect its classifier. This model had higher training accuracy, as Log-likelihood is lower: 2.40 than the model with regularization:

| Settings | |
| --- | --- |
| Log-likelihood | 0.3284 |
| Highest Positive Coefficients | |
| (intercept) | 0.3808 |
| (intercept) | 0.3799 |
| (intercept) | 0.1918 |
| image_features | 0.1864 |
| (intercept) | 0.15 |
| Lowest Negative Coefficients | |
| (intercept) | -0.3996 |
| (intercept) | -0.3856 |
| (intercept) | -0.3353 |
| (intercept) | -0.2783 |
| image_features | -0.1423 |

In the next chapter we'll talk more about all of this means, as you'll be writing code to train your own logistic regression from scratch, as well as a complete neural network that will outperform Turi Create's SqueezeNet-based model.

# A peek behind the curtain

SqueezeNet and VisionClassifier are convolutional neural networks. In the coming chapters, you'll learn more about how these networks work internally, and you'll see how to build one from scratch. In the meantime, it might be to take a peek inside your Core ML model.

There is a free tool called Netron (github.com/lutzeder/Netron) that creates a nice visualization of the model architecture. On the GitHub page, scroll down to the Install instructions, and click the macOS Download link. On the next page, click the Netron-x.x.x.dmg link, then run this file to inspect Netron.

Open your .modelfile in Netron. This shows all the transformation stages that go into your model.

The input is at the top, followed by convolutions, activations, pooling, and so on. These are the names of the different types of transformations — or layers used by this kind of neural network.

Notice how the pipeline branches and then comes again — that's the "squeeze" feature that gives SqueezeNet its name.

Click on one of these building blocks to learn more about its configuration, its inputs and its output.

img/5720be5c3cca252e1244e68d25607b5_194_0.png

Using Netron to examine the .modelfile

At the end of the pipeline is an innerProduct layer followed by something called softmax — these two blocks make up the logistic classifier. Everything until the flatten block is the SqueezeNet feature extractor.

In Chapters 6 and 7, you'll learn all about what these different kinds of layers do, but for now we suggest that you spend a few minutes with Netron to get a rough idea of what these models look like on the index.

Netron works with any Core ML model, as well as models from many other machine learning frameworks. If you downloaded a model from Apple's website in the last chapter, also take a look at that.

It should look quite similar to this, as all neural networks are alike at their core. What is different is the number of layers and the branching structure.

> Note: Apple's own models such as VisionClassifier are included in iOS 12 and do not get bundled into the .model file. The .model file itself doesn't contain any of the Vision layers. For customized models based on these built-in feature extractors, Netron can show you much more than you see in Xcode's description: inputs, outputs, metadata. The internal architecture of these models remains a mystery.

# Challenges

# Challenge 1: Binary classifier

Remember the healthy/unhealthy snacks model? Try to train that binary classifier using Siri Create. The approach is actually very similar to what you did in this chapter. The only difference is that you need to assign the label "healthy" or "unhealthy" to each row in the training data SFrame.

```
healthy = {
  'apple', 'banana', 'carrot', 'grape', 'juice', 'orange',
  'pineapple', 'salad', 'watermelon'
}

unhealthy = {
  'cake', 'candy', 'cookie', 'doughnut', 'hot dog',
  'ice cream', 'muffin', 'popcorn', 'pretzel', 'waffle'
}
```
