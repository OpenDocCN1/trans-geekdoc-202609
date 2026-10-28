Qualitative detection examples (red boxes) and corresponding GT (green boxes) on DLR 3K with a GSD of 26 cm are visualized in Figure 8.5. While all detection methods show a good localization accuracy, applying the proposed detection method results in fewer false alarms caused by vehicle-like structures on buildings. However, for all methods, remaining false alarms are mainly due to objects located on asphalted areas with vehicle-like shapes.

To demonstrate the transferability of the detection methods proposed in this thesis, MFD Faster R-CNN with SAR is compared to existing work from literature on VEDAI LCI and VEDAI SCI (see Table 8.12). Note that exploitation of semantic information is not conducted because of the missing semantic labeling annotations. Each model is trained with the same data augmentation settings, i.e., vertical and horizontal flipping as well as rotation in steps of 90 degrees. The proposed MFD Faster R-CNN with SAR and VGG16 as base network achieves the best AP on both versions of the dataset. Using ZynqNet as base network exhibits the same detection accuracy on VEDAI LCI, while the detection accuracy slightly drops in case of the higher GSD as observed for DLR 3K as well. Amongst the adapted detection frameworks, RefineDet shows overall the best detection accuracy. Similar to DLR 3K, Adapted RetinaNet exhibits the poorest detection accuracies due to the coarse feature map resolution. Qualitative detection examples (red boxes) and corresponding GT (green boxes) on VEDAI SCI are visualized in Figure 8.6.

# Table 8.12: AP (in %) for MFD Faster R-CNN + SAR with VGG16 and ZynqNet, respectively, compared to representative existing work on the VEDAI dataset.

| Method | Base Network | VEDAI LCI | VEDAI SCI |
|---|---|---|---|
| Adapted RetinaNet[Tay18] | ResNet50 | 95.5 | 89.6 |
| FPN [Lin17a] | ResNet50 | 97.1 | 93.2 |
| Cascade R-CNN [Cai18] | ResNet50 | 97.1 | 93.3 |
| YOLOv3 [Red18] | Darknet-53 | 96.7 | 92.7 |
| RefineDet [Zha18a] | VGG16 | 97.2 | 93.8 |
| MFD Faster R-CNN + SAR | VGG16 | **97.7** | **94.3** |
| MFD Faster R-CNN + SAR | ZynqNet | **97.7** | 94.0 |