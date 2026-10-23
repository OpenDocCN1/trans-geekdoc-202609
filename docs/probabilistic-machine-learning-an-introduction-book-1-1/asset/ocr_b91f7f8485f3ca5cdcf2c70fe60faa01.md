# Chapter 15. Neural networks for sequences

![](bbox=[0.2, 0.08, 0.8, 0.35])

![](bbox=[0.2, 0.38, 0.8, 0.25])

state-of-the-art performance on this task [CNB17]. We can also make the generated sequence depend on some kind of input vector x. For example, consider the task of image captioning: in this case, x is some embedding of the image computed by a CNN, as illustrated in Fig. 15.3. (In this example, D = H × W × 3 is the size of the image and C is the size of the vocabulary.) See e.g., [Hos+18] for a review of image captioning methods.

It is also possible to use RNNs to generate sequences of real-valued feature vectors, such as pen strokes for hand-written characters [Gra13] and hand-drawn shapes [HE18]. This can also be useful for time series forecasting real-value sequences.

# 15.2.1.2 Models

```
p(y_{1:T}|x) = \sum_{h_{1:T}} p(h_{1:T}|x) p(y_1|h_1) \prod_{t=2}^T p(y_t|h_t) p(h_t | h_{t-1}, y_{t-1}, x) \quad (15.1)
```

> 1. In the language modeling community, performance is usually measured by perplexity. This is explained in Sec. 6.1.5, but it suffices to know that low perplexity means high log likelihood.