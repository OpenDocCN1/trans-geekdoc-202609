![](bbox=[0.1, 0.1, 0.45, 0.65])

Figure 9: Recurrent neural networks for sequential anomaly detection in visual data.

changes its direction, the RNN recognizes those conditions involving analysis of the current frame and previous frames.

Since RNNs are used for visual anomaly detection, the visual data needs to be transformed into a suitable sequential form. A common method is to resend the video frames as feature vectors by using CNNs and extracting a feature map from each frame. These feature vectors containing basic information of the visual content are then passed into a model based on RNN to consider temporal relationships. The applicability of CNNs in the spatial feature extraction and RNNs in temporal modeling means that the system can attend to both the content of the frames and their temporal