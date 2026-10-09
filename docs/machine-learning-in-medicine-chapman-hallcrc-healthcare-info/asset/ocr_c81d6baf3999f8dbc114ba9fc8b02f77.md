TABLE 13.3 BP Measurements of Patients A, B, C, and D
| | Day 0 | | | Day 700 | | |
| --- | --- | --- | --- | --- | --- | --- |
| Patient | Systolic BP | Diastolic BP | MAP | Systolic BP | Diastolic BP | MAP |
| A | 120 | 80.5 | 93.7 | 103.5 | 66.5 | 78.8 |
| B | 130.5 | 83 | 98.8 | 143.5 | 94 | 110.5 |
| C | 118 | 80.5 | 93 | 105.3 | 69 | 81.1 |
| D | 114 | 84.5 | 94.3 | 120 | 88 | 98.7 |

![](bbox=[0.2, 0.28, 0.8, 0.57])

FIGURE 13.6 Applying a 3D growing algorithm to the volume of binary segmented images allows for visualization of the automatically segmented MRA data. Day 0 of patient C (top left). Day 700 of patient C (top right). Day 0 of patient D (bottom left). Day 700 of patient D (bottom right). These results demonstrate the temporal changes in cerebrovascular structure in these patients (circled).

# 13.4 DISCUSSION

The average cumulative segmentation algorithm had a sensitivity of $0.997 \pm 0.008$ and a specificity of $0.9998 \pm 0.001$. This high level of accuracy demonstrates the benefit of using a manual input to initialize automatic segmentation. Using manual segmentation alone would be too time intensive to be used in a practical healthcare setting, while utilizing only an automatic segmentation approach would not provide sufficient segmentation accuracy to delineate and quantify the diameters of the smaller arteriolar ($< 10 \mu m$) cerebral blood vessels. The proposed segmentation algorithm combines the accuracy of manual segmentation with the benefit