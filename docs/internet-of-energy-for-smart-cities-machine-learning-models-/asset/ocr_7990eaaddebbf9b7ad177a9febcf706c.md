# 10.3.3 AUTOMATIC CONTROL OF ELECTRICAL APPLIANCES

Figure 10.3 demonstrates the automatic detection and control mechanism. Images are captured at a fixed interval of time from a camera device in the room and each image is sent to the server for processing. At the server-side, when the image is provided, it detects the presence of person(s) in it by dividing the image into different grid sections. The appliance in a particular section will turn ON if the presence of a person is detected in that section. This is implemented in the prototype using the OpenCV library for Image Processing. OpenCV is an open-source library that is mainly used to deal with problems and solutions related to Computer Vision applications and also helps to enhance the algorithms of Machine Learning. An API request is sent to the raspberry pi server with the corresponding pin number and hence, the state of the appliance is controlled.

![](bbox=[0.135, 0.345, 0.865, 0.515])

Figure 10.3 Automatic detection and control

# 10.4 EXPERIMENTAL SET-UP AND RESULTS

The relay module is connected to the raspberry pi through GPIO pins. These pins are used to give signals to relay modules. They consist of two signals, HIGH and LOW. When the signal is HIGH, the relay channel is turned ON and when the signal is LOW, the relay is turned OFF. In the prototype, a 4-channel relay module is used, i.e. up to four devices can be connected to one module at a time. Each device on the relay channel has a dedicated pin connected to raspberry pi’s GPIO. The script is programmed according to the requirements and then the module is controlled by running that script. Figure 10.4 shows the circuit of the experimental set-up of the prototype.

Each relay has three sockets in which the negative pin of the LED is connected to the second socket, while the positive pin is connected to the power source (switchboard), and from the third socket a wire is connected to the negative of the power source (switchboard). Thus, this acts as a simple switch like the one in our home, but it is