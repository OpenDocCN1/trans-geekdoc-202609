# Machine Learning

# Chapter 13: Sequence Classification

| other versions in your apps, so be sure to check the generated code for options. |

Now go back to that comment you added earlier — // TODO predict the gesture
and replace it with a call to the method you just wrote:

```
predictGesture(window: window)
```

You already calculated the correct prediction window inside processMotionData,
and here pass that to predictGesture to perform inference.

Now build the app and run it on your iPhone. (Sorry, no data in the
sim!) You might succeed with the first gesture, but it won't take long before the
app calls out a gesture and then immediately complains that you got it wrong. What
gives?

Remember those fancy overlapping windows? Well, that backing storage
buffer may still contain data from the previous sequences we were processing.
When the app asks for a new gesture, there is a prediction window worth
just sitting there ready to be recognized — collected while you were making
t previous gesture. And don't forget, recurrent models use state from previous
predictions to help them make new predictions, because they assume the data is
related. But when this app asks for a new gesture, it no longer wants the model
toconsider the prior data. Each new gesture gets a clean state.

To this, you need to reset the buffer and the model's previous output states.
And adding the method to GameViewController:

```
func resetPredictionWindows() {
  // 1
  bufferIndex = 0
  // 2
  isDataAvailable = false
  // 3
  for i in 0..<modelOutputs.count {
    modelOutputs[i] = nil
  }
}
```

It's not much code, but it's vital in order for your app to function properly. Here's
what it does:

+   1. Reset bufferIndex to zero to start filling the buffer from the beginning again.
This ensures new predictions are based on relevant sequence data, rather than

![](bbox=[0.162, 0.923, 0.335, 0.953])

441