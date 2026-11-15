![](bbox=[0.19, 0.1, 0.76, 0.33])

Figure 9.1 Typical scenario of applying wireless smart cameras for surveillance purpose. One or multiple camera systems can be deployed at the front end to perform image acquisition, compression, and object detection. The compressed sequential images are transmitted through WIFI to the back-end server, where images are decompressed for visualization and further analysis.

has an efficiency improvement of more than 3× compared with traditional methods [13]. Thirdly, it is based on backpropagation used to train deep neural networks, so it is significantly more efficient than the NuMax [12] and ADAGIO [14] algorithms to estimate near-isometric sensing matrix. The proposed method extends the data-driven compressive sensing method to large-scale data sets.

From a system point of view, there are two main advantages for applying the SensCamera. First, by supporting object detection at the front end the smart camera only has to activate wireless image transmission when a certain event was detected. For the example of typical face detection applications, the SensCamera prototype only starts to transmit image frames when human faces are detected, which can dramatically save communication traffic and data storage requirement. Secondly, the SensCamera can compress the detected video images without computational overhead, which further improves computation efficiency. The whole system consists of one or multiple wireless cameras and a postprocessing computer, which receives the compressed images from the cameras through the WIFI transmitter.

The main contributions are as follows.

+   * A novel hardware-friendly compressive convolution network (CCN) is proposed, which can simultaneously achieve object detection and image compression in one network.