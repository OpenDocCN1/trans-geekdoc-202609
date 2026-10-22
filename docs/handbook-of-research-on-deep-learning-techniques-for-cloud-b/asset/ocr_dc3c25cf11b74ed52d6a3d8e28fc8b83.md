In 2020, Glenn Jocher produced Yolov5, which exploratory comparisons revealed had a slightly quicker prediction speed but the same accuracy as Yolov4 (Zhu et al., 2021). YOLOv5 has five versions, out of which YOLOv5s has the quickest detection time with few parameters.

The YOLOv5 network structure as depicted in Figure 2 consists of following three main parts:

+   - **Backbone:** Backbone is employed for extracting the key characteristics at various granularities from an input image.
+   - **Neck:** From the features that the backbone network has extracted, the neck is used to create feature pyramids. Feature pyramids enable the framework in generalising object scaling, i.e., it helps in the recognition of objects at various scales and sizes.
+   - **Head:** The final step in the prediction process is the construction of the final output using anchor boxes, objectness scores, class probabilities, and bounding boxes.

# PROPOSED METHODOLOGY

The lightweight YOLOv5 network based on the attention mechanism and bi-directional feature pyramid network was proposed to detect the dense tomatoes given multi-mode and multi-scale characteristics in natural environment. Firstly the coordinate attention module (CA) was added to the backbone network to capture the cross-channel information and position perception in order to detect and locate the dense tomatoes. Secondly, the bi-directional feature pyramid network (BFPN) which is an improved version of the PANet feature fusion network is added to the network in order to improve the detection accuracy of the tomatoes at different scales.

# Attention Mechanism

The original YOLOv5 network model possesses a poor ability to detect small and dense items due to the fact that it readily loses features derived from dense objects and small objects during the reasoning process. Hou et al. (2021) proposed coordinate attention mechanism shown in Figure 3 is a novel method that embeds location(positional) data into channel attention, enabling the network to concentrate on huge significant regions with a low computational cost. Coordinate information integration and coordinate attention generation are the two processes that make up this process. In order to solve the problem of location loss of information pertaining to location caused by prior attention methods like CBAM (Woo et al., 2018), CA split channel attention into two separate one-dimensional feature coding procedures that aggregated features across two spatial directions.

A computing unit known as a CA block can output data of the same size as the intermediate feature tensor Y while accepting any intermediate feature tensor X as input. At the same time, it has the effect of improving representation.

The CA block is added to the Proposed YOLOv5 model after the 4, 6, 8, 20, and 23 layers of the Original YOLOv5 model. The tomato images are provided as input to the model after data pre-processing in order to extract features, which are then entered into the neck region of the model through the CA module for prediction. This way the proposed model accurately detects the small dense fruits.