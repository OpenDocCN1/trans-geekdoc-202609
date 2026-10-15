![](bbox=[0.1, 0.14, 0.95, 0.32])

# FIGURE 8.7 Confusion of histopathology data classification.

# TABLE 8.3

# Performance Measures of Histopathology Data Classification

| Model | Class | Accuracy | Precision | Recall | F1 score |
|---|---|---|---|---|---|
| VGG-16 | Malignant | 85.0 | 0.76 | 0.77 | 0.76 |
|  | Benign |  | 0.89 | 0.88 | 0.89 |
| ResNet-50 | Malignant | 74.5 | 0.38 | 0.41 | 0.40 |
|  | Benign |  | 0.55 | 0.83 | 0.54 |
| Inception V3 | Malignant | 68.59 | 0.51 | 0.48 | 0.48 |
|  | Benign |  | 0.76 | 0.78 | 0.77 |
| Ensemble | Malignant | 89.9 | 0.85 | 0.84 | 0.85 |
|  | Benign |  | 0.92 | 0.93 | 0.92 |

hardware setup of the PYNQ board for MRI data classification is shown in Figure 8.12, and the time taken for each prediction was observed to be 10.62 milliseconds. Also, the power consumption of the setup was measured using a power meter and was found to be 3.4 watts.

# (ii) Ultrasound

In Figure 8.13, a clear visualization of the consecutive hardware deployment results of 16 ultrasound datasets is provided, where the “actual” label represents the ground truth and the “predicted” label represents the classification provided by the hardware. The hardware setup of the PYNQ board for ultrasound data classification is shown in Figure 8.14 and the time taken for each prediction was observed to be 10.14 milliseconds. Also, the power consumption of the setup was measured using a power meter and was found to be 3.2 watts.

# (iii) Histopathology

In Figure 8.15, a clear visualization of the consecutive hardware deployment results of 16 histopathology datasets is provided, where the “actual” label represents the