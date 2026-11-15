where the second term is weighted by \(1 - p_y(x, \theta)\), which is close to 0 if the sample is correctly classified and to 1 if it is (more) misclassified. This encourages the network to make more progress to the misclassified data points.

Based on a similar idea, we can also have adaptive \(\epsilon\) for each sample. A sample that is misclassified should have smaller \(\epsilon\) since it is not important (or not possible) to make it robust, whereas a corrected classified should be assigned with larger \(\epsilon\). Several methods have been proposed in this direction, including (Ding et al., 2018; Balaji et al., 2019; Cheng et al., 2020b).

# ## 12.4 Extended reading

+   - Wang et al. (2019d) developed algorithmic convergence analysis for adversarial training.
+   - Zhang et al. (2022) proposed distributed training algorithms for scaling up adversarial training.
+   - Cheng et al. (2021) proposed a self-progressing robust training method.