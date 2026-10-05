

Arduino 微控制器使用脉冲宽度调制 (PWM) 来控制光强度或改变风扇速度。

## 4 结果与讨论

本节详细介绍了从所提模型获得的实现结果。

## 4.1 CV 模块

项目中开发的计算机视觉模块用于检测手的存在。它在手部周围画一个边界框，表示在该框区域内需要检测手势。它还标记了手部的节点点，即手指上的点以及我们手部重要的运动点，如图 3 所示。

![](img/a35f8e852e0ee65e528c95ad0821783b_70_0.png)

图 3. 检测到手。

## 4.2 手势识别

随后，Python 模块会跟踪节点点并识别用户显示的手势。在图 4 中，计算了食指和拇指之间的距离。该距离可以用于增加家用灯光的亮度，或用于改变风扇的速度。在图 5 中，我们可以观察到食指和拇指之间的距离在缩短，这表示降低灯泡的亮度或强度。

![](img/a35f8e852e0ee65e528c95ad0821783b_70_1.png)

图 4. 检测到手势。

![](img/a35f8e852e0ee65e528c95ad0821783b_70_2.png)

图 5. 手势发生变化。

## 4.3 基于手势的灯控制

Python 模块将通过串口通信向 Arduino 发送命令。如图像所示，手势与图 5 相同，表示关闭灯泡。图 6 中的 LED 没有发光。

当我们增加食指和拇指之间的距离时，该值会被映射到相应的亮度范围（0 到 255），并且该值通过脉冲宽度调制来改变亮度。因此，在图 7 中我们可以看到 LED 的强度随着食指和拇指之间的距离而变化。

![](img/a35f8e852e0ee65e528c95ad0821783b_71_0.png)

图 6. 基于手势输入的灯光关闭。

![](img/a35f8e852e0ee65e528c95ad0821783b_71_1.png)

图 7. 基于手势输入的光强度变化。

## 结论与未来展望

该框架能够自动化并控制所有家电器。该系统将检测用户所需的所有手势，并可以根据给定参数控制或自动化家电器。手势检测和电器自动化的效率可以提高。手势检测和自动化的响应时间可以进一步减少。

## 参考文献

- [1] Agarwal Mohammad Hasnain, Rish S, Mayank P, Swapnil G. “Smart Home Automation Using Computer Vision and Segmented Image Processing.” In 2019 International Conference on Communication and Signal Processing (ICSP), IEEE, 2019.
- [2] Faris Alushay, Tawfik Al-Hadrami, Kenny Avuson-Day. “Toward Home Automation: An IoT Based Home Automation System Control and Security.” 2021 International Congress of Advanced Technology and Engineering (ICOTE), IEEE.
- [3] Xin Li, Yilang Shi. “Computer Vision Imaging Based on Artificial Intelligence.” 2018 International Conference on Virtual Reality and Computer Systems (ICRIS).
- [4] G.V. Naages Kumar, A. Bhaya, B. Bajaj, S. Dhananjay, P. Vikasitha, R. Rafi. “Smart Light Intensity Control Using Potentiometer for Energy Conservation,” 2021 International Conference on Recent Trends on Electronics, Information, Communication & Technology (RTEICT)
- [5] Nurshayati Adnan, Noorfazila Kamalal, Kalavani Chellappan. “An IoT Smart Lighting System Based on Human Activity.” 2019 IEEE 14th Malaysia International Conference on Communication (MIC).
- [6] Meenakshi, Panwar. “Hand Gesture Recognition Based on Shape Parameters.” 2012
- [7] Syed Ali, Waqas Mahmood. “Smart Automation Using IoT.” In International Journal of Engineering and Manufacturing, 2020.
- [8] Quentin Smet, Guillaume Hannous. “Skeleton-based.” In IEEE Society on Computer Vision and Pattern Recognition (CVPR), 2016.
- [9] Aron Amir, David Berg, Timothy Melton, Jeffrey McKinley. “Dynamic.” In IEEE Xplore, 2017.
- [10] Qiqi Miao, Yuan Li, Xiaochao Chao. “Multimodal.” published in IEEE Xplore, 2018.
- [11] Hu Wang, Song Wang, Zhen Li. “Large-scale.” published in IEEE Xplore, 2018.
- [12] Cristian Stojanu, Petru Bogdan. “An IoT Based.” In Polite University of Timisoara, 2021.
- [13] Biplal Sarma, Debajit Chakraborty. “Review-based.” In International Conference, 2017.
- [14] Ahmed Saeed, Mohammed Hassan, Mohamed M. “Early detection.” In International Journal of Engineering, 2020.
- [15] Siddharth Wadhwani, Uday Singh, Shraddha Divedi. “Smart.” In International Research Journal of Engineering and Technology (IJET), 2019.
- [16] Mansisha Kasa, Debasahi Bhattachary. “Face.” In International Journal of Security and Its, 2016.

