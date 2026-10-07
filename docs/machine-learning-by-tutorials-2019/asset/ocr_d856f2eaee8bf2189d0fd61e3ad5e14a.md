# Machine Learning

# Chapter 10: YOLO & Semantic Segmentation

```
'cake': 0.3897331947991153,
'candy': 0.3685744872282687,
...
'watermelon': 0.39704090310715189,
'mean_average_precision_50': 0.38825901743235355
```

In this previous chapter, you used the IOU or Intersection-over-Union metric to determine how good the predictions were, but Turi uses a different metric. It computes the average precision for each class, as well as the overall average of these average predictions — yes, you read that — known as the mean average precision, or mAP.

What's important for this average precision metric is that higher is better. If you were to train a different model on this same dataset and it gave a better mAP score, then you could safely draw the conclusion this new model is better than the old one.

IOU measures how much the predicted object overlaps the real object. It doesn't say anything about the classification accuracy — if a predicted box for class "orange" overlaps a ground-truth box for class "apple" with 95%, the bounding box is accurate, but the class is totally wrong. For a realistic metric, you want to match the classes, too.

Also, when evaluating an object detector, you want to get some idea of whether the model actually finds all the objects in the image (the recall). The mAP metric combines these two criteria into a single number. It's not necessarily a very intuitive metric, but it's useful to rank the quality of different models on a given dataset.

> Note: The Pascal VOC dataset (host.robots.ac.uk/pascal/VOC) is one of the standard datasets that people use to benchmark object detectors. At the time of writing, the top-scoring model on Pascal VOC named DOLO and had an mAP of 81.3. The runner-up was a variant of Faster R-CNN with a score of 81.1. For comparison, YOLO v2 scores "only" 48.8 and SSD scores 64.0. Another popular object detector can view the leaderboards at this link: bit.ly/2ET24YM, cocodataset.org/#detection-leaderboard.

For more insight on how your model is doing, take a look at the individual predictions for the test images, using model.predict():

```
test_data['predictions'] = model.predict(test_data)
```

raywender.com

351