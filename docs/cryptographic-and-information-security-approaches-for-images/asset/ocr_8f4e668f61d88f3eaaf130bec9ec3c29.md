+   26.5.2 Keypoint-Based Methods..................................................782
+   26.5.2.1 Feature Extraction Algorithms........................................782
+   26.5.2.2 Matching Techniques..................................................783
+   26.5.2.3 Comparison of Methods for CMFD .....................................783
+   26.6 RKEM-SIFT Method.........................................................784
+   26.6.1 Extraction of Scale Space Extrema......................................784
+   26.6.2 Improving the Accuracy of Location and Removal of Unstable Extrema .............................................................786
+   26.6.3 Assignment of Orientation for Each Feature............................788
+   26.6.4 Removal of Unnecessary Keypoints......................................788
+   26.7 Description of the Proposed CMFD Method Based on RKEM-SIFT .....789
+   26.7.1 Image Features Extraction .............................................789
+   26.7.2 Keypoints Matching.....................................................790
+   26.7.3 Clustering..............................................................790
+   26.7.4 Removal of Mismatches..................................................790
+   26.8 Experiment and Results ..................................................792
+   26.8.1 Evaluation Criteria....................................................792
+   26.8.2 Examining the Performance of the Proposed Method by the MICC-F220 Database...........................................................793
+   26.9 Conclusion...............................................................794
+   Exercises....................................................................794
+   References ...................................................................794

# 26.1 Introduction

Information security means the protection of information and information systems from unauthorized activities, which include access, use, disclosure, reading, copying or recording, tampering, changing, and manipulation. The main concepts in information security are information confidentiality, integrity, and availability. Integrity means preventing unauthorized change of information and detecting the change in case of unauthorized manipulation of information. Integrity is violated when information is changed in an unauthorized way not only during transfer but also in use or storage. Today, the development of image processing and image editing software such as Adobe Photoshop®, and Photo Editor has caused created image forgery, and these images ultimately cause limitations in the information security system (Huang et al. 2008; Birajdar and Mankar 2013). In this chapter, while reviewing the methods of copy-move forgery detection, a method is presented that has a high accuracy in detecting forged areas. The Scale Invariant Feature Transform (SIFT) algorithm is one of the most common methods of forgery detection based on keypoints. One of the disadvantages of SIFT is the extraction of inappropriate keypoints, which cause an increased FP-rate and interference in the forgery areas detection. In this chapter,