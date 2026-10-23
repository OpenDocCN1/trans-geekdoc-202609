from and full interaction between the feature maps, such that it contains high-level semantic information with a low resolution, and low-level detail information with a high resolution.

In addition, the subsequent part of this paper makes further attempts to combine different resolutions. It can be seen in subsequent chapters that improving the resolution of the feature maps in the rough matching stage can significantly increase the number of matching point pairs. Default HRNet outputs 1/2, 1/4, 1/8 resolution feature maps. Under the constraints of the experimental environment, we chose 1/5 and 1/2 as the low and high resolutions. The reason will be discussed in Section 3. Experimental Results and Analyses. The 1/5 resolution can be obtained from other resolutions by interpolation. The 1/2 resolution feature map cascades the 1 × 1 convolutional layer and the output works as the fine-level feature map. The 1/4 and 1/8 resolution feature maps are all interpolated to 1/5 resolution. After stitching, the coarse-level feature map is obtained through the 1 × 1 convolutional layer.

# 2.4.2. Performer

The Transformer has outstanding performance in many fields of CV, such as classification and detection. With the help of a multi-head self-attention mechanism, the Transformer can capture richer characteristic information. Generally speaking, Transformer complexity is squared with sequence length. In order to improve the speed of training and inference, a linear time complexity Transformer was also proposed recently, i.e., Performer [42]. It can achieve faster self-attention through the positive Orthogonal Random features approach.

Attention (Q, K, V) = softmax( (Q Kᵀ) / √dₖ ) V  (15)

Self-attention (as shown in Figure 7) performs an attention-weighted summation of the current data and global data, and realizes a special information aggregation by calculating the importance of the current location feature relative to other location features. The feedforward part contains the linear layer and the GELU (Gaussian Error Linear Unit) activation function. Each layer adopts Layer Normalization in order to ensure the consistency of the feature distribution, and to accelerate the convergence speed of the model training.

![](bbox=[0.25, 0.65, 0.78, 0.88])

Figure 7. Performer (Transformer) encoder architecture and self-attention schematic diagram.

As is shown in reference [42], Performer can achieve space complexity O(Lr + Ld + rd) and time complexity O(Lrd), but the original Transformer’s regular attention is O(L² + Ld)