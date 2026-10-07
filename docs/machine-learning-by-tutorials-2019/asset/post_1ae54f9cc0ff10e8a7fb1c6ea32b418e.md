
# Machine Learning Chapter 2: Getting Started with Image Classification

Most importantly for you, Vision makes it easy to run Core ML models that take images as input. You can even combine this with other Vision tasks to ensure an image-processing pipeline. For example, in an app that detects people's emotions, you can build a Vision pipeline that first detects a face in the image and then runs a Core ML-based classifier on that face to see whether the person is smiling or frowning.

It's highly recommended that you use Vision to run Core ML if you're working with images. Recall that the HealthySnacks model needs a 227x227 image as input, and images from the photo library or the camera will be much larger and are typically not square. Vision will automatically resize and crop the image.

In the automatically generated Swift file for the .model, you may have noticed that the input image (see HealthySnacksInput) has a CVPixelBuffer, while UIImage gives you a UIImage instead. Vision can do conversion for you, so you don't have to worry about CVPixelBuffer.

Finally, Vision performs a few other tricks, such as rotating the image so that it's always right-side up, and matching the image's color to the device's color space. Without the Vision framework, you'd have to write a lot of additional code! Surely, you'll agree that it's much more convenient to let Vision handle all these things.

> Note: Of course, if you're using a model that does not take images as input, you can't use Vision. In that case, you'll have to use the Core ML API directly.

The Vision shows that you create a VNRequest object, which describes the task you want to perform, and then you use a VNImageRequestHandler to execute the request. Since you'll use Vision to run a Core ML model, the request is a subclass named VNCoreMLRequest. Let's write some code:

## Creating the VNCoreML request

To add image classification to the app, you're going to implement classify(image:) in ViewController.swift. This method is currently empty.

Here, you'll use Vision to run the Core ML model and interpret its results. First, add the required imports to the top of the file:

```swift
import CoreML
import Vision
```

Next, you need to create the VNCoreMLRequest object. You typically create this request object once and re-use it for every image that you want to classify. Don't create a new request object every time you want to classify an image — that's wasteful.

In ViewController.swift, add the following code inside the ViewController class near the @IBOutlets:

```swift
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

- 1. Create an instance of HealthySnacks. This is the class from the .mlmodel file's automatically generated code. You won't use this class directly, so only you can pass its MLModel object to Vision.

- 2. Create a VNCoreMLModel object. This is a wrapper object that connects the MLModel instance from the Core ML framework with Vision.

- 3. Create the VNCoreMLRequest object. This object will perform the actual actions of converting the input image to a CVPixelBuffer, scaling it to 227×227, running the Core Model, interpreting the results, and so on.

Since Vision requests run asynchronously, you can supply a completion handler that will receive the results. For now, the completion handler just prints something to the Xcode debug output panel. You will flesh this out later.

- 4. The imageCropScaleOption tells Vision how it should resize the photo down to the 227×227 pixels that the model expects.

The code is wrapped in a do-catch because loading the VNCoreMLModel can fail if the .mlmodel file is invalid somehow. That should never happen in this example project, so you handle this kind of error by crashing the app. It is possible for apps to download an .mlmodel file and, if the download fails, the .mlmodel can get corrupted. In that case, you'll want to handle this in a more graceful way.

> Note: The classificationRequest variable is a lazy property. In case you're unfamiliar with lazy properties, this just means that the VNCoreMLRequest is not created until the very first time you use classificationRequest in the app.

## Crop and scale options

It has been mentioned a few times now that the model you are using, which is based on SqueezeNet, requires input images that are 227×227 pixels. Since you're using Vision, you don't really need to worry about this — Vision will automatically scale the image to the correct size. However, there is more than one way to resize an image, and you may need to choose the correct method for the model, otherwise it might not work as well as you'd hoped.

The correct method is for your model depends on how it was trained. For the Healthy Snacks app, you'll use .centerCrop as that's the resizing strategy that was used to train. Just make sure that the object you're pointing the camera at is near the center of the picture. Feel free to try out the scaling options to see what kind of difference they make, if any.

Vision offers three possible choices:

- centerCrop
- scaleFill
- scaleFit

The .centerCrop option first resizes the image so that the smallest side is 227 pixels, and then it crops out the part of the image that extends outside the square. Note that this removes pixels from the left and right edges of the image (or top/bottom if the image is in portrait).

With .scaleFill, the image gets resized to 227x227 without removing anything, but if the original wasn't square then it gets squashed. Finally, .scaleFit keeps the aspect ratio intact by filling in the rest with pixels.

## Performing the request

Now that you have the request object, you can implement the classify(image:) method. Add the following code to method:

```swift
func classify(image: UIImage) {
  // 1
  guard let image = CIImage(image: image) else {
    print("Unable to create CIImage")
    return
  }
  // 2
  let orientation = CGImagePropertyOrientation(image.orientation)
  // 3
  DispatchQueue.global(qos: .userInitiated).async {
    // 4
    let handler = VNImageRequestHandler(ciImage: image, orientation: orientation)
    do {
      try handler.perform([self.classificationRequest])
    } catch {
      print("Failed to perform classification: \(error)")
    }
  }
}
```

The image you get from UIPPickerController is a UIImage object but Vision prefers to work with CIImage or CIImage objects. Either will work fine, and they're both easy to obtain from the original UIImage. The advantage of using a CIImage is that this lets you apply additional Core Image transformations to the image, for more advanced image processing.

Here is what the method does, step-by-step:

- 1. Converts the UIImage to a CIImage object.

- 2. The UIImage has an orientation property that describes which way is up when the image is to be drawn. For example, if the orientation is "down", then the image should be rotated 180 degrees. You need to tell Vision about the image's orientation so that it can rotate the image if necessary, since Core ML expects images to be upright.
