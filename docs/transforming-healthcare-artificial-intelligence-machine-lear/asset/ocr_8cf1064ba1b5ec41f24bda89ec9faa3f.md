# 202 Transforming Healthcare

monitoring systems. The graph of precision, recall, and mAP50 exhibits fluctuations. This suggests that the dataset might have a limited number of images, and training with more epochs led to overfitting. This approach aimed to achieve higher final model accuracy to compensate for the constraint of fewer images

```
Average Accuracy = Precision + Recall + mAP50
3
= 95.6% + 94.4% + 97.8%
3
= 95.98%
```

# 9.6.1 Performances

Improving Detection Accuracy: Future research can focus on enhancing YOLOv9's ability to detect PPE under challenging conditions, such as poor lighting, complex backgrounds, and occlusions. Techniques like transfer learning and the integration of additional contextual information could improve detection accuracy.

Expanding Categories: As PPE requirements evolve, the model to recognize a broader range of PPE items, such as face shields, arguably, and protective footwear, will be important. This will require updating the training dataset and refining the model to handle the increased complexity.

Integration with IoT Devices: Integrating YOLOv9 with IoT devices, such as wearable sensors, can enhance its functionality. For example, combining visual detection with sensor data can provide a comprehensive safety monitoring system that detects not only PPE compliance but also environmental hazards and worker health status.

> Table 9.1 Performance evaluation of YOLOv9 for PPE kit detection

| Class | Precision (P) | Recall (R) | mAP50 |
|---||---|---|---|
| All | 0.956 | 0.944 | 0.978 |
| Boots | 0.978 | 0.9 | 0.971 |
| Helmet | 0.959 | 0.963 | 0.974 |
| Person | 0.98 | 0.961 | 0.991 |
| Vest | 0.98 | 0.961 | 0.991 |