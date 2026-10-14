+   - **SURF Algorithm**
+   The SURF algorithm was proposed by Bay et al. in 2006. SURF uses quick measurements of Hessian's matrix to detect features and the distribution-based descriptor to describe features. This algorithm is the developed version of SIFT in terms of speed, but is less accurate (Bay et al. 2006).
+   - **MIFT Algorithm**
+   The MIFT algorithm was proposed by Guo et al. (2009). This algorithm is similar to SIFT at the features extraction stage, but is improved at the stage of descriptors, which is constant relative to mirror reflection. This algorithm is constant against scale changes, rotation and mirror reflection and is robust against viewpoint variations.

# 26.5.2.2 Matching Techniques

The similarity of the feature points in the image can be measured using the nearest neighbor and clustering techniques; each technique of matching is described in the following.

+   - **Nearest Neighbor:** The nearest neighbor technique calculates the similarity between feature points’ distance from each keypoint relative to each other. Then the distance of the keypoints less than the predetermined threshold is matched. The nearest neighbor techniques for the keypoint-based approach are divided into four types: Best Bin First, 2NN, g2NN, and others where the g2NN method is suitable for multiple copy-move forgery detection (Amerini et al. 2011; Fan et al. 2016).
+   - **Clustering:** In clustering techniques, similar objects are placed in the same category (cluster) and different objects are placed in a different category. The Hierarchical Agglomerative Clustering (HAC) is a common example of the clustering technique in CMFD (Amerini et al. 2013).

Next section concludes both methods (block-based and keypoint-based methods) to CMFD.

# 26.5.2.3 Comparison of Methods for CMFD

Block-based methods for CMFD are suitable for cases of the compression JPEG, but is not suitable for geometric distortion (scale change, rotation, angle, affine and translation), and they have a high computational complexity (Li et al. 2014). Their computational complexity has led to a widespread use of keypoint-based methods, including the SIFT algorithm (Amerini et al. 2011; Sadeghi et al. 2017). SIFT is one of the keypoint-based methods for detecting forgery, which is constant against scale and rotation changes and is also stable against intensity, affine, and noise distortions. But this algorithm has some disadvantages: