# Machine Learning Chapter 2: Getting Started with Image Classification

Next, you need to create the VNCoreMLRequest object. You typically create this request object once and re-use it for every image that you want to classify. Don't create a new request object every time you want to classify an image — that's wasteful.

In ViewController.swift, add the following code inside the ViewController class near the @IBOutlets:

```
lazy var classificationRequest: VNCoreMLRequest = {
  do {
    // 1
    let healthySnacks = HealthySnacks()
    // 2
    let visionModel = try VNCoreMLModel(for: healthySnacks.model)
    // 3
    let request = VNCoreMLRequest(model: visionModel, completionHandler: {
      [weak self] request, error in
        print("Request is finished!", request.results)
    })
    // 4
    request.imageCropScaleOption = .centerCrop
    return request
  } catch {
    fatalError("Failed to create VNCoreMLModel: \(error)")
  }
}()
```

Here's what this code does:

+   1. Create an instance of HealthySnacks. This is the class from the .mlmodel file's automatically generated code. You won't use this class directly, so only you can pass its MLModel object to Vision.

+   2. Create a VNCoreMLModel object. This is a wrapper object that connects the MLModel instance from the Core ML framework with Vision.

+   3. Create the VNCoreMLRequest object. This object will perform the actual actions of converting the input image to a CixelBuffer, scaling it to 227×227, running the Core Model, interpreting the results, and so on.

Since Vision requests run asynchronously, you can supply a completion handler that will receive the results. For now, the completion handler just prints something to the Xcode debug output panel. You will flesh this out later.

+   4. The imageCropScaleOption tells Vision how it should resize the photo down to the 227×227 pixels that the model expects.