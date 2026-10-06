194 Machine Learning for Neurodegenerative Disorders

![](bbox=[0.151, 0.085, 0.84, 0.345])

**FIGURE 9.3** (a) Example of a noisy image. (b) Example after denoised by AD filter.

# 9.3.2 AI-BASED SEGMENTATION OF THE MRI BRAIN SLICE

In order help AI mimic learning processes and progressively increase its degree of precision, ML, a subfield of computational science and artificial intelligence (AI), focuses on leveraging data along algorithms [27]. Image segmentation technique is implemented to analyze the image and partition it into multiple regions based on the characteristics of the image pixels. The division of an image into several pieces is called image segmentation in computer vision. Changing an image's representation into something more pertinent and comprehensible is the aim of image segmentation. Location and boundary construction are its usual purposes.

Because many areas of an image might not contain any relevant information, processing a full image is not an ideal choice. As such, we can process the image by segmenting it so that only the major portions are used. A collection of predominated slices is all that makes up an image. Pixels with comparable characteristics are clustered together in image segmentation. Through the pixel-by-pixel boundaries for every element in a picture, image segmentation provides us with a more detailed and thorough understanding of the object – ROI.

As a consequence, the ROI along with its attributes can be extracted and studied for quantitative purpose. The KM clustering algorithm is implemented for a primary level of image segmentation [28] which acts as a powerful tool in clustering the image and a secondary segmentation by GT algorithm detailing the ROI's features, which in this case is the tumor in the MRI image.

# 9.3.2.1 Primary Segmentation by KM Clustering Algorithm

An unsupervised AI approach allows KM clustering to divide the data set without differing categories. The process of training an algorithm to work on data without labels, unclassified information, without oversight is known as ML. The machine's task in this scenario is to arrange unordered data based on comparisons, trends, and variances without any prior training. In order to make the data points within each group similar to one another and distinct from the data points in the other groups, clustering aims to divide the population or set of data points into many groups. In essence, it is a classification of objects according to how similar or dissimilar they are to one another.

In order to make the data points within each group more similar to one another and distinct from the data points within the other groups, clustering aims to divide the population or set of data points into many groups. In essence, it is a classification of objects according to how similar or dissimilar they are to one another.