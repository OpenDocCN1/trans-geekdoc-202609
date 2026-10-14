![](bbox=[0.14, 0.12, 0.44, 0.31])

![](bbox=[0.5, 0.12, 0.8, 0.31])

Figure 7.5 Experimental results of temporal scalability: (a) Base layer and (b) enhancement layer.

Spatial scalability: In all types of video sequences and an arbitrary QP difference between the reference layer and enhancement layer, the image of spatial scalability always leaks the visual content. The larger the QP difference is, the more content for video sequences are exposed.

+   - Quality Scalability: Similar to the spatial scalability, the quality scalability is affected by the QP difference. In addition to that, other factors also lead to the exposure.
+   - Coarse Grain Scalability: The image features, such as texture, shape and edge, lead to –content exposure. The richer the features are, the more data are leaked in the enhancement layers.

Medium Grain Scalability: MGS layers may consist of low frequency, middle frequency, or high frequency DCT coefficients, whose leakage are related to the image features. A richer feature image will contain more non-zero coefficients such that each MGS layer may disclose more information.

Temporal Scalability: The motion feature determines the amount of leakage from the temporal scalability layers. Obviously, more intense motions result in more leakage in the enhancement layers.

# 7.2.1.5 Conclusion

In this article, we investigate whether partial encryption in H.264/SVC can protect data confidentiality. The experiments show that the unencrypted enhancement layers leak significant context information about the video stream, from all three scalability dimensions. We also analyzed the coding techniques for spatial, quality and temporal scalabilities, and showed that the coding techniques in use determined that those enhancement layers have to be encrypted for the confidentiality purpose, although partial encryption may be sufficient for access control in the sense of deterring unauthorized access to the high quality video.