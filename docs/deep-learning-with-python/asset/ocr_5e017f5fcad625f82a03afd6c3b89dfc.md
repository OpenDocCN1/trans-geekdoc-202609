![](bbox=[0.179, 0.096, 0.781, 0.346])

**Figure 11.8** The MultiHeadAttention layer

This is similar in principle to what makes depthwise separable convolutions work: in a depthwise separable convolution, the output space of the convolution is factored into many subspaces (one per input channel) that get learned independently. The “Attention is all you need” paper was written at a time when the idea of factoring feature spaces into independent subspaces had been shown to provide great benefits for computer vision models—both in the case of depthwise separable convolutions, and in the case of a closely related approach, grouped convolutions. Multi-head attention is simply the application of the same idea to self-attention.

# ## 11.4.3 The Transformer encoder

If adding extra dense projections is so useful, why don’t we also apply one or two to the output of the attention projections mechanism? Actually, that’s a great idea—let’s do that. And our model is starting to do a lot, so we might want to add residual connections to make sure we don’t destroy any valuable information along the way—you learned in chapter 9 that they’re a must for any sufficiently deep architecture. And there’s another thing you learned in chapter 9: normalization layers are supposed to help gradients flow better during backpropagation. Let’s add those too.

That’s roughly the thought process that I imagine unfolded in the minds of the inventors of the Transformer architecture at the time. Factoring outputs into multiple independent spaces, adding residual connections, adding normalization layers—all of these are standard architecture patterns that one would be wise to leverage in any complex model. Together, these bells and whistles form the Transformer encoder—one of two critical parts that make up the Transformer architecture (see figure 11.9).