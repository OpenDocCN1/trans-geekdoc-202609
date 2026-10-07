# Sewer Pipe Defect Detection in CCTV Images ■ 233

![](bbox=[0.119, 0.123, 0.467, 0.312])

![](bbox=[0.513, 0.123, 0.861, 0.312])

Figure 12.10 Defect images trained with VGG16 network (a) longitudinal crack (b) infiltration.

![](bbox=[0.119, 0.396, 0.477, 0.584])

![](bbox=[0.523, 0.396, 0.879, 0.584])

Figure 12.11 (a) Region-based segments (b) image segmentation based on clustering.

defected image are shown in Figure 12.13. Finally, segmented defects are created using bounding boxes (Figure 12.14).

# 12.5 Conclusion

This work suggests solutions to pipe system detection. Many pipe systems are old so various defects such as roots, cracks, deposits, and infiltration are found, which can lead to serious consequences. CCTV is used for sewer pipe inspection by capturing inspection videos. Manual interpretation of the CCTV inspection videos is time-consuming, and the assessment results are affected by the inspector's expertise and experience. Here defects are found quickly using faster R-CNN with VGG