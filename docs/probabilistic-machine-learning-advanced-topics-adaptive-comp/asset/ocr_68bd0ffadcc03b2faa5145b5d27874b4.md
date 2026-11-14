![](bbox=[0.15, 0.13, 0.85, 0.37])

![](bbox=[0.15, 0.39, 0.85, 0.64])

where T > 0 is a temperature parameter, which can be estimated by maximum likelihood on the validation set. The effect of this temperature parameter is to make the distribution less peaky, as shown in Figure 14.3. [Guo+17] show empirically that this method produces the lowest ECE on a variety of DNN classification problems (see Figure 14.1 for a visualization). Furthermore, it is much simpler and faster than the other methods.

Note that Platt scaling and temperature scaling do not affect the identity of the most probable class label, so these methods have no impact on classification accuracy. However, they do improve calibration performance. A more recent multi-class calibration method is discussed in [Kul+19].

# 14.2.2.6 Label smoothing

When training classifiers, we usually represent the true target label as a one-hot vector, say y = (0, 1, 0) to represent class 2 out of 3. We can improve results if we “spread” some of the probability mass across all the bins. For example we may use y = (0.1, 0.8, 0.1). This is called label smoothing and