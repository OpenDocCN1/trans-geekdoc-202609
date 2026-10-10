

## 5.6.9 基于遗传算法的技术

基于遗传算法的技术（[Bali & Singh, 2015](#ch13.xhtml#r165)）源于进化论。该理论包含三个主要功能。第一个功能是选择，第二个和第三个分别是交叉和变异。这些方法最适合用于模式识别应用。

## 5.6.10 基于显著性的技术

计算机视觉应用中进展最快的领域之一是基于显著性的技术（[Shokoufandeh et al., 1999](#ch13.xhtml#r186)）。该技术有助于检测图像中的显著目标，这在当今发挥着相对非常重要的作用。此外，在寻找分割问题的解决方案时，显著性目标检测技术将显著的前景目标从背景中分离出来。它不像上述分割技术通常做的那样，将图像分割成具有相似属性的区域。因此，它是一种新的图像分割方法。

## 5.7 实验结果

让我们以一张由高清摄像头捕获的图像为例，应用噪声去除技术进行人脸检测。结果如[图 5.5(a)](#ch13.xhtml#f40)至[5.5(e)](#ch13.xhtml#f44)所示。

![Figure 5.5(a) Original image in RGB.](html/images/9780367720919_C005_005a.jpg)

图 5.5(a) RGB 原始图像。

![Figure 5.5(b) Grey scale image with noise.](html/images/9780367720919_C005_005b.jpg)

图 5.5(b) 含噪声的灰度图像。

![Figure 5.5(c) Grey scale image after noise removal.](html/images/9780367720919_C005_005c.jpg)

图 5.5(c) 去噪后的灰度图像。

![Figure 5.5(d) Face detection in gray scale.](html/images/9780367720919_C005_005d.jpg)

图 5.5(d) 灰度图像中的人脸检测。

![Figure 5.5(e) Face detection in RGB image.](html/images/9780367720919_C005_005e.jpg)

图 5.5(e) RGB 图像中的人脸检测。

正如我们从[图 5.5(a)](#ch13.xhtml#f40)到[5.5(e)](#ch13.xhtml#f44)所看到的，首先，我们将原始 RGB 图像转换为灰度图像，该图像充满了噪声。接下来，我们使用维纳滤波器应用噪声去除技术，从灰度图像中去除噪声。最后，我们应用人脸检测算法检测图像中的人脸，并将检测到的人脸图像转换回 RGB 图像。

## 5.8 结论

在本章中，讨论了各种图像预处理方法、图像增强、图像增强的性能指标以及图像分割技术。此外，还设计了一种用于 `MATLAB 2018a` 中人脸检测的算法。可以得出结论，在将图像输入任何智能系统之前，图像预处理是一项重要任务。预处理主要涉及增强技术，用于去除因模糊、夜景、弱光、遮挡、阴影等原因产生的噪声。因此，当我们设计用于监控或视频中目标检测或任何其他图像识别任务的系统时，第一步是图像预处理，以便实现系统的高性能。

## 参考文献

*   [Abd Elaziz, M](#ch13.xhtml#r160b)., Bhattacharyya, S., & Lu, S. (2019). Swarm selection method for multilevel thresholding image segmentation. *Expert Systems with Applications*, *138*, 112818。

*   [Agrawal, A. K.](#ch13.xhtml#r161b), & Sivagami, M, P. S. (2015). Object recognition in Hadoop using HIPI. *International Journal of Scientific & Technology Research*, *4*(7), 115–118。

*   [Al-Ameen, Z](#ch13.xhtml#r162b)., Sulong, G., Rehman, A., Al-Dhelaan, A., Saba, T., & Al-Rodhaan, M. (2015). An innovative technique for contrast enhancement of computed tomography images using normalized gamma-corrected contrast-limited adaptive histogram equalization. *EURASIP Journal on Advances in Signal Processing*, *2015*(1), 1–12。

*   [Anitha, S](#ch13.xhtml#r163b)., & Radha, V. (2010). Comparison of image preprocessing techniques for textile texture images. *International Journal of Engineering Science and Technology*, *2*(12), 7619–7625。

*   [Aradhye, A. A](#ch13.xhtml#r164b)., Inamdar, H. S., Patil, G. S., & Jagdale, Y. B. (2016). Object detection avenue for video surveillance using Hadoop. International Research Journal of Engineering and Technology (IRJET), 3(5), 497–499。

*   [Bali, A](#ch13.xhtml#r165b)., & Singh, S. N. (2015). A review on the strategies and techniques of image segmentation. *2015 Fifth International Conference on Advanced Computing & Communication Technologies*, 113–120。

*   [Dhinakaran, K](#ch13.xhtml#r166b)., Silviya Nancy, J., & Duraimurugan, N. (2015). Video analytics using HDVFS in cloud environment. *ARPN J Eng Appl Sci*, *10*, 13。

*   [Ganesh, R. B.](#ch13.xhtml#r167b), & Appavu, S. (2015). An intelligent video surveillance framework with big data management for Indian road traffic system. *International Journal of Computer Applications*, *123*(10), 12–19。

*   [Ghaware, S](#ch13.xhtml#r168b)., Harke, V., Jadhav, S., & Khanuja, H. (2016). *Approaches for Video Surveillance Using Hadoop*. *4863*(February), 47–50。

*   [Irmak, E](#ch13.xhtml#r169b)., & Ertas, A. H. (2016). A review of robust image enhancement algorithms and their applications. *2016 IEEE Smart Energy Grid Engineering (SEGE)*, 371–375。

*   [Jamkhandikar, D](#ch13.xhtml#r170b)., Mytri, V. D., & Shahapure, P. (2014). Object detection and tracking in real time video based on color. *International Journal of Engineering Research and Development*, *10*, 33–37。

*   [Jaya, V. L.](#ch13.xhtml#r171b), & Gopikakumari, R. (2013). IEM: a new image enhancement metric for contrast and sharpness measurements. *International Journal of Computer Applications*, *79*(9), 1–9。

*   [Jintasuttisak, T](#ch13.xhtml#r172b)., & Intajag, S. (2014). Color retinal image enhancement by Rayleigh contrast-limited adaptive histogram equalization. *2014 14th International Conference on Control, Automation and Systems (ICCAS 2014)*, 692–697。

*   [Kang, W.-X](#ch13.xhtml#r173b)., Yang, Q.-Q., & Liang, R.-P. (2009). The comparative research on image segmentation algorithms. *2009 First International Workshop on Education Technology and Computer Science*, *2*, 703–707。

*   [Kober, V](#ch13.xhtml#r174b). (2006). Robust and efficient algorithm of image enhancement. *IEEE Transactions on Consumer Electronics*, *52*(2), 655–659。

*   [Kumar, A. K. P. B. K](#ch13.xhtml#r175b)., Mahankud, A., & Mishra, P. K. (2016). Detection of objects in a video of traffic. *International Research Journal of Engineering and Technology*, 3(5), 676–678。

*   [Kumar, N](#ch13.xhtml#r176b)., Pathan, E., Yadav, L., & Ransubhe, V. (2015). Video surveillance over camera network using Hadoop. *International Journal of Innovative Research in Computer and Communication Engineering*, 4(1), 1111–1115。

*   [Li, J](#ch13.xhtml#r177b)., Wu, Q., Lian, X., & Sun, J. (2016). Real-time video copy detection based on Hadoop. *2016 Sixth International Conference on Information Science and Technology* *(ICIST)*, 492–497。

*   [Min, H](#ch13.xhtml#r178b)., Jia, W., Wang, X.-F., Zhao, Y., Hu, R.-X., Luo, Y.-T., Xue, F., & Lu, J.-T. (2015). An intensity-texture model based level set method for image segmentation. *Pattern Recognition*, *48*(4), 1547–1562。

