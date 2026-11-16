contribution to the loss. As shown in Equation (5), the first two terms are related to coordinate the identified object with x and y to denote the object location, while w and h refer to the width and height of the bounding box. In order to have more weight in the first two terms, \(\gamma_{coord}\)was assigned to be the largest number, which had a value of 5. Thus, the weight of localization error got enhanced. In terms of IoU error computation, when the object center falls in this cell, the weight of IoU error should be increased in order to predict location accurately. The value of \(\gamma_{noobj}\)is set to be 0.5 to refine the IoU error. For the same error value, the effect of large object error on the detection should be less than the effect of small object error on the detection. This is because the same bias accounts for the proportion of large objects is much smaller than the proportion of the same deviation to small objects. Therefore, it is supposed to increase the contribution to loss due to bigger object IoU error. Square roots of width and height were chosen to replace their original forms. For same bias value, the square root error from the big box is smaller than the small one.

![](bbox=[0.195, 0.455, 0.805, 0.695])

Figure 14. Enhancement of identification accuracy with data augmentation.

![](bbox=[0.285, 0.765, 0.685, 0.885])

Figure 15. Comparison of training loss.