2. Details of conventional and upcoming video data sets for IR tracking along with the evaluation metrics utilized to determine the detection and tracking efficiency corresponding to the model has also been investigated.

# 6.2 LITERATURE REVIEW

# 6.2.1 DETECTION-BASED AND DETECTION-FREE THERMAL TRACKING TECHNIQUES

Two principal approaches., i.e., detection-based, and detection-free tracking (Figure 6.3) have been used to carry out thermal object tracking. In detection-based tracking using deep learning, a pre-trained detector is fed with an uninterrupted video sequence which, in turn, gives tracking trajectories based on detection proposition. The technique has been widely used as it detects the new objects and automatically terminates the disappearing one. Detection-free tracking involves the manual establishment of a predetermined number of objects in the first frame, which are then localized in subsequent frames. These trackers often fail in the cases where new objects occur in the intermediate frames.

Thermal IR frames often suffer from unwanted attributes which hinder the discriminatory features of the object of interest. Liu et al. (2017) has utilized the discriminative representation capability of a convolutional neural network (CNN) to perform thermal object tracking. An ensemble tracker based on a correlation filter having multiple convolutional layer features have been proposed. In the initial stage, a pre-trained CNN which extracts the varied features of a thermal IR object from multiple convolutional layers has been used. Further, various weak trackers corresponding to the extracted features are constructed with the help of a correlation filter. The weak trackers constructed additionally contributes to the object location response maps which have been merged to achieve better response results. Finally, an effective strategy for scale estimation has been exploited to enhance the tracking efficacy (Rani et al., 2023).

Li et al. (2019) implemented HSSNet, which is a thermal IR tracker based on a spatially ordered Siamese CNN. A Siamese CNN, which concatenates features from multiple convolutional layers, has been designed to gather the spatial and semantic information associated with the object. The network has been trained in an end-to-end manner on a visible video detection data set to acquire correlation among the matching objects. The pre-trained network is then transferred into a thermal domain to estimate the likeness between target object and its equivalent template. Eventually, the candidate which highly resembles the object being tracked has been located.

![](bbox=[0.12, 0.78, 0.9, 0.9])

FIGURE 6.3 (a) Detection-based tracking vs (b) Detection-free tracking.