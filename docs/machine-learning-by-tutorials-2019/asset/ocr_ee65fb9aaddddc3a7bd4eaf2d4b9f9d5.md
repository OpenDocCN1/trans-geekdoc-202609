Note: In case it's not clear which app's samplesPerSecond must match that of the dataset used to train your model, consider this example: Imagine you trained your model using a prediction window of 200 samples, data collected at 100 samples per second. That means the model would learn to recognize actions in highly detailed, two-second chunks. If you then run this app with samplesPerSecond set to 8, it would take 20 seconds to gather the expected 200 samples! Your model would then look at 20 seconds of data but evaluate it as if two seconds worth, because that's how it learned. This would almost certainly make the patterns in these sequences appear different from what the model saw during training. Remember, machine learning models only work well with data that is similar to what they saw during training, so getting the sampling rate wrong here could make a perfect model seem completely broken.

Likwise, the model discussed in this chapter expects data in blocks of 20 samples at a time, with six features for each sample. The windowSize and numFeatures constants capture those expectations.

> Note: If you're ever working with a Puri Create activity classifier and aren't sure about its expected number of features and window size, you can find them by looking at the .model file in Xcode's Project Navigator. However, this does not include information about the rate at which motion data needs to be processed, so you'll just to know.

Now that you've added those constants, you can complete the starter code's implementation of enableMotionUpdates by setting the CMotionManager's update interval. To do so, add the following line inside enableMotionUpdates, just before the call to startDeviceMotionUpdates:

```
motionManager.deviceMotionUpdateInterval = 1.0 / Config.samplesPerSecond
```

Just like in GestureDataRecord, this tells MotionManager to deliver updates to your app 25 times per second — once every 0.04 seconds.

Core ML models, such as GestureClassifier, expect their input in the form of MLMultiArray objects. Unfortunately, working with these objects involves quite a bit of type casting. Swift's type safety is great, and explicit type casting forces developers to be more thorough about their code — but I think we can all agree