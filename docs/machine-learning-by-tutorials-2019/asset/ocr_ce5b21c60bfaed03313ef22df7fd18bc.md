# Machine Learning

# Chapter 10: YOLO & Semantic Segmentation

display with the camera's sensor may cause artefacts to appear in the image that can throw off the model. If users pointing their phones at computer screens is going to be a major use case for your apps, then you'll need to train the model to ignore those artifacts and distortions.

One limitation of Vision was that it could only provide a value for the model's image input, as of iOS 15, you can also pass in values for the other inputs to override defaults from the model. See the VCoreML object:

```
if #available(iOS 13.0, *) {
  visionModel.input.featureName = "image"
  visionModel.featureProvider = try MLDictionaryFeatureProvider(
    "iouThreshold": MLFeatureValue(double: 0.45),
    "confidenceThreshold": MLFeatureValue(double: 0.25)
  )
}
```

With a bit of effort, it's possible to make YOLO on iOS 11. In that case, Vision does not give you the VNRecognizedObjectInstances instances but a VCoreMLFeatureValueObservation with the contents of 13×135 grid. You'll have to decode these into actual bounding boxes and perform NMS yourself to find the best. The YOLO models built by Turi Create with iOS 11, but there are also Keras of YOLO available. For an example of how to run a YOLO model on iOS 11, see github.com/hollance/YOLO-CoreML-MPSNNGraph.

> Note: This was only a brief introduction to object detection. As you can imagine, there is a lot of going under the hood that we glossed over here. If you want to learn more about how single-stage object detectors are trained, see the author's in-depth blog post at machinineth.net/blog/detection/

> Note: The architecture used by Turi, "Tiny YOLO v2", is already a few years old. You can download modern YOLOv3 and YOLOv3-Tiny models from developer.apple.com/machine-learning/models/. These are trained on the 80 classes of the COCO dataset. To make a version of YOLOv3 for your classes, train it yourself, for example using github.com/ultralytics/yolov3 or one of the other popular implementations.