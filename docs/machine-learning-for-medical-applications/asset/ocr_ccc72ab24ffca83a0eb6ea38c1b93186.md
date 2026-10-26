lems means enhancing the annotation procedures, applying semisupervised techniques and using data augmentation techniques to generate a more balanced training dataset.

# 6 Transformer-based architectures for image segmentation

# 6.1 Introduction to ViTs

The introduction of Vision Transformers (ViTs) marks a significant paradigm shift in the field of image segmentation and computer vision. Originating from natural language processing, transformers have demonstrated exceptional performance in handling sequential data, largely due to the effectiveness of self-attention mechanisms. ViTs adapt this architecture by dividing images into patches, allowing them to model long-range dependencies and complex spatial relationships. As shown in Figure 8, this patch-based attention mechanism enables ViTs to capture global context more effectively than traditional CNNs, which are often limited by their local receptive fields. This advancement opens up new possibilities for overcoming key limitations in conventional segmentation models.

# 6.1.1 Architecture and mechanism

Perspective: The fundamental concept behind transformers is the division of a picture into fixed-size patches, which are subsequently linearly embedded into vectors. Similar to the layers in text processing transformers, these vectors are processed by several layers of feed-forward and self-attention networks. The model can effectively capture long-range relationships and contextual information over the whole image, thanks to the self-attention mechanism, which also allows the model to assess the value of individual patches in relation to one another. In contrast, CNNs usually use pooling layers and convolutional processes to concentrate on local features.

# 6.1.2 Advantages over convolutional networks

One of the key advantages of ViTs is their ability to capture global relationships within an image, which is often challenging for traditional CNNs that primarily focus on local feature extraction. By leveraging self-attention, ViTs can integrate information from all parts of an image, leading to improved performance in tasks requiring a holistic understanding of spatial relationships. This capability is particularly beneficial for complex segmentation tasks where global context is crucial for accurate predictions.