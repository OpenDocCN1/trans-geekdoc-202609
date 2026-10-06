# Convolutional neural networks

Predicted: batch 0

Predicted: batch 1

Predicted: batch 2

![](bbox=[0.212, 0.107, 0.396, 0.252])

![](bbox=[0.423, 0.107, 0.607, 0.252])

![](bbox=[0.634, 0.107, 0.818, 0.252])

Ground truth: batch 0

Ground truth: batch 1

Ground truth: batch 2

![](bbox=[0.212, 0.277, 0.396, 0.422])

![](bbox=[0.423, 0.277, 0.607, 0.422])

![](bbox=[0.634, 0.277, 0.818, 0.422])

Figure 11.12 Predicted and ground-truth segmentations on the test set.

sensitivity and specificity (see Sec. 4.1.5). However, accuracy is not a very good measure to evaluate binary segmentation because a correctly classified background class is not important to us. Note that we have quite a lot of empty space around the brain in our MR images, which is easy to segment correctly as background. This will artificially increase accuracy compared to the situation in which we cropped the images around the brain more tightly. A much more meaningful way to evaluate segmentation is to look at *precision* and recall because these measures always look at the foreground, in our case, the cortical segmentation.

**Precision** (or positive predictive value) measures a proportion of correctly segmented voxels in the predicted segmentation. It can be numerically expressed as

```
precision = \frac{TP}{TP + FP}$
```

where true positives $TP$ are pixels of the foreground label (cortex) classified correctly and false positives $FP$ are pixels of the background incorrectly classified as the foreground label. $TP + FP$ therefore comprises all the pixels that are predicted as a foreground label. To evaluate this measure we can use the scikit-learn object

```
sklearn.metrics.precision_score
```