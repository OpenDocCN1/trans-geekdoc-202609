# Table 9.6 Comparing the inference time (second) of the proposed single-stage CCN approach with conventional dual-stage approaches.

| Block Size | 16 x 16 | 32 x 32 | 64 x 64 | 128 x 128 |
| :--- | :--- | :--- | :--- | :--- |
| **CCN-YOLO** | 2.82 | 2.82 | 2.82 | 2.82 |
| Original YOLO | 2.81 | 2.81 | 2.81 | 2.81 |
| GAUSS+YOLO | 8.81 | 9.25 | 11.65 | 14.15 |
| ADAGIO+YOLO | 8.81 | 9.24 | 11.67 | 14.13 |
| CS-SM+YOLO | 8.80 | 9.21 | 11.47 | 13.69 |
| **CCN-SSD** | 2.45 | 2.45 | 2.45 | 2.45 |
| Original SSD | 2.44 | 2.44 | 2.44 | 2.44 |
| GAUSS+SSD | 8.44 | 8.88 | 11.28 | 13.78 |
| ADAGIO+SSD | 8.44 | 8.87 | 11.30 | 13.76 |
| CS-SM+SSD | 8.43 | 8.84 | 11.10 | 13.32 |

performing object detection side-by-side with a compressive sensing module using different types of sensing matrices. It is worth noting that the conventional compressive sensing approaches require O(M×N/B) floating-point multiplications at the front end for data embedding, and the complexity of these strategies depends on the block size B. On the other hand, the CCN models need much fewer multiplications, and it is 3.1–5.5 times more efficient than the conventional approaches.

The SensCamera was implemented as a prototyping wireless smart camera system with an integrated CCN-SSD algorithm for object detection and image compression. The camera was built with a 1280-720 pixel RGB image sensor, which captured video images at the speed of 25 frames per second (FPS). Frame by frame, the video image was streamed into the FPGA device, which was optimized for power-efficient implementation of the CCN-SSD algorithm. The experiment showed that the prototyping SensCamera could process 20–25 FPS, which was adequate for a wide range of IoT and surveillance applications. Further examination showed that the performance metric of FPS was partially affected by the number of potential objects detected in the image.

Fig. 9.8 shows the SensCamera running in real-time for object detection and image compression. Thanks to algorithm-level and hardware-level optimization, the peak power consumption of the SensCamera was as low as 13.97 watts. The FPGA implementation of the CCN-SSD algorithm consumed 7.2 watts on average.