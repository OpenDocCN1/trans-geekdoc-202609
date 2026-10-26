# #### 4.5.4 Scalability and multiresolution processing

One of the major difficulties of DeepLab models lies in their scalability to very high-resolution images and 3D volumetric ones. The necessity of large amounts of memory and calculation to process images that have large dimensions of data makes the model barely feasible in some cases. There was less prior work proposed in this category, including solutions for expanding the model scalability, for instance, hierarchical processing of efficient multi-resolution approaches that further expand these applications across multiple domains.

Performance of DeepLab models depends on the caliber and volume of training data available to the systems. The fact is that segmentation outcomes that are not perfect stem from insufficient data. The models also fail to handle class imbalance, a situation whereby some classes are deprived in the training set. Solving such problems requires coming up with solutions of raising the quality of annotations and methods of using unsupervised learning, as well as using data augmentation when training the models.

# ## 5 Mask R-CNN and the rise of instance segmentation

# ### 5.1 Introduction to mask R-CNN

Mask R-CNN can be seen as the model that takes instance segmentation to the next level and is based on the basics that was introduced by faster R-CNN. Built to take object detection to the next level by adding pixel segmentation, mask R-CNN offers a new idea that effectively identifies an object and even outlines it. This architecture improves on the lack of instance-level information that commonly comes with object detections, which gives only bounding boxes and class labels, by including a segmentation branch to output precise masks for each detected instance.

# #### 5.1.1 Architecture and major building blocks

The foundation of mask R-CNN is the particularity of this approach, where object detection and instance segmentation are performed at the same time. To realize the candidate of object regions, the model uses region proposal network (RPN); for accurate positioning of regions, the model uses RoIAlign layer. The architecture includes three primary components: a backbone network for feature extraction, an RPN for generating region proposals, and a fully connected network that predicts class labels, bounding boxes, and segmentation masks. The addition of the segmentation mask branch