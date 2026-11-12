# TABLE 6.1 Comparative Study of the COVID-19 Diagnosis Architecture Using the COVIDx Dataset

| Author | Year | Task | No. Cases | Pre-Processing | Architecture | Performance |
|---|---|---|---|---|---|---|
| Gunraj et al. [12] | 2021 | Geographic extent and Opacity extent scoring | 396 | Randomly translation Rotations Horizontal flips Zooms intensity shifts Cutout Gaussian noise. | DNN | Geographic Extent = 0.664 Opacity extent = 0.635 Mean = 0.032 STD = 0.044 |
| Ebadi et al. [15] | 2021 | Image Classification | 12,943 | Cropping | DNN | N/A |
| Ambati et al. [17] | 2021 | Image Classification | 13,870 | N/A | CNN | Accuracy = 98.08% |
| Cherti et al. [18] | 2021 | Few-Shot learning Image classification transfer learning | 13,870 | Standard random resized crop data augmentation | Pre-trained model, Resent 50 | Accuracy = 95.78% |
| Celaya, et al. [25] | 2021 | Medical image segmentation Semantic segmentation | 13,870 | Randomly reflecting | CNN | Accuracy = 0.9941% |
| Qi et al. [19] | 2021 | Computed tomography (CT) COVID-19 diagnosis Decision making | 13,870 | N/A | ResNet50 | Accuracy = 86.46% |
| Yang et al. [26] | 2021 | Federated learning | 13,870 | N/A | CNN | Flop = 94.54 +/- 0.21 |
| Ali et al. [27] | 2021 | Classification | 13,870 | Geometric transformations and color space transformations | CNN | Accuracy = 95% |
| Li et al. [20] | 2021 | Computed tomography (CT) | 19 | Flipping, translation, rotation using random five different angles | Patch-based convolutional neural network | Accuracy = 97.89% |
| Hao et al. [21] | 2021 | Active learning General classification-representation learning Unsupervised representation learning | 13,870 | Random crop Random flip Color distortion Gaussian blur Random grayscale | CNN-GP hybrid model | Accuracy = 96% |
| Zhang et al. [22] | 2021 | COVID-19 Diagnosis | 13,870 | N/A | CNN | Accuracy = 88% |
| Gunraj et al. [10] | 2020 | COVID-19 Diagnosis | 13,870 | Translation rotation horizontal flip Zoom intensity shift | CNN | N/A |
| Gunraj et al. [11] | 2020 | Decision-making | N/A | Cropping box Jitter Rotation Horizontal and vertical shear Horizontal flip Intensity | DNN | Sensitivity = 98.1% Positive Predictive Value = 98.1% |