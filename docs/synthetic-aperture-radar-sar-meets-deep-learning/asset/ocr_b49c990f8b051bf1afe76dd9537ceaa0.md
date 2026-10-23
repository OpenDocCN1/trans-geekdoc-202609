![](bbox=[0.24, 0.14, 0.52, 0.3])

![](bbox=[0.6, 0.14, 0.9, 0.3])

(c)

![](bbox=[0.24, 0.3, 0.52, 0.46])

![](bbox=[0.6, 0.3, 0.9, 0.46])

(d)

Figure 5. Pairs of RealSAR-RAW (left) and RealSAR-IMG (right) examples. Example pair (a) represents an empty scene, (b) scene with an aluminium bottle, (c) scene with an aluminium and a glass bottle, while (d) contains all three bottles.

# 4. Deep Learning

# 4.1. End-to-End Learning vs. Feature Engineering

In classical machine learning, we usually need to transform our raw data to make it suitable as input to our machine learning model. We extract a set of features from each raw data point using classical algorithms or hand-crafted rules. The process of choosing an appropriate set of features with corresponding procedure for their extraction is called feature engineering [44].

With the advent of deep learning, approaches with fewer preprocessing steps have become more popular. Instead of manually transforming raw data into representations appropriate for the model, new model architectures were developed that were able to consume raw data [33]. Such models would implicitly learn their own optimal representations [34] of raw data, often outperforming model which learned on fixed, manually extracted features [45]. This paradigm is also referred to as end-to-end learning.

We designed our models and experiments to compare and contrast these two paradigms. The first approach is to use an existing image classification architecture ResNet18, which has been shown to be able to tackle a diverse set of computer vision problems [46,47]. This model is trained on RGB images reconstructed from radar data using Omega-K algorithm [39]. The second is an end-to-end learning approach, where the input is raw data collected with our GBSAR-Pi. The model architecture is based on ResNet18, with a few modifications to accommodate learning from raw data.

# 4.2. Multi-Task Learning and Multi-Label Classification

Our task consists of detecting the presence of multiple different objects in a scene. Instead of training a separate model for recognizing each individual object, we adopt the multi-task learning paradigm [48] and train only one model which recognizes all objects at once. The model consists of a single convolutional backbone which learns shared feature representations [49] that are then fed to multiple independent fully-connected binary