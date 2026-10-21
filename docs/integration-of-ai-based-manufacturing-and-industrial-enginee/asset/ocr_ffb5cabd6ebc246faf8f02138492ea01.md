![](bbox=[0.1, 0.12, 0.88, 0.55])

FIGURE 6.7 Frames from OTCVBS thermal data set.

# 6.3 PERFORMANCE METRICS

New strategies and frameworks are constantly being established, and futuristic tracking and recognition systems are emerging. One of the most critical aspects in developing an effective framework is assessing the effectiveness of that model. Different metrics are often used to estimate the performance of the model, and these measures are termed as performance metrics or evaluation metrics. Thus, in this section, performance metrics have been roughly characterized into target detection performance metrics and target tracking performance metrics.

# 6.3.1 Detection Performance Metrics

Because numerous approaches to MOT make use of the detection-based tracking strategy, they frequently test both detection and tracking performance. Target detection metrics are thus used in MOT methods and use different parameters for evaluation. The most widely used detection performance metrics are:

+   a) Precision:
+   This refers to the model’s precision in detecting only relevant objects and is the ratio of true positives to total detections recorded by the model. Mathematically, this is given as Eq. (6.1). Here, TP stands for true positive and FP stands for false positives. A good model has both high precision and high recall.
+   
+   P = TP / (TP + FP) (6.1)