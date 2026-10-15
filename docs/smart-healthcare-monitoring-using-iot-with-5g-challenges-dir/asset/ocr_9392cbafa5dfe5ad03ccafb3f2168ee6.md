![](bbox=[0.13, 0.12, 0.84, 0.34])

FIGURE 7.3 General block diagram for COVID-19 diagnosis system using deep learning.

Deep learning–based detection can be categorized based on two different perspectives:

+   - Pre-trained model with deep learning
+   - Deep learning on custom based

Pre-trained models are those where the data are already trained in the area that is similar to the application context. Deep transfer learning involves transferring weight and bias for training and retraining purposes to a new model similar to the trained parent model. General training models require more time and high computational power. Utilizing a pre-trained model advances the facility to accelerate convergence with network generalization [47,48]. Another technique, which is the custom deep learning technique, requires no previous weight and bias; hence, it is time-consuming and requires high computational power. Due to its specific application of interest, custom deep learning models deal with feasible architecture development, which is consistent and gives more accurate performance [5].

With its advantage over custom deep learning techniques, we focus on the pre-existing CNN, ResNet, and its utilization by various researchers to classify and diagnose COVID-19. The following section elaborates on the application of ResNet using both imaging modalities.

# 7.4.1 Pre-Trained Model with Deep Learning ResNet

This section details on the application of ResNet on chest region X-ray and CT-scan images of probable COVID-19 diagnostic patients.

# 7.4.1.1 X-Ray and ResNet

Various methods based on X-ray image analysis using ResNet are presented in Table 7.1 [5], which summarizes the research findings. Almost all the algorithms have used the database COVID-19 X-ray image as the standard. Apart from COVID-19 X-ray image databases, other sources are used with multiple source