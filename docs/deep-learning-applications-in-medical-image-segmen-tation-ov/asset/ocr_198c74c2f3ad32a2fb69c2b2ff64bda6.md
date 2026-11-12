# Table 6.1 Comparison of DL models.

| Model | Architecture | Advantages | Limitations | Metrics | Metrics score |
| :--- | :--- | :--- | :--- | :--- | :--- |
| U-Net | Convolutional | High accuracy, handles complex structures | Requires large amounts of labeled data | Precision Accuracy | 89.48 92.60 to |
| FCN | Fully convolutional | Efficient, real-time processing | Limited ability to handle object boundaries | Precision | 84.30 |
| FRNet | Convolutional | Lightweight end-to-end feature refinement network | Loss of spatial information, difficulty in handling blurred boundaries | Accuracy | 0.968 |
| DeepLab | Dilated convolutional | Captures fine details, handles large images | Computationally intensive. | Precision | 95.79 |
| Mask R-CNN | Regional convolutional | Combined object detection and segmentation | Higher computational complexity | Intersection over Union | 0.843 |
| RetinaMask | Feature pyramid network | High accuracy, handles class imbalance, real-time processing | Limited object boundary precision, sensitivity to parameter tuning | AUC | 0.950 to |
| PSPNet | Pyramid pooling modules | Multi-scale contextual information, accurate object boundary delineation | Computationally intensive, sensitivity to hyperparameters | Precision | 88.27 |