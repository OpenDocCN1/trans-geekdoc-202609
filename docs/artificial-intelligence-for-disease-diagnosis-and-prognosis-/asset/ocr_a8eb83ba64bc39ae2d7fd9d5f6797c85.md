easily split our target images from other parts and we can easily remove extra parts of images [36]. Example: Affected skin can be isolated easily by image segmentation. There are two types of image segmentation techniques: Region-Based Segmentation and Edge Detection Segmentation.

Feature Extraction Feature extraction is a part of the dimensionality reduction process [37]. Features describe an image's actions, indicating its position in terms of space taken up, classification performance, and, of course, time consumption.

Classifier The classifier can be any algorithm that can categorize a set of data into classes. The classification algorithm is an assumption as well as separable method for assigning class labels for particular data points [38]. There are many types of classifiers in deep learning like MobileNet, DensNet121, ResNet101, VGG16, Xception, etc.

# 13.2.5.7 Alert Texts

Alerts seem to be a straightforward, one-button format that works well for brief, insightful messages. When the classifier detects a patient's final result, this portion will send an alert message to the patient's phone via wifi module, informing him that his result is ready, along with a random code that was produced and transmitted to the application before encrypting the patient's face image for security purposes.

![](bbox=[0.115, 0.5, 0.885, 0.72])

Figure 13.5 Representation of where encryption and decryption are done.

Figure 13.5 interprets the SMS alerts when a patient receives after undergoing a certain operation. This file will be decrypted after receiving the combined files of facial images and randomly generated code. After decryption, the model will generate a result, and then the alarm message will be transmitted to the patient via cloud computing.