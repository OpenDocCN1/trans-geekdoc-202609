**Table 1.** The 15 factors of evaluated score for each respondent in the questionnaire.

The questionnaire survey involved displaying virtual scenes from each location to the interviewees using a VR Google tool. The survey occurred at Nakamura Lab, Department of Civil Engineering, Meijo University. There are several benefits to using virtual reality technology for conducting the questionnaire survey. Firstly, it allows interviewees to immerse themselves in the surrounding environment of each scene, enabling them to perceive the scene better and understand the QoL in those settings compared to simply watching video clips on a computer monitor. Secondly, interviewees can control their viewing direction, enabling them to focus on specific elements such as the walking path, sky, trees, or buildings according to their preferences. Finally, because the scenes were collected from different countries, it would be impractical to take interviewees to the actual locations physically. Utilizing VR tools offers a cost-effective solution for surveying such circumstances.

# 4.3. *Feature Extraction Using Image Recognition*

This subsection details a feature extraction approach to extract features from prior-recorded videos. This approach consists of two processes, object detection and semantic segmentation.

Each video is captured into pictures frame by frame and then passed to an object detection model, YOLOv4, and a semantic segmentation model, DDRNet-23-Slim. The results of the YOLOv4 model are shown in Figure 9, which visualizes the object detected with bounding boxes, and DDRNet-23-Slim in Figure 10, which visualizes highlight colors at each pixel.

The YOLOv4 model and the DDR-Net-23-Slim model extract the image information from the video. The extracting results from YOLOv4 consist of 17 classes (as shown in Table 2), while the extracting results from DDR-Net-23-Slim consist of 19 classes (as shown in Table 3).