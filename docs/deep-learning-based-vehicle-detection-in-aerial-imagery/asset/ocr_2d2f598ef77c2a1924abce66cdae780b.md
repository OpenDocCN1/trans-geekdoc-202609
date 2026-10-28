# Integration of Spatial Context and Lightweight Feature Extraction

To combine the integration of spatial context and the lightweight feature extraction, ZynqNet is applied as base network for MFD Faster R-CNN. The integration of spatial context from deeper layers is conducted in a stage-wise manner by applying the CEM introduced in Section 6.1.1. The output from the 9th Fire module is up-sampled and combined with the output from the 7th Fire module. The combined features are up-sampled and combined with the output from the 5th Fire module. The resulting feature map enriched with features that comprise more contextual information is then used as input for the RPN and classification stage. Due to its good trade-off between detection accuracy and inference time in case of Faster R-CNN with ZynqNet as base network, VGG0.5-Head is employed as classification head. For training, the staged fine-tuning scheme proposed in Section 6.1.2 is adopted.

The AP and inference times for MFD Faster R-CNN with ZynqNetα=1.00 as base network are given in Table 8.5. The inference time is significantly reduced on both setups by replacing the default base network with ZynqNetα=1.00, while the decrease in AP is small. Applying the pruning strategy introduced in Section 7.1.3 to remove redundant filters yields a further acceleration as expected. The drop in AP with fewer filters per convolutional layer is smaller compared to EMT Faster R-CNN with ZynqNet (see Table 8.2).

Table 8.5: Comparison of the detection accuracy and inference time for MFD Faster R-CNN with different base networks.

| Base Network | AP (in %) | Time (in ms) |  |
|---|---|---|---|
|  |  | Server | Desktop |
| VGG16 | 95.9 | 316.3 | 815.2 |
| ZynqNetα=1.00 | 95.8 | 167.8 | 283.6 |
| ZynqNetα=0.75 | 95.3 | 162.5 | 233.3 |
| ZynqNetα=0.50 | 94.5 | 142.3 | 190.9 |