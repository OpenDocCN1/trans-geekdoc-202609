Patch-based approaches gained popularity initially due to their straightforward implementation and computational feasibility, especially when hardware resources were limited.

# 2.5.1 Challenges in patch-based segmentation

Due to their simplicity, patch-based CNNs face several challenges. One significant limitation is the lack of context captured by individual patches. Since patches are processed independently, the model struggles to maintain coherence across neighboring regions, leading to inconsistencies in the segmentation results. The fixed-size patches can lead to issues when encountering objects that span multiple patches. This problem necessitates careful handling of patch boundaries and often requires post-processing steps to merge the outputs from adjacent patches seamlessly.

# 2.5.2 Advantages of patch-based approaches

Patch-based CNNs were used initially because they have a lot of advantages. A significant benefit was a relative requirement of lesser computation as compared to the full-image methods. A characteristic of patch-based CNNs was that they can save on memory and computational power because they operate from square one at smaller fields than the complete image; this makes such networks ideal for systems with restricted memory and power. In addition, the patch-based approach allows to simultaneously apply data augmentation techniques such as flipping and cropping that can enhance the model generalization and its ability to be less sensitive to data variations. Patch-based CNNs were reasonable to use for the first attempts at picture segmentation because of these characteristics.

# 2.5.3 Comparisons with fully convolutional networks

Compared to FCNs, patch-based CNNs exhibit both strengths and weaknesses. FCNs, by processing the entire image in one pass, can leverage global context and produce more coherent segmentation maps. In contrast, patch-based approaches struggle with integrating information across the entire image, potentially leading to less accurate segmentations. Patch-based CNNs are often simpler to implement and can be effective for specific applications where local context was sufficient. The comparison highlights the trade-offs between processing efficiency and segmentation quality, paving the way for hybrid approaches that combine elements of both methods.