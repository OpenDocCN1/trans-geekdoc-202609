# Performing the request

Now that you have the request object, you can implement the classify(image:) method. Add the following code to method:

```
func classify(image: UIImage) {
  // 1
  guard let image = CIImage(image: image) else {
    print("Unable to create CIImage")
    return
  }
  // 2
  let orientation = CGImagePropertyOrientation(image.image.orientation)
  // 3
  DispatchQueue.global(qos: .userInitiated).async {
    // 4
    let handler = VNRequestHandler(ciImage: ciImage, orientation: 
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

+   1. Converts the UIImage to a CIImage object.

+   2. The UIImage has an imageorientation property that describes which way is up when the image is to be drawn. For example, if the orientation is "down", then the image should be rotated 180 degrees. You need to tell Vision about the image's orientation so that it can rotate the image if necessary, since Core ML expects images to be upright.