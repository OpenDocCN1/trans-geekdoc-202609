# Machine Learning

pretty ugly when there's too much casting on. To keep that ugliness — and the extra typing it requires — to a minimum, you'll be isolating MLMultiArray-specific code within convenience methods. Add the first of these methods below the MARK: Core ML methods in GameViewController:

```
static func makeMLMultiArray(numSamples: Int) ->
MLMultiArray? {
    return try MLMultiArray(
        shape: [1, numSamples, Config.numFeatures] as [NSNumber],
        dataType: MLMultiArrayDataType.double
    )
```

This function takes as input the number of samples the array should contain. Then it attempts to make an MLMultiArray with a shape and data type that will work with our model: [1, numSamples, Config.numFeatures] and double, respectively. Notice how the shape needs to be cast as an array of NSNumber — you'll see a lot of those types of casts when dealing with MLMultiArrays.

Attempting to create an MLMultiArray can fail by throwing an exception. If that occurs here, the try? causes this function to return nil. This might occur in situations such as when there is insufficient memory to create the requested array. Hopefully it doesn't ever happen, but you'll add some code to deal with that possibility a bit later.

Now that you have that function, you'll use it to create space to store motion data to use as input to your model. Add the following property, time to the area under the // MARK: Core ML properties comment:

```
let modelInput: MLMultiArray =
GameViewController.makeMLMultiArray(numSamples:
Config.windowSize)
```

This creates the modelInput array, appropriately sized for the model you trained. Later you'll populate this array with motion data prior to passing it to your model for classification.

> Note: You may have noticed that modelInput is declared as an implicitly unwrapped optional, makeMLMultiArray can return nil. Doesn't that mean you run the risk of crashing your app elsewhere if you try to unwrap modelInput when it's nil? Normally, that would be a problem, but later you'll add some code that ensures this can never happen.

raywenderlich.com 427