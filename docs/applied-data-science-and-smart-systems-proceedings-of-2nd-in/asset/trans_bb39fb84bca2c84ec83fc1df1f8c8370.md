
-   [检测迎面车辆的速度]使用 ROI（感兴趣区域）实现。ROI 可根据需求进行修改。此外，迎面车辆的速度通过距离与时间的概念来估算，即车辆在一秒内行驶的距离。

(11)  

$$Speed = \\frac{Distance}{Time}$$  

### 结果与分析

来自印度马哈拉施特拉邦浦纳（Pune, Maharashtra, India）DMART 道路（坐标 18.4518331°，73.8439111°）的真实时间交通视频被用于车道检测、目标检测及其跟踪。本节将讨论使用上述算法和我们开发的机器学习模型对车道和目标检测的实时结果。[Figure 17.11](#ch17.xhtml#fig17_11)，[Figure 17.12](#ch17.xhtml#fig17_12)，[Figure 17.13](#ch17.xhtml#fig17_13)，[Figure 17.14](#ch17.xhtml#fig17_14) 和 [Figure 17.15](#ch17.xhtml#fig17_15) 显示在 Section III.C.1（对象检测与跟踪）下讨论的步骤输出（[Table 17.4](#ch17.xhtml#tab17_4)）。

![Figure 17.11 Frame capture](images/fig17_11_C.jpg)

[Figure 17.11 Frame capture](#ch17.xhtml#R_fig17_11)

![Figure 17.12 Frame gray scaling](images/fig17_12_B.jpg)

[Figure 17.12 Frame gray scaling](#ch17.xhtml#R_fig17_12)

![Figure 17.13 Extracting ROI](images/fig17_13_C.jpg)

[Figure 17.13 Extracting ROI](#ch17.xhtml#R_fig17_13)

![Figure 17.14 ROI masking](images/fig17_14_B.jpg)

[Figure 17.14 ROI masking](#ch17.xhtml#R_fig17_14)

 ![Figure 17.15 Final output](images/fig17_15_C.jpg)

[Figure 17.15 Final output](#ch17.xhtml#R_fig17_15)

[Table 17.4 Parameters for Robert operator](#ch17.xhtml#R_tab17_4)

| Images Pixel || Precision || Recall || F1 score || PSNR (dB) |
| --- | --- | --- | --- | --- |
| Img 1 300\*168 || 0.53 || 0.49 || 0.72 || 66 |
| --- | --- | --- | --- | --- |
| Img 2 300\*168 || 0.51 || 0.45 || 0.77 || 70 |
| Img 3 303\*166 || 0.59 || 0.51 || 0.64 || 68 |
| Img 4 300\*168 || 0.57 || 0.50 || 0.71 || 77 |
| Img 5 259\*194 || 0.61 || 0.53 || 0.57 || 79 |

Table 17.5 Parameters for Prewitt operator

| Image Pixel || Precision || Recall || F1 score || PSNR (dB) |
| --- | --- | --- | --- | --- |
| Img 1 300\*168 || 0.83 || 0.77 || 0.90 || 70 |
| --- | --- | --- | --- | --- |
| Img 2 300\*168 || 0.79 || 0.68 || 0.84 || 56 |
| Img 3 303\*166 || 0.39 || 0.42 || 0.88 || 59 |
| Img 4 300\*168 || 0.47 || 0.38 || 0.81 || 68 |
| Img 5 259\*194 || 0.93 || 0.86 || 0.80 || 62 |

Table 17.6 Parameters for Sobel operator

| Image Pixel || Precision || Recall || F1 score || PSNR (dB) |
| --- | --- | --- | --- | --- |
| Img 1 Image || Pixel || Precision || Recall || F1 score |
| --- | --- | --- | --- | --- |
| Img 2 300\*168 || 0.96 || 0.81 || 0.44 || 45 |
| Img 3 303\*166 || 0.43 || 0.39 || 0.38 || 44 |
| Img 4 300\*168 || 0.76 || 0.79 || 0.40 || 51 |
| Img 5 259\*194 || 0.92 || 0.86 || 0.37 || 59 |

Table 17.7 Parameters for Canny operator

| Image Pixel || Precision || Recall || F1 score || PSNR (dB) |
| --- | --- | --- | --- | --- |
| Img 1 300\*168 || 0.95 || 0.97 || 0.96 || 82 |
| --- | --- | --- | --- | --- |
| Img 2 300\*168 || 0.88 || 0.89 || 0.91 || 79 |
| Img 3 303\*166 || 0.89 || 0.90 || 0.93 || 80 |
| Img 4 300\*168 || 0.74 || 0.77 || 0.90 || 83 |
| Img 5 259\*194 || 0.82 || 0.86 || 0.90 || 85 |

**For lane detection**, on an empty road with a straight lane, we apply the Hough transform on the detected edges using the Canny edge detector. The lanes are detected and highlighted with orange markings (see [Figure 17.16](#ch17.xhtml#fig17_16)). This makes it easier for the driver to navigate.

![Figure 17.16 Real time lane detection](images/fig17_16_C.jpg)

[Figure 17.16 Real time lane detection](#ch17.xhtml#R_fig17_16)

As soon as the incoming vehicle enters the specified ROI, the object detection algorithm starts detecting the vehicle and finally bounds it in a bounding box (see [Figure 17.17](#ch17.xhtml#fig17_17)). Thus, the driver is alerted for a safe lane change.

 ![Figure 17.17 Real time object detection](images/fig17_17_C.jpg)

[Figure 17.17 Real time object detection](#ch17.xhtml#R_fig17_17)

To detect the speed of the oncoming vehicle, ROI is used. ROI is set up to a distance of up to 80 m, which can be varied according to user requirement. The test vehicle’s speed is 25 m/s. A time interval of 2 s has been chosen for the vehicle to cover its distance (see [Table 17.8](#ch17.xhtml#tab17_8)).

[Table 17.8 Speed analysis](#ch17.xhtml#R_tab17_8)

| Object || Distance (m) || Speed (m/s) |
| --- | --- | --- |
| Object 1 || 70 || 35 |
| --- | --- | --- |
| Object 2 || 75 || 27.5 |
| Object 3 || 60 || 30 |
| Object 4 || 65 || 37.5 |
| Object 5 || 72 || 36 |

## VI. Conclusion

Four distinct edge detection algorithms are mentioned in the study for our proposed **SLODS**. PSNR values, precision, recall, and F1 score were the metrics used to assess these approaches. These parameters were used to evaluate the performance of edge detection methods developed by Canny, Sobel, Prewitt, and Robert. After careful examination, we determined that the edge detection approach successfully detected the greatest number of edges for both vertical and horizontal edges. Visualizing the images in [Figure 17.9](#ch17.xhtml#fig17_9) clearly shows that Robert, Prewitt, and Sobel produce lower‑quality images compared to Canny, which can detect both weak and strong edges. The paper also mentions an efficient method for detecting and tracking objects. It suggests selecting and masking the ROI after converting the image to grayscale. The algorithm used in this paper detected 96 % of all vehicles in the image. The **SLODS** provides accurate speed estimation of the oncoming vehicle.

## VII. Future scope

The same object detection algorithm can also be used to recognize stop signs or pedestrians in a self‑driving vehicle, helping the vehicle to stop or maneuver at a safe distance from a pedestrian.

## References

* Annual report on Road Accidents in India. (2020). Retrieved from [https://morth.nic.in/sites/default/files/RA_2020.pdf](https://morth.nic.in).

* Madhura, B., Tanuja, D., Akshay, V., and Dina, S. (2022). Performance analysis of object classification system for traffic objects using various SVM Kkernels. Adv. Data Comput. Comm. Sec., 423–432, doi:[https://doi.org/10.1007/978-981-16-8403-6_39](http://dx.doi.org/10.1007/978-981-16-8403-6_39).

* Sandipann, N., Pradnya, N. B., and Dhiraj, M. D. (2018). A review of recent advances in lane detection and departure warning system. Pattern Recogn., 73, 216–234. doi:[https://doi.org/10.1016/j.patcog.2017.08.014](http://dx.doi.org/10.1016/j.patcog.2017.08.014).

* Anuj, M., Constantine, P., and Tomaso, P. (2001). Example-based object detection in images by components. IEEE Trans. Pattern Anal. Mac. Intel., 23(4), 349–361. doi:[https://doi.org/10.1109/34.917571](https://doi.org/10.1109/34.917571).

* [Bertozzi, M. and Broggi, A.](#ch17.xhtml#R_ref17_5) (1998). GOLD: A parallel realtime stereo vision system for generic obstacle and lane detection. IEEE Trans. Image Proc., 7(1), 62–81. doi: [https://doi.org/10.1109/83.650851](https://dx.doi.org/10.1109/83.650851).

* Mukesh, T. and Rakesh, S. (2017). A review of detection and tracking of object from image and video sequences. Int. J. Computat. Intel. Res., 13(5), 745–765. [https://www.ripublication.com/ijcir17/ijcirv13n5_07.pdf](https://www.ripublication.com).

* William, N., Jack, L., Simon, G., and Jaco, V. (2005). A review of recent results in multiple target tracking. Proc. 4th Int. Sym. Image Sig. Proc. Anal., 3807–3812. doi:[https://doi.org/10.1109/ISPA.2005.195381](https://doi.org/10.1109/ISPA.2005.195381).

