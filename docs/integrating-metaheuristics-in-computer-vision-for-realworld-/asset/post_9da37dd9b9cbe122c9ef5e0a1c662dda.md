
corrective action before the damage gets out of hand. Image processing can be used to reduce the demand for herbicides and lessens the environmental damage caused by invasive species [20].

## 17.2.5 In Manufacturing

Image processing is used to inspect products for defects and to automate assembly lines. Throughout the manufacturing process, faults in items can be found via image processing. In order to quickly and precisely identify any faults, this can be done by using cameras to take pictures of the items as they move down the production line.

## 17.2.6 In Entertainment

Image processing is used to create special effects for movies and video games.

## 17.2.7 Object Recognition

It can also be used for object recognition, motion detection, and face recognition.

## 17.3 Enhancement of Handwritten Document

The process of improving the visual quality and readability of scanned or digitized handwritten papers is referred to as the “problem of enhancing handwritten documents.” This is a crucial task in many fields, including document analysis, the preservation of historical documents, and digital archiving [26].

The quality of the original document, the kind of ink or paper used, and the document’s age are just a few of the variables that might cause handwritten papers to deteriorate. The text might therefore become obscured, hazy, or unintelligible, making it challenging to read and comprehend. Enhancement techniques can be used to improve the quality of written documents by reducing noise, sharpening edges, improving contrast, and improving the overall appearance of text. These techniques may include image processing techniques, such as filtering, thresholding, and classification, and machine learning algorithms, such as deep learning and neural networks. In previous works, most commonly used technique is thresholding [24, 28].

### 17.3.1 Local Thresholding Technique

Local thresholding is a common technique used in image processing to binarize an image by segmenting it into foreground and background regions based on local properties, such as image intensity or texture [1, 3, 4, 7]. Figure 17.2 is the resultant image of Figure 17.3. But there are number of issues with local thresholding when improving handwritten documents these are as follows:

- **Artifact and noise sensitivity:** Due to the sensitivity of local thresholding to noise and other image artefacts, the threshold values may differ dramatically between various regions of the image, producing inconsistent binarization results.

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_301_0.png)

Figure 17.2 Resultant image of local thresholding.

- **The difficulty of choosing the window size** Selecting an adequate window size can be challenging, and doing so has a significant impact on how well local thresholding works. Selecting a window that is too small may cause important details to be lost, while choosing a window that is too large may result in the loss of small details or centering large areas.
- **Complexity of computing** Local thresholding may require a significant amount of processing, particularly for large images and tiny window widths. This makes it problematic for real-time or high-throughput applications because it can lead to large processing times.
- **Difficulty dealing with different lighting conditions** Area measurement assumes that lighting conditions are uniform throughout the image. However, if the image contains different lighting sources, local scaling can cause uneven binarization.
- **Limited applicability to non-uniform backgrounds** In situations when the background of the handwritten document is non-uniform or contains notable texture or color variations, local thresholding may not be effective. To get the best outcomes in these situations, global thresholding or more complicated methods could be necessary. To overcome the disadvantages associated with the local Thresholding process, various clustering and segmentation techniques are used to increase the readability of the collected data.

## 17.4 Clustering Techniques

### 17.4.1 K-Means Clustering Technique

K-means clustering can be used for image enhancement by segmenting the image into distinct regions of interest and applying appropriate filters to each region. This allows you to sharpen the image and improve the colors. This can also be used to reduce noise in the image and to reduce the amount of compression needed to compress the image [9, 22, 23] while applying enhancement to Figure 17.3, the resultant image of k-means clustering has been presented in Figure 17.4.

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_302_0.png)

Figure 17.3 Initial damaged image.

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_302_1.png)

Figure 17.4 Resultant image of K-Means.

### 17.4.2 Combination of Neutrosophic and Fuzzy Type 1 Technique

We used neutrosophic set (NS) [6] to distinct foreground and background and yield of neutrosophic set act input for fuzzy type-1 and after fuzzy type we have a better-quality image [2, 27]. The first step for neutrosophic set is to pre-process the image by applying contrast enhancement and noise reduction techniques to improve the visibility of edges and features.

The next step is to extract the features from the pre-processed image. This can be done by applying various edge detection algorithms, such as Canny edge detection algorithm (refer Figure 17.6). After extracting the features, the next step is to cluster them into the foreground and background fuzzy objects. This can be accomplished by using a variety of clustering techniques, including fuzzy c-means clustering and k-means clustering, etc. The final step is to separate the foreground and background objects. This can be done by applying various segmentation techniques, such as region-based segmentation [8]. Figure 17.5 is the resultant image after applying neutrosophic set.

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_302_2.png)

Figure 17.5 Resultant image of neutrosophic set.

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_303_0.png)

Figure 17.6 Resultant image of fuzzy type 1.

After this output, neutrosophic act as input to fuzzy type. Fuzzy type 1 enhances an image by increasing the contrast between colors and sharpening the edges of objects in the image. It can also reduce noise, making the image look clearer and more detailed. Figure 17.6 is the resultant image after applying fuzzy type 1.

## 17.5 Performance Parameters

Image enhancement is the process of modifying digital images to make them more aesthetically pleasing or to improve their accuracy for analysis. In this study, we compared the effectiveness of two segmentation algorithms using various factors. The following parameters were used: Peak Signal to Noise Ratio (PSNR), Mean Square Error (MSE), Root Mean Square Error (RMSE), Normalized Coefficient (NC), and Distance Reciprocal Distortion Metric (DRD) [11].

### 17.5.1 Mean Square Error

Mean square error (MSE) is a common metric used to estimate the quality of an image enhancement algorithm. It measures the average of the squared differences between the original image and the enhanced image. The formula for calculating MSE for image enhancement is as follows:

```
MSE = \left(\frac{1}{N * M}\right) * \Sigma [I(x, y) - E(x, y)]^2
```

where I(x,y) is the pixel value of the original image at location (x,y), E(x,y) is the pixel value of the enhanced image at the same location, and N and M are the height and width of the image, respectively. To calculate MSE for image enhancement, you would first need to obtain the original image and the enhanced image. Then, for each pixel in both images, you would calculate the difference between the original and enhanced pixel values, square this difference, and sum up all these squared differences across all pixels in the image. Finally, you would divide this sum by the total number of pixels in the image (N*M) to obtain the MSE. A lower MSE value indicates a better quality enhancement, as it means that the enhanced image is closer to the original image. However, MSE alone may not always be
