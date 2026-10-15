
# 2: Tasks in facial analysis

In this survey, we classify the tasks in facial analysis into two categories: (1) `Face Detection and Recognition` and (2) `Attribute Prediction` (refer to [Fig. 2](#Ch007_169-221_S0169716123000020.xhtml#f0015)). The tasks falling into these two categories cover a wide spectrum of facial analysis tasks. The problems are detailed in the following sections.

![Fig. 2 Illustrating the different tasks in facial analysis. (Top left) The task of face verification where the identity of subjects is the same for the first set of face images and different for the second set. (Top right) Face identification where the gallery contains two subjects—A and B. Probe X is identified as subject A since it is the closest match. (Bottom) The task of attribute prediction where values for three different attributes- `gender`, `wearing earrings`, *is smiling*‑ are predicted, given the same set of face images. The images and gender annotations are taken from the MORPH dataset (Rawls and Ricanek, 2009).](images/S0169716123000020/f07-02-9780443184307.jpg)

[Fig. 2](#Ch007_169-221_S0169716123000020.xhtml#B-f0015) Illustrating the different tasks in facial analysis. (Top left) The task of face verification where the identity of subjects is the same for the first set of face images and different for the second set. (Top right) Face identification where the gallery contains two subjects—A and B. Probe X is identified as subject A since it is the closest match. (Bottom) The task of attribute prediction where values for three different attributes- `gender`, `wearing earrings`, `is smiling`‑ are predicted, given the same set of face images. The images and gender annotations are taken from the MORPH dataset ([Rawls and Ricanek, 2009](#Ch007_169-221_S0169716123000020.xhtml#bb0675)).

###  2.1: Face detection and recognition

The tasks in this category include `face detection`, `verification`, and `identification`. `Face recognition` comprises `face verification` and `identification`. These tasks use `face detection` algorithms as pre‑processing.

####  2.1.1: Face detection

The task of `face detection` involves detecting the region of an image containing the face through image coordinates. Some algorithms provide a confidence score for each detected face indicating the algorithm's confidence in the prediction. The performance of algorithms is measured through the `mAP` score. While popular datasets contain multiple faces in one image, some research only involves one face per image. In such cases, the detection accuracy of the face detector is calculated. `Face detection` algorithms are used as a pre‑processing step for `face recognition` pipelines.

####  2.1.2: Face verification and identification

In the `face verification` task, two face images are compared in a 1:1 fashion and predicted to be either a match or a non‑match. Most algorithms provide a continuous match score between 0 to 1, and this score is thresholded at a particular value above/below which a pair is considered as a match/non‑match. For this task, the verification accuracy of a model is evaluated using the verification pairs. Further, the True Positive Rate (`TPR`) at a particular False Positive Rate (`FPR`) is also computed. `TPR` values at 0.01 and 0.001 `FPR` values are commonly reported.

In `face identification`, the goal is to identify the person present in a given face image. In the most common identification scenario, a given face image (probe) is compared against a set of stored face images (gallery) in a 1:N fashion. The face image is identified as the closest match from the gallery. The algorithms are evaluated using identification accuracy and CMC curves.

###  2.2: Attribute prediction
