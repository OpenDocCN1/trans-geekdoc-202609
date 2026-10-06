# 94 k-Nearest Neighbors — Getting Started

try to identify the ten digits (0 - 9) from handwriting. This is also known as OCR (Optical Character Recognition).

# 4.10 ◎ Project: Recognize Handwritten Numbers

In this section, you will develop a machine learning model based on k-Nearest Neighbors for a real-world application. The goal is to recognize handwritten digits from images. You will use the MNIST dataset, a standard dataset for image recognition. The MNIST dataset is publicly available and contains 60,000 images for training and 10,000 images for testing purposes. LeCun et al. (2005) developed the MNIST dataset based on two datasets from handwritten workers and high school students.

![](bbox=[0.135, 0.381, 0.726, 0.655])

FIGURE 4.9 First Six Handwritten Numbers of the MNIST dataset

Figure 4.9 shows a printout of the first six images from the MNIST dataset, giving you an idea of how the census workers and high school students wrote the numbers.

Rather than using the complete MNIST dataset, in this project, we will use only a subset (the first 500 images/rows of the original MNIST dataset) to speed up the training time. In the digital resources section (see Section 4.12) of this chapter, you will find links for sample images of 500, 1,000, and 10,000, as well as the link to the original dataset. This allows you to modify the code below to use more observations.