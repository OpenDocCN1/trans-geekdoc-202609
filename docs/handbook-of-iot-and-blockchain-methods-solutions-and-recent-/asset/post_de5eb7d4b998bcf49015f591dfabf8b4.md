
![](img/cd1801130f8a9057bd2f396e8025ba69_101_0.png)

FIGURE 5.3 Circuit Diagram of Proposed work.

![](img/cd1801130f8a9057bd2f396e8025ba69_101_1.png)

FIGURE 5.4 General Speech Recognition Process.

change them into digital format, and analyze that sound. Figure 5.4 represents the general speech recognition system.

Simple Speech recognition module is categorized into three parts as follows:

- 1. Input: Human: Voice is used as source of input for this module.
- 2. Neural Network: Natural Language Processing (NLP) and Neural Network (NN) break speech into a number of components that can help to easily interpret it. After conversion, these components change into a digital state and analyze these states. NN is used to train the dataset of specific words and phrases and create predictions for the new voice related to input data.
- 3. Output: In the last stage, it transcribes the input voice into text format.

## 5.2.4 TENSOR FLOW

TensorFlow [18] is an open-source platform especially designed for machine learning and deep learning that helps to provide end-to-end solutions. It provides a huge number of tools and flexible platforms that motivate and push researchers to extend their creativity limit. TensorFlow gives stable Python and C++ APIs. Moreover, these APIs are compatible with other languages in unstable versions. The main features of TensorFlow are as follows:

![](img/cd1801130f8a9057bd2f396e8025ba69_102_0.png)

ALGORITHM 5.1 Proposed Workflow.

- 1. **Model Building:** Training and Building models in machine learning is quite easy compared to other system models. With the introduction of Keras, this helps to improve model debugging and model iteration.
- 2. **Robust:** Due to the power of clouds, it is easy to train and train deploy models anywhere.
- 3. **Research Experimentation:** This provides a flexible architecture that helps to implement from idea to practical implementation. Especially regarding results, it provides these in the form of graphs and statistical form as well.

## 5.2.5 PROPOSED ALGORITHM

Algorithm 1 presents a proposed workflow. In this system, the arm is activated through the voice and if there is no matching voice, it rechecks. In the next step, voice is converted into plain text, processing this text in the TensorFlow and checking the libraries and detecting the object with the convolutional network. The arm is synchronized with the TensorFlow. A camera captures the image which is processed through the use of installed OpenCV in the Raspberry Pi. Sensors check the location of the object. If the object is within range of the robotic arm it will grasp it; otherwise the robotic arm will not move. With the use of text to speech, it can convert into voice instructions such as object name, specification etc.

## 5.3 RESULTS AND DISCUSSION

In this section, the input signal (see Figure 5.5) is used to recognize the particular object. For image recognition, TensorFlow is deployed and measured through the accuracy score of the model. The accuracy of the training dataset is 0.697.

![](img/cd1801130f8a9057bd2f396e8025ba69_103_0.png)

**FIGURE 5.5** Input Signal of Hello.

![](img/cd1801130f8a9057bd2f396e8025ba69_104_0.png)

FIGURE 5.6 Left Side: Direction of Robotic Arm; Right Side: Detection of Object.

![](img/cd1801130f8a9057bd2f396e8025ba69_104_1.png)

FIGURE 5.7 Activated mode of Voice and Image Recognition.

In this section, Figure 5.6 and Figure 5.7 represent the outcome of the results from our proposed work. In Figure 5.6, the terminal shows the direction of the robotic arm which moves forward or backward. Figure 5.6 shows the detection of an object with a yellow screen. The most noteworthy point of this proposed system is that it works remotely through use of the internet. Through the use of SSH, the robotic arm captures images and grasps crucial objects. Figure 5.7 presents an activated mode of image and speech recognition.

Figure 5.8 represents the system proposed to fetch objects with a camera mounted on the arm. With the aid of speech recognition, it is activated through voice. Below
![](img/cd1801130f8a9057bd2f396e8025ba69_105_0.png)

FIGURE 5.8 Robotic arm enabled with Camera.

the arm, IR and ultrasonic sensors are mounted that help camera to locate the object location as well as maintain an exact distance between the object and arm.

## 5.4 CONCLUSION

In this chapter, a vision- and voice-based robotic arm is proposed. This proposed system provides an opportunity to tackle real-world problems such as remote surveillance; tasks impossible for humans. The integration of day-to-day life problems with complex visions can improve image processing research. OpenCV libraries installed on the Raspberry Pi allow focus on image processing with minimal labor. In this study, the robotic arm is equipped with a camera, ultrasonic sensor and IR sensor that increases the accuracy of selection of objects from exact coordinates. Object detection and location extraction techniques are executed with the aid of image processing methods; namely object extraction techniques, matching pre-installed templates.

## REFERENCES

- 1. Juang, J. G., Tsai, Y. J., & Fan, Y. W. (2015). Visual recognition and its application to robot arm control. Applied Sciences, 5(4), 851–880.
- 2. Manigpan, S. (2010). A Simulation of 6R Industrial Articulated Robot Arm Using Neural Network (Doctoral dissertation, University of the Thai Chamber of Commerce).
- 3. Ejiri, M. (2007, November). Machine vision in early days: Japan’s pioneering contributions. In Asian Conference on Computer Vision (pp. 35–53). Springer, Berlin, Heidelberg.
- 4. OpenCV Introduction: https://opencv.org/ (Accessed on 16/11/2019).
- 5. Bradski, G., & Kaehler, A. (2008). Learning OpenCV: Computer vision with the OpenCV library. “O’Reilly Media, Inc.”.
- 6. Furuta, K. A. T. S. U. H. I. S. A., Kosuge, K. A. Z. U. H. I. R. O., & Mukai, N. O. B. U. H. I. K. O. (1988). Control of articulated robot arm with sensory feedback: Laser beam tracking system. IEEE Transactions on Industrial Electronics, 35(1), 31–39.
- 7. MunaSinghe, S. R., Nakamura, M., Goto, S., & Kyura, N. (2001). Optimum contouring of industrial robot arms under assigned velocity and torque constraints. IEEE Transactions on Systems, Man, and Cybernetics, Part C (Applications and Reviews), 31(2), 159–167.
- 8. Koga, M., Kosuge, K., Furuta, K., and Nosaki, K. (1992). Coordinated motion control of robot arms based on the virtual internal model. IEEE Transactions on Robotics and Automation, 8(1), 77–85.
- 9. Efe, M. Ö. (2008). Fractional fuzzy adaptive sliding-mode control of a 2-DOF direct-drive robot arm. IEEE Transactions on Systems, Man, and Cybernetics, Part B (Cybernetics), 38(6), 1561–1570.
- 10. Wang, W. J., Huang, C. H., Lai, I. H., & Chen, H. C. (2010, August). A robot arm for pushing elevator buttons. In Proceedings of SICE Annual Conference 2010 (pp. 1844–1848). IEEE.
- 11. Juang, J. G., Tsai, Y. J., & Fan, Y. W. (2015). Visual recognition and its application to robot arm control. Applied Sciences, 5(4), 851–880.
- 12. Chen, O. T. C., Zhang, Y. C., Lin, Z. K., Kuo, P. I., & Lee, Y. L. (2019, August). Camera-in-Hand Robotic Arm Using a Deep Neural Network to Realize Unmanned Store Service. In 2019 IEEE Intl Conf on Dependable, Autonomic and Secure Computing, Intl Conf on Pervasive Intelligence and Computing, Intl Conf on Cloud and Big Data Computing, Intl Conf on Cyber Science and Technology Congress (DASC/PiCom/CBDCom/CyberSciTech) (pp. 833–839). IEEE.
- 13. Kakde, Y., Bothe, N., & Paul, A. (2019). Real Life Implementation of Object Detection and Classification Using Deep Learning and Robotic Arm. Available at SSRN 3372199.
- 14. Kumbhar, S., Mathurekar, D., & Lobo, D. (2019). Robotic Arm with Vision (Doctoral dissertation).
- 15. Raspbian Operating System. www.raspbian.org/ (Accessed on 17/11/2019)
- 16. Graves, A., Mohamed, A. R., & Hinton, G. (2013, May). Speech recognition with deep recurrent neural networks. In 2013 IEEE international conference on acoustics, speech and signal processing (pp. 6645–6649). IEEE.
- 17. Hinton, G., Deng, L., Yu, D., Dahl, G., Mohamed, A. R., Jaitly, N., ... & Sainath, T. (2012). Deep neural networks for acoustic modeling in speech recognition. IEEE Signal processing magazine, 29.
- 18. TensorFlow: www.tensorflow.org/ (Accessed on 10/12/2019)
