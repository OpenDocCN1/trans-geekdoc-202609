![](bbox=[0.17, 0.11, 0.83, 0.34])

# 3.2. Annotation

Our annotate method detects the person class in each frame using a pre-trained YOLOv5 model, and then stores the bounding box coordinates in a CSV table. In the next step, we examine each frame and correct the annotation results for fall and upright, as shown in Table 1. Figure 2 shows the detection results of YOLOv5 and Manual post-correction.

Table 1. Example bounding box coordinates and annotations.

| File Name | Xmin | Ymin | Xmax | Ymax | YOLOv5 Annotations | Manually Corrected Annotations |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 000018.jpg | 120 | 101 | 187 | 200 | person | upright |
| 000019.jpg | 109 | 113 | 194 | 198 | person | upright |
| 000020.jpg | 108 | 116 | 195 | 197 | person | fall |
| 000021.jpg | 107 | 125 | 198 | 200 | person | fall |
| 000022.jpg | 107 | 125 | 198 | 200 | person | fall |
| 000023.jpg | 107 | 125 | 198 | 200 | person | fall |

# 3.3. Proposed Framework

The proposed framework is shown in Figure 3, which employs a two-stage framework to detect falls in low-light indoor environments. The object detection model is used as the main component of the fall detection system to further elaborate on the proposed technique. In the first stage, the captured video frames are pre-processed to improve the visual quality of the footage. This is accomplished using a dual illumination estimation-based exposure correction technique field [40]. The goal of this step is to adjust the brightness, contrast, and detail of the video frames so that later stages can detect falls more accurately. On the enhanced video frames, the second stage implements a deep-learning-based approach for person tracking and detection. This is accomplished using a technique known as people tracking by detection, which involves using an object detection model to track the movements of people in video footage. The algorithm can detect when a person falls by analysing the motion patterns of the tracked objects. To detect falls in low-light indoor environments, the proposed fall detection system utilizes a sophisticated combination of exposure correction and deep-learning-based people tracking by detection algorithms. By improving the visual quality of the video footage and leveraging advanced object detection techniques, the system can improve the accuracy and reliability of fall detection.