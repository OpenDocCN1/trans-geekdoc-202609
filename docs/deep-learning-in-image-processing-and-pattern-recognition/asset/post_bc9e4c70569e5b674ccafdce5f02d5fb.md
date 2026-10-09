
Figures 5 and 6 show the data updates of the AutoAssign model when $\mathrm{n}=3$. For Figure 5, this is the evaluation when the model AutoAssign is trained to epoch = 4. There are 11 classes in the dataset that have not been expanded by MSACP: i4, i5, ii100, ii60, ip, p23, p27, pl100, and pr40 have not been amplified because these classes have higher AP.

![](img/e4200cc4308edaf8913e513b0f96dbb6_148_0.png)

Figure 5. The first updated training dataset by MSACP and corresponding evaluation results of AutoAssign at $\mathrm{n}=3$.

![](img/e4200cc4308edaf8913e513b0f96dbb6_148_1.png)

Figure 6. The second updated training dataset by MSACP and corresponding evaluation results of AutoAssign at $\mathrm{n}=3$.

Figure 6 shows the second data update of the AutoAssign model when n = 3. The result of AutoAssign is trained to epoch = 8. There are 14 classes in the figure that have not been expanded by MSACP: i4, i5, i1100, i60, i8, i100, p11, p120, p140, and p4 do not have amplification information because these classes have higher APs. Compared with the first data update with n = 3, three more classes of information were expanded in this update, namely, p26, p5, and p140. For example, the model does not pay much attention to category p140 in early training, which leads to poor model detection of this class. The MSACP algorithm adjusts the model’s attention to this class with information compensation. In the second data update, class p140 does not need compensation for the information by MSACP because it has a higher AP. The class information is updated according to the different stages of training.

According to the data visualization of the MSACP experiment, the expanded sample quantity of each category is different in the three updates. By dividing the training amount into multiple stages, MSACP dynamically adjusts the class information of the training dataset and modifies the learning direction of the model at intervals according to the learning situation. This kind of dynamic adjustment at intervals not only reduces the computing power requirement of training, but also alleviates the class imbalance.

Six models are used to verify the effectiveness of the MSACP algorithm. There are three models that achieve better results when n = 4, namely, Grid RCNN, NAS FGN, and YOLOv3. The other three models achieve better results when n = 2 or n = 3. From the experimental results, it can be seen that more training stages do not necessarily make the model obtain a better improvement effect. When n is greater than four, these models are likely to have better results. The larger the n, the more time it takes to update the training dataset, which leads to a longer training time. When n = 1, the training of the model has only one stage and the training set is not updated. The entire training of the AutoAssign model takes approximately 270 min. When n is greater than one, the training dataset is updated by MSACP. For AutoAssign, it takes about 30 min to complete an update of the training dataset and start the next stage of training. When n = 4, the total running time of MSACP is about 120 min, as shown in Table 7. Although better detection performance may occur if the hyper-parameter n is set larger, there is not much room for improvement in the model. Under the comprehensive consideration of training time and performance improvement, the experiment only set four groups to test the impact of n on the MSACP algorithm.

Table 7. The time of AutoAssign model to update the training dataset by MSACP.

| n | Time (min) | AP (%) |
| :---: | :---: | :---: |
| 1 | 270 | 48.0 |
| 2 | 300 | 53.4 |
| 3 | 330 | 52.7 |
| 4 | 370 | 52.5 |

## 5. Embedded Application of MSACP Algorithm

Many deep learning algorithms have been applied in real life, but there are also many challenges in the practical application. How to improve the performance of the embedded platform under the limited computing power is one of the main challenges. Therefore, MSACP is applied to the autonomous driving scenario to test the effect of the algorithm in practical applications. The scenario is shown in Figure 7. It can be seen that the autonomous driving scenario has multiple speed limit signs and a traffic light. The embedded platform is in the red box, which is equipped with a CPU of 4-core ARM Cortex-57 series (ARM, Cambridge, UK) and a GPU of 128-core Maxwell architecture (NVIDIA, Santa Clara, CA, USA). The computing power is not less than 472 GFLOPs. In addition, the platform is equipped with a human–computer interaction interface, which can output the road condition information and detect the corresponding object information in real time.

The model YOLOv3-tiny is selected for traffic sign detection in the embedded platform, which is a simplified version of YOLOv3. YOLOv3-tiny mainly removes one feature layer based on YOLOv3, and at the same time changes the three independent prediction branches into two. Therefore, YOLOv3-tiny has a faster inference speed and is widely used in practical projects. The dataset used in this experiment contains 12 classes, some of which are difficult to collect in real life. There is still an imbalance of categories in the dataset. The class of people and car in the dataset has the largest number of samples, while the class with the smallest number of samples is yellow light. Because of the cost and time of production, MSACP is used to optimize the dataset, which is embedded into the YOLOv3-tiny model. The optimal weight file is obtained after the training is completed and deployed to the embedded platform for object detection. A comparative test is performed before importing the embedded platform, as shown in Table 8. The metric used in the table is AP50. The YOLOv3-tiny model with the MSACP algorithm is improved by 3.3% compared to the original model. Some classes have significant improvements, such as limit_10 and limit_50.

![](img/e4200cc4308edaf8913e513b0f96dbb6_150_0.png)

### Table 8. The comparison of class performances based on the YOLOv3-tiny model.

| Class | YOLOv3-Tiny (%) | YOLOv3-Tiny + MSACP(%) |
|:--|--:|--:|
| green_light | 78.8 | 76.8 (-2.0) |
| yellow_light | 97.0 | 98.4 (+1.4) |
| red_light | 68.8 | 70.3 (+1.5) |
| turn_right | 85.2 | 83.4 (-1.8) |
| turn_left | 77.4 | 82.3 (+4.9) |
| limit_10 | 72.0 | 99.5 (+27.5) |
| limit_50 | 85.6 | 91.3 (+5.7) |
| limit_60 | 95.6 | 95.6 (+0.0) |
| limit_110 | 94.5 | 96.9 (+2.4) |
| person | 99.3 | 99.4 (+0.1) |
| car | 99.5 | 99.5 (+0.0) |
| stop | 99.5 | 99.5 (+0.0) |
| Average | 87.8 | 91.1 (+3.3) |

In addition, a more intuitive experiment was performed. Three images with traffic signs on which the model had not been trained were randomly selected for testing. The results are shown in Figures 8 and 9. Figure 8 shows the detection results of YOLOv3-tiny. Figure 9 shows the detection results of YOLOv3-tiny + MSACP. From the visual results, the YOLOv3-tiny model with MSACP has higher confidence in detecting traffic signs. More importantly, the inference time is the same for both comparisons.

![](img/e4200cc4308edaf8913e513b0f96dbb6_151_0.png)

![](img/e4200cc4308edaf8913e513b0f96dbb6_151_1.png)

Figure 8. The detection effect of YOLOv3-tiny: (a) The class of speed limit 50 km/h; (b) The class of speed limit 10 km/h.

![](img/e4200cc4308edaf8913e513b0f96dbb6_151_2.png)

![](img/e4200cc4308edaf8913e513b0f96dbb6_151_3.png)

Figure 9. The detection effect of YOLOv3-tiny + MSACP: (a) The class of speed limit 50 km/h; (b) The class of speed limit 10 km/h.

## 6. Conclusions

In this paper, we propose MSACP, a multi-stage adaptive Copy-Paste augmentation method based on model training preference. MSACP introduces a multi-stage adjustment mechanism to provide dynamic information compensations for the training of the model. Under the premise of alleviating class imbalance, the over-fitting or under-fitting phenomenon generated in the training of the model is avoided as much as possible. Although the MSACP algorithm is effective according to the experimental results, it takes a long time to update the training dataset. When the MSACP algorithm processes complex data such as 3D images, the operation among objects easily destroys key information in the image, and even generates data that are not conducive to model training. In future work, this is one of the difficulties that we will focus on overcoming. In addition, we hope that the multi-stage adjustment mechanism in the MSACP algorithm can further be applied to different data enhancement strategies so that data augmentation can play an effective role in model training.

**Author Contributions:** Conceptionualization, X.Y., F.L., Y.L. and A.W.; methodology, X.Y., A.W., Y.L. and F.L.; software, F.L.; validation, F.L.; writing—review and editing, X.Y., F.L. and A.W. All authors have read and agreed to the published version of the manuscript.

**Funding:** This work was funded by the Major Science and Technology Projects of Zhongshan City in 2022 (2022A1020).

**Data Availability Statement:** https://cg.cs.tsinghua.edu.cn/traffic-sign/ (accessed on 1 January 2016).

**Conflicts of Interest:** The authors declare no conflict of interest.
