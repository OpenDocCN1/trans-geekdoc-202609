
This exploration has familiarized you with the fundamental concepts and provided you with the practical skills necessary to manipulate data, construct models, and harness the power of automatic differentiation. The journey through optimizing model parameters and the nuances of saving and loading models equips you with a comprehensive toolkit to tackle real-world problems.

As you move forward, let the principles and practices discussed serve as building blocks for more complex applications. PyTorch's dynamic nature encourages experimentation and innovation, inviting you to explore the vast possibilities of neural network architectures and applications.

Remember, the field of ML is ever-evolving, and continuous learning is vital. Keep experimenting, stay curious, and leverage the vibrant PyTorch community and resources to further your knowledge and skills.

In the next chapter, we will understand more about classification through multi object detection use cases.

**Join our book’s Discord space**

Join the book’s Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/Discord.png)

# Chapter 3

## Multi-object Detection

### Introduction

This chapter introduces the user to dealing with image data, segmenting images, transforming images, and building deep learning models to detect multiple objects in an image dataset. Computer vision has changed greatly, thanks to deep learning, especially in spotting objects in images. Among different ways to spot objects, one method called classification-based multi-object detection is really good at not just figuring out what is in a picture but also saying exactly where it is. In this chapter, we will talk about this method.

It uses convolutional neural networks (CNNs) to do two jobs at once: Figuring out what an object is and where it is located in the image. By teaching these networks to recognize different types of objects and guess where they are, we get a powerful way to find stuff in pictures. PyTorch is a great tool because it is easy to use and has many helpful features.

### Structure

In this chapter, we will go through the following topics:

• Problem statement

• Algorithm selection

• Solution architecture

• Deep dive into YOLO

• Data loading and processing

• Downloading dataset for only a few classes

• Data preprocessing

• Model training

• Model testing and evaluation

### Objectives

In this chapter, we will discuss the basics of classification-based multi-object detection. We will first understand details about object detection, the difference between image classification and object detection, and use cases of object detection. We will then understand the algorithms used for object detection, popular datasets, and solution architecture for model training and evaluation.

We will also give you some tips on building and training these models using PyTorch. By the end, you will know a lot about finding multiple objects in images and be ready to use this knowledge in your projects.

Let us first understand about computer vision. Computer vision focuses on enabling computers to extract meaningful information from images and videos to interpret visual data. It involves the development of algorithms and machine learning (ML) models to replicate human vision capabilities to process, analyze, and make decisions on visual data.

### Problem statement

Given an image containing multiple objects of interest, the task is to develop a deep learning model capable of accurately detecting and localizing these objects within the image. This involves identifying the types of objects present and precisely outlining their bounding boxes to indicate their locations. The challenge lies in handling various object classes, varying sizes, occlusions, and cluttered backgrounds commonly encountered in real-world images. The objective is to devise a robust and efficient solution for multi-object detection that can be applied across diverse domains such as autonomous driving, surveillance, medical imaging, and more.

#### Object detection

Object detection is a computer vision task that identifies and locates objects of interest within an image or video. The goal is to recognize what objects are present in the visual data and provide information about where they are located in the image. Object detection is a fundamental problem in computer vision and has numerous real-world applications.

The image below showcases a bustling city street with pedestrians, vehicles, traffic lights, and signage:

![](images/Figure_3.1.png)

When we talk about how computers understand pictures, they use different parts to make sense of what they see. Imagine a computer looking at a photo of a city street. Here is a simple breakdown of what it does:

• Street scene: The background typically depicts a street or road, representing the context in which objects are detected.

• Bounding boxes: Bounding boxes are drawn around individual objects within the scene. Each box is rectangular and contains an object of interest. The object detection algorithm determines the size and position of the bounding boxes.

• Objects: Objects inside the bounding boxes can include cars, pedestrians, dogs, signposts, traffic lights, and other elements in the street scene.

• Labels: To further illustrate the concept, labels are often added near or within the bounding boxes to indicate each object, e.g., car, person, or dog.

Image classification is the process of teaching a computer to recognize and categorize different types of images. For example, let us say we want to classify different types of flowers based on their images. We collect photos of daisies, dandelions, roses, sunflowers, and tulips. Then, we train a ML model to recognize flower patterns. When we give it a new flower image, it predicts the flower type (e.g., rose or tulip). This technology has practical applications in fields like medical imaging, self-driving cars, and quality control.

Object detection enables the computer to identify and locate various objects within an image or video frame. For example, let us say we want to classify different types of flowers contained within each image. We collect photos containing daisies, dandelions, roses, sunflowers, and tulips. Then, we train a ML model to recognize flower patterns. When we give it a new image, it predicts all the flower types (e.g., rose and tulip).

#### Image classification vs. object detection

Let us understand the key difference between image classification and object detection. The figures below capture a teddy bear sitting and reading a book.

The image classification will classify the image as a teddy bear and the object detection will classify image as a list containing both teddy bear and book:

![](images/Figure_3.2.png)

The following are the key terms of object detection:

• Bounding box: A rectangular region drawn around an object to specify the object's location.

• Class label: The category or class to which an object belongs.

• Object localization: The process of determining the coordinates of a bounding box that accurately encloses an object.

• Anchor boxes: Pre-defined bounding boxes of various sizes and aspect ratios are used in object detection models to predict object locations.

• Non-maximum suppression (NMS): A postprocessing technique that removes redundant bounding boxes by keeping only the one with the highest confidence score when multiple boxes overlap.

• Intersection over union (IoU): A metric that measures the overlap between two bounding boxes. It is used to evaluate the accuracy of bounding box predictions.
