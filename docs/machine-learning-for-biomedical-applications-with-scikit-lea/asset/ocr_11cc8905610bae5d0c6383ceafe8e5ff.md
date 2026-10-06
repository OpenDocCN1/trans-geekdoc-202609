Recall (or sensitivity) measures a proportion of correctly segmented pixels in the ground-truth segmentation. It can be numerically expressed as

$$recall = \frac{TP}{TP + FN}$$

where false negatives $FN$ are pixels of the foreground class incorrectly classified as the background. $TP + FN$ then comprises all pixels of the foreground in the ground-truth segmentation. To evaluate this measure, we can use scikit-learn object

```
sklearn.metrics.recall_score
```

Note that neither of these measures considers correctly classified background (true negatives). Therefore, the amount of background surrounding the image will have no effect on these measures.

# Dice score

In machine learning it is common to create a composite score from precision and recall that is called **F1 score** and is defined as

$$F1 = \frac{2 \times precision \times recall}{precision + recall}$$

This measure is known in medical image segmentation as **dice score**, and it represents the number of correctly segmented pixels of the foreground label, over the average number of foreground label pixels in the predicted and ground-truth segmentations. In fact, this score is often used as a segmentation loss instead of the cross-entropy. To evaluate score, we can use the scikit-learn object

```
sklearn.metrics.f1_score
```

# Quantitative evaluation of the segmentation performance

We will now evaluate F1 score, precision and recall on the test set. We will calculate the scores for all individual test images and average them. To do that we need to loop over all test batches and then over all images in each batch:

```
from sklearn.metrics import f1_score, \
precision_score, recall_score
```

```
# scores to calculate
f1_scores=[]
prec_scores={}
recall_scores={}
```