

## 基于中性模糊和 K-Means 聚类的手写图像增强

Jaspreet Kaur\(^1\), Divya Gupta\(^1*\), Simarjeet Kaur\(^2\) and Amrinder Singh\(^3\)

\(^1\)Department of Computer Science and Engineering, Chandigarh University, Mohali, India
\(^2\)Chitkara University Institute of Engineering and Technology, Chitkara University, Punjab, India
\(^3\)Department of History, Chandigarh University, Mohali, India

### Abstract

图像处理是通过对图像应用不同操作来改进图像或从中提取有用信息的过程。在本章中，我们解决了随着时间推移而与手写文档相关的问题。手写文档可能因多种原因而劣化，包括原始文档的质量、所用的墨水或纸张以及文档的年龄。结果，文本可能变得模糊不清、模糊或褪色，使其难以阅读和理解。由于边界和对比度差，旧手稿的识别与识别从低分辨率图像中非常困难。该领域的研究工作涉及识别旧手稿的内容。今天生产的许多文件，如个人信件、图片、协议、报纸和医疗记录，未来对某些人来说将作为宝贵的历史文件。而且，其中大部分未来将会消失，因为许多文件通常由有缺陷的材料制成，这些材料会随时间消失、撕裂或损坏，或者即使以数字格式存储，也会随时间丢失。保护古代手稿免受劣化是图书馆的主要工作之一。在本章中，我们尝试使用各种分割和聚类技术来增强因时间流逝而退化的手写文档。对于文物加固，采用中性模糊集体方法来提高文档的可读性。本章对修复背景受损的古代手稿的技术进行了详尽分析。发现了三种不同的增强技术，包括：
- local threshold image enhancement
- k-means clustering
- combination of neutrosophic set (NS) and fuzzy type-1 image enhancement

Images used for enhancement can be any scanned image or camera-captured images. This work employs image segmentation methods for separating foreground and background and clustering techniques for enhancing the quality of image.

**Keywords:** Image processing, image enhancement, damaged background, thresholding method, fuzzy logic and neutrosophic set, k-means clustering

## 17.1 Introduction

Image processing involves analyzing and manipulating digital images using mathematical algorithms and computer software. The image processing process usually includes several stages like image acquisition, processing, segmentation, enhancement, image compression, image visualization analysis and interpretation (refer to Figure 17.1). In this work, we use segmentation and clustering techniques to enhance old manuscripts that has been damaged with the passage of time.

Old photos and documents are important for preserving our history, culture or important events. Many documents created today, such as personal letters, photographs, contracts, newspapers, and medical records, are somehow considered historical documents. However, weak paper will usually disappear in the future due to adhesive swelling, noise, subsequent damage due to differences in size, storage, and other products. Protection of historical data is very important [9]. This is very beneficial not only for property but also for the status of the world.

To ensure that these data are still accessible, they can be used as a reference in making further findings about the world and, most importantly, in the making of films necessary to ensure peace, equality and freedom everywhere. The primary purpose of data collection is for human research [5]. Imaging has an important role in developing this information. Basic steps in imaging involved are:

### 17.1.1 Image Acquisition

Image acquisition is the process of capturing digital images from an image sensor or other device. This can be done using a variety of imaging equipment such as cameras, scanners and microscopes. In digital cameras, images are captured by an image sensor and stored in a digital file. For scanners, images are captured by a detection device, such as contact image sensor (CIS) or charge-coupled device (CCD) and stored in digital data format [12].

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_297_0.png)

Figure 17.1 Basic image processing stages.

### 17.1.2 Image Segmentation

In this step, we divide the image into regions or segments based on certain parameters like color, texture, and brightness. The most commonly used segmentation methods are thresholding, edge detection, and growing region. Image segmentation is the first step in image analysis. To segment images for medical purposes without losing information, it is sometimes a difficult task to remove image noise before segmentation, in order to avoid incorrect contour selection. Scientists and researchers have developed many image segmentation techniques, some of the most important and widely used image segmentation techniques are:

### Threshold-Based Image Segmentation

Thresholding is a method of separating the foreground and background of an image based on grayscale data.

### Region-Based Image Segmentation

Segmentation based on regional distribution is simple as compared to other methods. It separates the image into different regions according to predetermined criteria (such as color, texture, or object). Region-based segmentation methods categorized into three broad categories that are the growing region, the dividing region, and the merging region [18].

### 17.1.3 Image Filtering

Image filtering involves applying a mathematical operation to an image pixel-by-pixel in order to remove noise or extract important features. Common types of filters include Gaussian filters, median filters, and Sobel filters. These filters can be used for tasks such as smoothing an image, sharpening edges, or detecting edges and gradients.

### 17.1.4 Image Enhancement

On the other hand, enhancement involves modifying an image to improve its overall appearance or make it more suitable for a specific application. It can be used to improve the quality of images, enhance the contrast and brightness, make color corrections, remove noise, and reduce artifacts. It can also be used to sharpen images and make them look more natural. Enhancement techniques can be applied to adjust brightness, contrast, color balance, and other image properties [25].

### 17.1.5 Clustering

The segmented regions are then grouped according to the similarity of the features. K-means, hierarchical clustering, and rate-based clustering are the most often used clustering algorithms.

### 17.1.6 Image Restoration

Image restoration refers to the removal or reduction of image degradation. Image enhancement is different from image enhancement. Image enhancement is more image dependent, while restoration usually depends only on the dataset class or character of the data.

### 17.1.7 Data Compression for Image

Image data compression strategies aim to lower the amount of bits needed to store or transmit images while minimizing data loss.

### 17.1.8 Color Image Processing

Color image processing is an important field as the use of digital images on the Internet increases.

## 17.2 Application of Image Processing

Image processing is the manipulation of digital images using various algorithms and techniques to create new images or enhance existing ones. It is an important field of computer science and has applications in many fields, such as medicine, robotics, robotics, and defense.

### 17.2.1 In Healthcare

Image processing is used to diagnose diseases, detect abnormalities, and monitor treatment progress. For example, doctors may use computed tomography (CT) or magnetic resonance imaging (MRI) to diagnose and treat various medical conditions [19]. Techniques for image processing can be used to identify healthy and diseased tissue and find bodily anomalies. This allows doctors to make more accurate diagnoses and provide more effective treatment.

### 17.2.2 In Robotics

Image processing is used to detect objects and obstacles in the environment. Using image processing algorithms, robots can identify and classify objects, determine their size, shape, color and texture, and detect changes in their environment. This helps the robots to navigate and avoid obstacles independently.

### 17.2.3 In Defence

Image processing is used to detect and track targets such as aircraft, ships and vehicles. It can also be used to identify objects and people in surveillance images and to detect suspicious activity. Image processing can be used to detect and classify weapons, explosives and other dangerous objects. Image processing can also be used in other fields such as astronomy, agriculture, manufacturing, and entertainment. For example, astronomers use image processing to detect and analyze distant galaxies and stars [21].

### 17.2.4 In Agriculture

Image processing is used to detect crop diseases and pests and to identify specific plants. With image processing, farmers can quickly spot unhealthy or infected crops and take

