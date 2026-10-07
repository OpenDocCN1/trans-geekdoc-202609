# ML-Based Driving Assistance System ■ 197

![](bbox=[0.121, 0.114, 0.875, 0.373])

Figure 10.2 Use case diagram.

![](bbox=[0.121, 0.436, 0.875, 0.739])

Figure 10.3 Process flow.

# 10.4 Image Capturing

Webcams are used to capture input images. An infinite loop returns every frame from the webcam until it is accessed. The cv2.VideoCapture(0) method of the OpenCV library is used to capture video and set the capture object [3]. Each image is stored in a video frame variable by reading () in the frame.