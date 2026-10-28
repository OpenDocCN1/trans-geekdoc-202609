that the proposed architectures affect the detection performance even for low spatial resolutions.

![](bbox=[0.11, 0.24, 0.88, 0.48])

Figure 6.21: Qualitative detection examples of the baseline Faster R-CNN (top row) and EMT Faster R-CNN with FCN-D16 (bottom row) indicate that false alarms located on regions that are unlikely to contain vehicles, e.g., buildings, are reduced.

Table 6.14: Average precision of the baseline Faster R-CNN, IMT Faster R-CNN and EMT Faster R-CNN on DLR 3K for different GSDs.

| Approach | GSD (in cm) |  |  |
|---|---|---|---|
| Approach | 13 | 19.5 | 26 |
| Faster R-CNN | 95.0 | 91.9 | 86.0 |
| IMT Faster R-CNN | 95.8 | 93.0 | 87.3 |
| EMT Faster R-CNN | 96.2 | 93.3 | 88.9 |