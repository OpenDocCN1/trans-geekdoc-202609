
# Machine Learning Chapter 12: Training a Model for Sequence Classification

model to always consider its past predictions as part of the current sequence?

Well, that finally brings us back to those new items you saw in Xcode: hiddenIn, cellIn, hiddenOut and cellOut. The names may seem backwards, but cellOut is the output from the LSTM itself, while cellOut is the LSTM's internal memory state after making the prediction. And hiddenIn and cellIn are the inputs you use to pass the model outputs from the previous prediction. Each of these is a vector of 200 Doubles seen as an MLArray—you don't need to worry about that, it's just how the model's LSTM layer encodes its state information.

So to start of a new sequence, you'll pass to the model for both hiddenIn and cellIn. On the other hand, when the current prediction is picking up where the last one ended—as will be the case with streaming motion data—you’ll have the hiddenOut and cellOut values from the previous prediction and pass those back to the model as hiddenIn and cellIn, respectively. Using the output and memory from the previous step like this allows the LSTM to recognize longer sequences.

Continuing with our text example

This whole chapter has been talking about classifying sensor data, but it turns out the model you made with Turi looking at its inputs in two ways—as sequences of sensor data, and as sequences of sequences of sensor data. The prediction window contains enough information to classify the first kind of sequence, but these extra inputs and outputs allow the LSTM portion of the network over longer periods of time to classify the second kind of sequence.

While combining CNNs and LSTMs have achieved state-of-the-art results for tasks such as activity detection and speech recognition, there are also other techniques that deliver excellent performance when working with sequences. These include: Attention—a sort of memory added to other networks that guide your focus; Transformers—networks that use attention instead of recurrent or convolutional layers; and Temporal Convolutional Networks—CNNs designed for processing sequences. And new research seems to appear on a weekly basis, so there may be even more options by the time you're reading this. You'll read a bit more about some of these in later chapters.

# A note on sequence classification

In the previous section you learned about the model architecture of Turi Create's activity classifier. Recall how the final layer had a node for each class the model recognizes, with a softmax activation to produce a probability distribution over them.

We didn't underscore it, but it's important to realize that using neural networks to classify sequences works the same as it does for other types of data. You build a network with layers that make sense for the problem—convolutions, LSTMs, etc., and then a final layer of nodes—one for each output—with a softmax activation function to produce probabilities over them.

In fact, you can even use networks with this architecture to predict the next item in a sequence instead of the class of a sequence. The difference is that during training, instead of providing sequences as inputs and class as outputs, you give partial sequences as inputs and the next item in the sequence as the output. You'll get to do this in a later chapter about translating natural language.

# Key points

- Turi Create's activity API can help you easily make models capable of recognizing human activity from motion data. However, it can be used for more than just human activity detection—it's a generic classifier for numeric sequences.
- Try isolating data from a single source into one of train, validation or test sets.
- Prefer a balanced class representation. In cases where that's not possible, evaluate your model with techniques other than accuracy, such as precision and recall.
- Sample/shuffle sequential data as full sequences, not as individual rows.
- First train on a small portion of your training set and make sure you can get the model to overfit. That's the best way to find problems with your model, because if it can't overfit to a small dataset, then you likely need to make changes before it is able to learn at all.
- Train multiple models and run multiple experiments until you find what works for your app.
- RNNs process data serially, so they're slower than CNNs, both when training and performing inference.
- One-dimensional convolutions are commonly used to extract temporal features from sequences prior to passing them into RNNs.
- RNNs are a good choice for sequential data, with LSTMs being the most commonly used variant because they train.

# Where to go

You've trained a model and added it to the project. Now it's time to actually use it. In the next chapter, you'll learn how to integrate your model into an iOS app.

## Classifying human activity in your app

The project already includes the interface (not shown here) is even simpler than GestureRecorder—it’s just two buttons: Play and Instructions. Choosing Instructions shows videos of gesture, and play starts a game. While playing, the game speaks out gestures for the player to make, awarding one point for each gesture. The game ends when the app recognizes an incorrect gesture or if the player takes too long.

All the code you wrote for the rest of this chapter goes in GameViewController.swift, so open file in Xcode to get started. This file imports the Core Motion framework and includes all the necessary code to use it. Its implementations of disableMotionUpdates are almost identical to what you wrote in the GestureRecorder project. The differences are minor and you should have no problem understanding them. As was the case with project, this file contains a method named processMotionData that calls when it receives device motion data. At the moment it's empty, you implement it later. For now, import the Core ML framework by adding the following line with the other imports near the top of the:

```swift
import CoreML
```

In order to keep your code tidy and more maintainable, you’ll store numeric configuration values as constants in the Config struct at the top of the class, just like you did in the GestureRecorder project. To start, add the following three constants to struct:

```swift
static let samplesPerSecond = 25.0
static let numFeatures = 6
static let windowSize = 20
```

These values must match those of the model you trained. You’ll use samplesPerSecond to ensure the app processes motion data at the same rate as your model saw during training. The dataset provided in this chapter’s resources were collected at 25 samples per second, so that’s the value used here. Here, change value if you train your own model using data fed to it at a different rate.
