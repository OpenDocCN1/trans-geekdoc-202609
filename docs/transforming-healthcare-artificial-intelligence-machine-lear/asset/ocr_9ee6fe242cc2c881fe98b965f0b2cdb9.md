# Yoga pose estimation using PoseNet model 273

CNNs to process video frames from a webcam. These CNNs are designed to detect and estimate keypoints on the human body, as the positions of joints and limbs, with high accuracy. PoseNet's CNN architecture consists of multiple convolutional layers that extract features from the video frames, followed by fully connected layers that predict the coordinates of keypoints. This process provides a detailed map of the user's pose, including the location of keypoints in the x and y dimensions. The data from this stage is crucial for subsequent pose classification and tracking, as it establishes the foundation upon which all further analysis is built. p5.js is utilized to handle video capture and display, seamlessly integrating PoseNet's output into the user interface and providing real-time visual feedback [11].

# 13.2.3 Real-time pose classification and tracking

In the second phase, the project focuses on classifying and tracking yoga poses using the keypoint data obtained from PoseNet. This is achieved with a custom-trained neural network and developed using ml5.js. The neural network uses fully connected layers to process the input keypoint data and classify it into one of several predefined yoga poses: Mountain, Tree, Downward Dog, Warrior II, and Chair. The network is trained on a labeled dataset, where each set of keypoint coordinates is associated with a specific pose yoga. During classification, the network predicts the pose patterns on the keypoint data.

Kalman Filtering is a mathematical technique used for real-time tracking and noise reduction. It is employed to enhance tracking accuracy by smoothing out the detected keypoint positions and reducing noise. Kalman filters predict the future positions of keypoints by their past movements, ensuring stable and reliable tracking despite potential fluctuations. The integration of ml5.js for classification and Kalman filtering for tracking ensures each detected pose is consistently and accurately classified. p5.js is used to render the tracking results on the canvas, providing users with visual feedback and real-time updates.

```
State Prediction = \tilde{X}(k|k-1) = A\tilde{X}(k-1|k-1) + Bu(k-1)  (13.4)
```

```
Error Covariance Prediction = P(k|k-1) = A \cdot P(k-1|k-1)A^T + Q  (13.5)
```

```
Kalman Gain = K(k) = P(k|k-1)*H^T * (H*P(k|k-1)*H^T + R)^{-1}  (13.6)
```

```
State update = \tilde{X}(k) = \tilde{X}(k|k-1) + K(k)*(z(k) - H\tilde{X}(k|k-1))  (13.7)
```

```
Error Covariance Update = P(k|k-1) = (I - K(k)*H)*P(k|k-1)  (13.8)
```