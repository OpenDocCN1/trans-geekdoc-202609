eq. (6.1)) are used to filter the region proposals. The detection performance is clearly improved for all GSDs, whereby the gain in AP increases with higher GSDs even though the semantic labeling accuracy gets worse for higher GSDs. This indicates that the importance of employing semantic context information increases with higher GSDs and consequently smaller object dimensions.

![](bbox=[0.14, 0.3, 0.9, 0.62])

Figure 6.12: Qualitative detection examples before (top row) and after (bottom row) filtering the region proposals using the semantic labeling mask outputted by FCN-D16 indicate that false alarms located on regions that are unlikely to contain vehicles, e.g., windows on buildings, are removed.

Table 6.7: Average precision (in %) of Faster R-CNN with and without semantic labeling based filtering using FCN-D16 on the Potsdam dataset for different GSDs.

| Filter Criterion | GSD (in cm) |  |  |  |  |
|---|---|---|---|---|---|
|  | 5 | 10 | 15 | 20 | 25 |
| - | 92.9 | 92.2 | 90.1 | 82.7 | 62.9 |
| eq. (6.1) | 93.9 | 93.3 | 91.7 | 85.8 | 70.7 |