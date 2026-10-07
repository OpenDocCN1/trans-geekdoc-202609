However, based on these percentages, you can't say, "This image contains an unhealthy snack." It does, but it also contains a healthy snack. With the new rule that we just added, the model would say "not sure" for this particular photo, since neither class has over 80% confidence.

It's also possible that the model predicts something like 90% healthy or unhealthy for an image like this. All bets are off, since this input image is really supposed to contain one "main" object, not multiple objects or at most multiple objects that are all from the same class. The model can't really handle images with more than one object if they are from different classes.

In any case

# How does it work?

At this point, you may be wondering exactly how this Core ML model is able to tell apart healthy snacks from unhealthy snacks. The model takes an image as input and produces a probability distribution as output, but what is the magic that makes happen? Let's peek under the hood a little.

The HealthySnacks.model is a so-called neural network classifier. You've already seen classification, but you may not know exactly what a neural network is.

Artificial networks are inspired by the human brain. The particular neural network used by HealthySnacks is a so-called "convolutional" neural network, which in many ways is similar to how the human visual cortex processes information.

Despite how they are often depicted in the popular press, it's not really that useful to think of these artificial networks as a computerized version of human brains. Artificial neural networks are only a very crude model of how the human brain works — and not nearly as complicated.

It's much more constructive to think of a neural network as a pipeline that transforms data in several stages. A machine learning model is like a Swift function:

```
let outputs = myModel(inputs)
```