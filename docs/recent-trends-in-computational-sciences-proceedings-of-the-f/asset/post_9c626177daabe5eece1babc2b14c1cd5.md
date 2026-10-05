
# 2 SURVEY OF POSTURE DETECTION MODELS

Weili Ding in his paper on Human posture recognition proposed a solution to identify various postures using the rule-learning algorithm. With the help of a Kinect sensor, human skeleton information is extracted. Figure 1(a) illustrates the joint points of the human body, which are very important for mobility. The RIPPER rule algorithm created a high-performance entity [3]. An overview of the steps followed for posture recognition is shown in Figure 1(b).

A method suggested by students of Amity University to detect postures from time-series data using Deep Learning. The knowledge of a long short-term model and fully connected convolutional network is discussed. Tri-axial accelerometers are attached to the back of an object using nine different postures are identified. An average accuracy recorded by the model for classification is 99.91%, [4]

A solution is proposed in the IEEE Sensors Journal to use a hybrid model of machine learning and deep learning algorithms, resulting in an accuracy of more than 98%. ML algorithms are trained using cross-validation of 10-to-find precision, recall, accuracy and f-measure [5].

Students of Ehwa Womans University proposed a system that classifies the user's postures using deep learning and a specifically designed chair of Arduino hardware. Pressure and ultrasonic sensors are used. Figure 3 shows how the data is collected through the sensors. [6]

A model implemented in the Philippines uses Motion capture data and RGB-D to assess a person. The cameras are used to record the markers (39 retro-reflective) placed on the body parts of the subject. Compared to Mo-Cap data, RGB-D unfiltered has a 7.23% error rate, whereas RGB-D has a 2.73%. [7]

![](img/a35f8e852e0ee65e528c95ad0821783b_322_0.png)

(a) Joints in Human Skeleton (b) Steps in Posture Recognition.

Figure 1. Gesture recognition.

The two types of human identification algorithms are discussed in Guanjan Liu's article. The other RGB models, the extensively used techniques in the field of posture recognition include the Support Vector Machine (SVM), Dynamic Time Warping (DTW), Hidden Markov Model (HMM) and Gaussian Mixture Model (GMM). Their final rate of posture recognition was 99.01 percent, which is higher than the majority of other posture recognition [8].

An evaluation of postures carried out by a university in China uses an intelligent assessment of the whole body with the help of convolutional pose machines. To calculate the reliability of the assessment, a motion capture system was used for comparison. An average root means squared error of 4.77% was found. Not only does this system calculate the working posture also predicts risks for musculoskeletal disorders. [9]

A system developed by Varsha Bhosale, provides a method to correct yoga postures by posenet and KNN with an accuracy of 98.51%. Posenet is a learning algorithm that is used to identify points within a body to train the model. Webcam is used for input feed, which helps in acquiring real-time yoga postures. [10].

# 3 SURVEY ON AUTOMATION TECHNIQUES TOWARDS SAFETY

JoonOh Seo et al. in their paper, have proposed a 2D image-based classification approach for the ergonomic assessment. The purpose of their model is to classify the different body postures from video or time lapsed images. The dataset consists of diverse postures collected using human modelling. The classifier used is a machine learning algorithm, SVM (support vector machine). Demerits include lack of real-time consideration and consideration of the complexity of capturing postures from multiple viewpoints.

Sasha E. Mundayage in their paper, have discussed various machine learning models like decision trees, SVM, random forest and K nearest neighbor to classify the risks in postures in industrial workers while performing manual activity detection. The EMG (electromyogram) sensors are used to detect harmful activities. Decision tree outperformed the other models and a test accuracy of 99.05% was recorded. Demerits lack of data since only one participant was used to collect training data, to produce realistic results and sophisticated algorithms with large data sets [12].

HuJyeong Ryu et al. in their paper, have discussed an automated tool which is used by systems that generate postures from motion capture wearable sensors. The rule-based approach RULA, REBA, and OWAS are performed for bicycling task. It is a highly efficient approach compared to other methods; however, because mechanical analysis was carried out it is robust to continuous postures risks. Demerits include the scope of risk analysis for a single task, that is, bicycling [13].

Behnosha Par et al. have proposed a multi task learning graph approach to evaluate the different postures of humans. The proposed GCN (graph convolutional network) model's effectiveness to extract spatial features from unstructured data and how the joint positions in skeletal representations can be mapped to the model's scores to solve the observed activities labeled and kinematics such as velocity and acceleration, which are important to observe any injuries. Demerits are that the model is limited to the observed activities and considered, [14].

Maxim Fernandez et al., in their paper, have proposed a method that uses computer vision and machine learning to calculate RULA (upper limb assessment) from digital videos or signals. This computation requires worker skeleton information. The neural network model proved to be working under acquisition conditions and for single or multiple postures. Demerits are that anthropometric feature evaluations are not considered, which is useful for the prediction of the model in situations related to gender and genotypes. [15].

Amir H. Bezhad et al. in their paper, have proposed an approach using machine learning with the help of mobile sensors to perform ergonomic risk analysis and productivity analysis. Smart sensors are used to identify the activity like lift, push and load. About 80% of accuracy was recorded for 7 out of 10 activities tested. The dataset size is considered a demerit, hence for enhancement of the model a greater number of workers would be needed. [16].

# 4 SUMMARY OF LITERATURE SURVEY

From the above survey, we observed that on worker's safety in Industry 4.0 has been an area of research. Various combinations of sensors and learning and deep learning models were tested to monitor the ergonomics of worker.

| ARTIFICIAL INTELLIGENCE | | | |
|---|---|---|---|
| Machine Learning | Deep Learning | COMPUTER VISION |

* Supervised Learning
  1. ANN
  2. CNN
  3. RNN
* Unsupervised Learning
  1. BM
  2. AE
  3. SOM
* Video Analytics
  * Image Classification
  * Image Segmentation
  * Emotion Detection
  * Object Detection
  * Object Tracking
  * Face Recognition

Figure 2. Overview of AI concepts.

Figure 2 displays the various concepts that come under the scope of AI, which Deep learning with computer vision are largely explored, to solve many problems, by replacing humans with a computer. The complex problem of analyzing ergonomics of workers can be broken into two parts: one continuous posture analysis in the surveillance video which is used for monitoring with the help of SVM or CNN (used in PoseNet) and other analyzing the risks with the help of classifier that classifies based on the NIOSH equation. The sequence flow is shown in the Figure 3.

![](img/a35f8e852e0ee65e528c95ad0821783b_324_0.png)

![](img/a35f8e852e0ee65e528c95ad0821783b_324_1.png)

![](img/a35f8e852e0ee65e528c95ad0821783b_324_2.png)

![](img/a35f8e852e0ee65e528c95ad0821783b_324_3.png)

Figure 3. Overview of steps involved in industrial ergonomics safety analysis.

# 5 CONCLUSION

Industrial worker's health is extremely crucial from both the industry as well as the worker's perspectives. Companies take preventive measures to ensure ergonomics of employees by providing effective training for them to adapt to their job profiles. Even then, there can be situations where the employees consciously or subconsciously follow improper ergonomics which can jeopardize their health in the long run. This article provides a review of research and work carried out on how to automate the monitoring of worker health and ergonomics. Finally, the paper has highlighted the method of approach for early detection of improper ergonomics of workers.
