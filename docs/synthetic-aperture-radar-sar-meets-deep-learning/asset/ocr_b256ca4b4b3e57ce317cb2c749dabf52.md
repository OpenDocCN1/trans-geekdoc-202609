- The existing SAR image registration methods mainly rely on the CNN structure, and lack a complete relative relationship between their features due to the receptive field’s limitations.

![](bbox=[0.25, 0.24, 0.85, 0.35])

Figure 1. Remote sensing image registration milestones in the last two decades.

Based on the above analysis, this paper proposes a wide-swath SAR image fine-level registration framework that combines traditional methods and deep learning. The experimental results show that, compared with the state of the art, the proposed method can obtain better matching results. Under the comparison and analysis of the matching performance in different data sources, the method in this paper is more effective and robust for SAR image registration.

The general innovations of this paper are as follows:

+   1. A CNN and Transformer hybrid approach is proposed in order to accurately register SAR images through a coarse-to-fine form.
+   2. A stable partition framework from the full image to sub-images is constructed; in this method, the regions of interest are selected in pairs.

The remainder of this paper is organized as follows. In Section 2. Methods, the proposed framework of SAR image registration and the learning-based sub-image matching method are discussed in detail. In Section 3. Experimental Results and Analyses, specified experiments, as well as quantitative and qualitative results, are given. In Section 4. Discussion, the conclusion is provided.

# 2. Methods

In this study, we propose a phased SAR image registration framework that combines traditional and deep learning methods. The framework is illustrated in Figure 2; the proposed method mainly consists of four steps. First, the ORB [25] and GMS [26] are used to obtain the coarse registration result via the downsampled original image. Second, K-means++ [27] select cluster centers of registration points from the previous step, and a series of corresponding original-resolution image slices are obtained. Third, we register the above image pairs through deep learning. The fourth step is to integrate the point pair subsets and obtain the final global transformation result after RANSAC [28].

As a starting point for our work, we first introduce the existing deep learning mainstream.

# 2.1. Deep Learning-Related Background

As AlexNet [29] won first place in 2012 ImageNet, deep learning had begun to play a leading role in CV, NLP (natural language processing), and other fields. The current mainstream of deep learning includes two categories: CNN and Transformer. CNN does well in the extraction of local information from two-dimensional data, such as images. Because the deep neural network can extract key features from massive data, deep CNN is performed outstandingly in image classification [30], detection [16,31], and segmentation [32].