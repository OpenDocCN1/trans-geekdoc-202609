# Machine Learning Chapter 11: Data Collection for Sequence Classification

device motion API is often a better choice. Data directly from the sensors is often noisy and requires some preprocessing to smooth it. But the good folks at Apple have already worked out some preprocessing steps and do for you if you access the device motion data instead. Another nice touch — it separates acceleration from the user acceleration due to gravity, which makes the motion reported by the data easier to decipher.

However, if you ever want data from those sensors, CMMotionManager provides APIs that manage that device motion. So deviceMotionUpdateInterval, startDeviceMotionUpdates, etc., become accelerometerUpdateInterval, startAccelerometerUpdates, and so on. Similar methods exist for each sensor.

> Note: There are also versions of startDeviceMotionUpdates, startAccelerometerUpdates, etc. that take no parameters. These methods quickly update properties on the CMMotionManager, such as deviceMotion and accelerometerData. For some apps, it makes sense to use these methods instead of the ones that take parameters, and then poll the properties directly when you send sensor data.

Now that you've defined enableMotionUpdates, find the comment that reads // TODO: enable Core Motion inside the Utterances.sessionStart case in speechSynthesizer, and add a call to your new method here:

```
case Utterances.sessionStart:
// TODO: enable Core Motion
enableMotionUpdates()
queueNextActivity()
```

Most of the timing in GestureDataRecorder actually comes from logic in speechSynthesizer. The appSpeechSynthesizer calls this function whenever it finishes a phrase, and the app uses the finished utterance to determine what to next. In the case of the sessionStart message, it enables motion updates and calls queueNextActivity to get the recording started.

You've started motion updates, you'll need to stop them at some point. Add the following method to ViewController to do:

```
func disableMotionUpdates() {
  motionManager.stopDeviceMotionUpdates()
}
```

![](bbox=[0.162, 0.923, 0.837, 0.955])