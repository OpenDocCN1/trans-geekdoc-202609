+   1) Thresholding: Thresholding is a process of dividing an image based on pixel intensity values. Pixels with intensities above or below a selected threshold are allocated to distinct segments based on the threshold value.
+   
+   2) Region growing: This bottom-up method divides pixels into segments based on similarity standards. If nearby pixels satisfy certain similarity requirements, they are iteratively added to the segment starting from the seed points.
+   
+   3) Clustering: Algorithms for image segmentation, such as K-means or Gaussian mixture models (GMMs), group pixels based on the similarity of features, including color or texture. Each cluster represents a portion of the image.
+   
+   4) Edge detection: Techniques for edge-based segmentation, such as the Canny edge detector and Sobel operator, aim to identify abrupt changes in gradient magnitude or intensity to identify object boundaries.
+   
+   5) Contour-based segmentation: This method uses the edges or contours of an image to determine object boundaries, dividing the images into regions based on these outlines.
+   
+   6) Deep learning methods: Deep learning has revolutionized the image segmentation industry by directly learning hierarchical representations from data. Convolutional neural networks (CNNs) are commonly used for semantic and instance segmentation tasks, with architectures such as U-Net, fully convolutional networks (FCNs), and DeepLab being frequently employed (Khan et al. 2020).

Image segmentation has numerous applications across various domains, including medical imaging for organ delineation, tumor identification, and illness diagnosis; autonomous driving for video feed recognition of items such as cars, people, and road markings; and object detection and recognition systems for identifying and locating objects within pictures or videos (Ma et al. 2024). Additionally, satellite imagery segmentation is utilized in remote sensing applications for the classification of land cover and land use, precision-agriculture, disaster response and management, monitoring of infrastructure and water resources, urban planning, and climate change. Facial recognition systems also use segmentation to identify and locate facial characteristics such as the mouth, nose, and eyes. Despite advances in image segmentation, complex scenes with overlapping or occluded objects, or with ambiguous object borders, remain a challenge. Future research directions include developing segmentation methods that can effectively handle such complex scenes.

The commonly used medical imaging techniques are computed tomography (CT), positron emission tomography (PET), and magnetic resonance imaging (MRI).