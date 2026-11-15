We will get into the details of the topics mentioned here:

+   • What self-driving cars are
+   • How deep learning is applied in self-driving cars
+   • How deep learning becomes a state-of-the-art solution for object recognition in intelligent vehicles
+   • Exploratory analysis on the German Traffic Sign Recognition Benchmark dataset's data
+   • Traffic sign recognition using convolutional neural networks with the MXNet package
+   • Keras and TensorFlow
+   • Traffic sign recognition using convolutional neural networks with the `keras` package
+   • Reducing overfitting with dropout
+   • Data augmentation and common augmentation methods
+   • Using data augmentation for a small training set
+   • Summarizing approaches to prevent overfitting in CNN models

# How is deep learning applied in self-driving cars?

A self-driving car (also called an autonomous/automated vehicle or driverless car) is a robotic vehicle that is capable of traveling between destinations and navigating without human intervention. To enable autonomy, self-driving cars detect and interpret environments using a variety of techniques such as radar, GPS and computer vision; and they then plan appropriate navigational paths to the desired destination.

In more detail, the following is how self-driving cars work in general:

+   • The software plans the routes based on the destination, traffic, and road information and starts the car
+   • A **Light Detection and Ranging (LiDAR)** sensor captures the surroundings in real time and creates a dynamic 3D map
+   • Sensors monitor lateral movement to calculate the car's position on the 3D map