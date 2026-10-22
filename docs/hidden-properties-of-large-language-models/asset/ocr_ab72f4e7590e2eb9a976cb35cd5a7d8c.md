![](bbox=[0.12, 0.07, 0.88, 0.27])

Figure 4.13: Massive activations are present in ViT-L from CLIP and DINOv2, but not MAE.

sequence dimensions. In these two models, there are extremely few activations (fewer than four) with significantly larger magnitudes than others. In addition, these activations are located in specific feature dimensions and appear in random patch tokens. However, we do not observe massive activations in MAE ViT-L. In this model, a feature dimension (927) exhibits uniformly large values across all tokens.

# Massive activations are biases in ViTs.

Figure 4.14 shows the three largest activation magnitudes and the median per layer in CLIP and DINOv2 ViT-L, averaged over 1k images. We find that massive activations are consistently present across images and their values remain largely the same around the mean values. It is worth noting that unlike LLMs, massive activations start to appear only in the later stages of ViTs.

![](bbox=[0.15, 0.54, 0.85, 0.68])

Figure 4.14: Three largest activation magnitudes and the median magnitude at each layer in CLIP and DINOv2 ViT-L.

Following our methodology in Section 4.4, we perform intervention analysis on CLIP ViT-L. We modify the two largest massive activations to zero and mean values respectively. The intervention is conducted on layer 13, where massive activations first appear within this model. Results are shown in Table 4.4, where we evaluate the zero-shot accuracy on ImageNet. We can see that setting massive activations to zero leads to significant drop in accuracy while setting to their means results in negligible accuracy drop. These results indicate that massive activations function as fixed but crucial biases in ViTs, aligned with our observations in Section 4.4.