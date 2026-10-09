![](bbox=[0.15, 0.09, 0.55, 0.33])

![](bbox=[0.15, 0.34, 0.85, 0.36])

In order to verify the performance of the algorithm in practical applications, both the algorithm and the original YOLOv5s algorithm are used to detect the defects in the captured images. The detection results are shown in Figure 9.

![](bbox=[0.12, 0.43, 0.45, 0.58])

![](bbox=[0.55, 0.43, 0.88, 0.58])

![](bbox=[0.12, 0.58, 0.45, 0.72])

![](bbox=[0.55, 0.58, 0.88, 0.72])

![](bbox=[0.17, 0.73, 0.43, 0.74])

It can be seen from the processing results in Figure 9 that in the first group of pictures, the Pig materials are disorderly arranged, and both algorithms detect the fluorescent bodies with surface damage. However, the original algorithm misses the detection of fluorescent bodies with shape defects, while the improved algorithm is more in line with the actual size of the defects. In the second group of images, for the pollution that is not obvious in the lower left corner, the original algorithm has missed detection. On the other hand, the improved algorithm enhances the detection of small target defects and less obvious target defects. Despite the differences in the two scene targets, the improved algorithm exhibits strong robustness.

In order to further verify the performance of the model in the same type of algorithm, the popular single-stage algorithm and the two-stage algorithm in the field of the deep