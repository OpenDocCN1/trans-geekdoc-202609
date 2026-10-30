# I2.2.1 Low-level image processing techniques

The first proposed approaches to countermeasure CMF were based on low-level image features. This subsection overviews some of the most popular techniques belonging to this category.

In 2003, Fridrich [11] proposed a block-based approach dividing the image into overlapping blocks. The latter undergo discrete cosine transformation (DCT) to be used as descriptors. Each block is then characterized by features that are then lexicographically arranged. Similarities between blocks are computed by comparing their description.

Another study by Zhao et al. [12] relies on overlapping blocks analysis. In particular, 2D-DCT is applied to the image blocks; the DCT coefficients are then quantized. Each block is divided into non-overlapping sub-blocks upon which SVD (Singular Value Decomposition) is applied. Last, the largest singular value out of each block is extracted to reduce the size of each block description.

Besides the previously mentioned methods, Lynch’s approach [13] runs direct block comparisons rather than using block features. The first step has a given image divided into N small overlapping blocks with a sliding block approach. A dominant feature is computed for each block to avoid the bottleneck of way too many blocks to be compared.

The scientific literature counts several methods for CMFD that rely on local keypoint descriptors, such as SIFT, SURF, and BRISK [14].

Zhu et al. [15] presented a technique by introducing a Gaussian scale space, extracting the FAST keypoints and the ORB features in each scale space. The orientated FAST coordinates are projected onto the original image for a match analysis of the ORB features between every two different keypoints. Further refinement involves removing the false-matched keypoints with the RANSAC (Random Sample Consensus) algorithm [16].

By pairing SIFT descriptors with SVD (Single Value Decomposition), Chihauoi et al. [17] delved into the attempt to improve a SIFT-based copy-move detection by reducing the dimensionality of the corresponding descriptor.

Yeaps et al.’s approach [18] stands along the lines of SIFT-based methods. The authors tested the robustness of rotated BRIEF descriptors plus oriented FAST. Two Nearest Neighbor with Hierarchical Agglomerative Clustering were adopted for feature matching.

In a study by Wang et al. [19], the authors proposed a method using local keypoints and the SURF descriptor. A given image is segmented into non-overlapping and nearly uniform superpixel blocks. Local keypoints are extracted from each superpixel and are characterized with the superpixel contents and color invariance SIFER. Connected Delaunay triangles are drawn using the extracted image keypoints. Local image feature for each Delaunay triangle is computed by using FQRHFMs and gradient entropy.