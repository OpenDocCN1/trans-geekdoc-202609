![](bbox=[0.21, 0.1, 0.82, 0.19])

FIGURE 5.15 The reconstruction result of the encoder and decoder with (right) and without (middle) the reconstruction branch during the training stage. Obviously, involving the reconstruction branch helps guarantee no style information to be absorbed in the encoder and decoder part and almost perfect reconstruction. The figures are by courtesy of Chen et al. (2017b).

![](bbox=[0.2, 0.28, 0.8, 0.35])

FIGURE 5.16 The disentanglement enables fast incremental learning for new styles. For each case, the left and right are the stylization results of incremental training and fresh training respectively. The figures are by courtesy of Chen et al. (2017b).

![](bbox=[0.19, 0.45, 0.83, 0.52])

FIGURE 5.17 Stylization results by linear combination of two style filter banks. By adopting different fusing weights, we change the proportion of each style accordingly. The figures are by courtesy of Chen et al. (2017b).

obtain comparable stylization results to those from fresh training, which retrains the whole network with the new styles.

The second advantage is enabling style fusion in two different ways: linear fusion and region-specific fusion. For linear fusion, since different styles are encoded into different filter banks {K_i^1, ..., K_i^m}, we can linearly fuse multiple styles by linearly fusing filter banks in the StyleBank layer. Then the fused filter bank is used to convolve with the content feature F:

F̃ = (∑_{i=1}^m w_i * K_i) ⊗ F   ∑_{i=1}^m w_i = 1,   (5.12)

where m is the number of styles, K_i is the filter bank of style i. F̃ is then fed to the decoder to get the final stylization result. Fig. 5.17 shows such linear fusion results of two different styles with variant fusion weight w_i.

For region-specific style fusion, suppose that the image is decomposed into n disjoint regions in the feature space, and M_i denotes every region mask, then the feature maps can be