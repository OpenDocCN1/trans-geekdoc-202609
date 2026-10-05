# Design implementation of PPE detection system YOLOv9 201

objects. Consequently, the loss decreases significantly in the second epoch and continues to gradually decline as the number of epochs increases. The YOLOv9 model achieved outstanding results (Figure 9.8), demonstrating exceptional capabilities in detecting PPE items.

Precision: With a precision close to 96.5%, the model exhibits a remarkable ability to correctly identify all PPE items in the test set images. This signifies a very low row of misclassification.

Recall: A recall to 94.4% indicates that a very high proportion of the model's detections for all PPE classes were actually correct (true positives). This translates to a minimal number of false alarms, making the model highly reliable in real-world applications (Figure 9.7).

mAP50: The mAP50 metric signifies a Mean Average Precision (mAP) close to 98%, indicating exceptional performance by the YOLOv9 model in detecting various PPE items within the test set. Overall, these results suggest that the YOLOv9 model has been effectively trained to detect PPE items with a high degree of accuracy and generalizability. This paves the way for its potential implementation in real-world workplace safety

![](bbox=[0.125, 0.433, 0.875, 0.883])

Figure 9.7 Confusion matrix.