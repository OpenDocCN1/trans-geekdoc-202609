Loss = \(\lambda_{coord} \sum_{i=0}^{S'} \sum_{j=0}^{B} [1_{ij}^{obj}(x_i - \hat{x}_i)^2 + (y_i - \hat{y}_i)^2]\)
\(+ \lambda_{coord} \sum_{i=0}^{S'} \sum_{j=0}^{B} 1_{ij}^{obj} [(\sqrt{w_i} - \sqrt{\hat{w}_i})^2 + (\sqrt{h_i} - \sqrt{\hat{h}_i})^2]\)
\(+ \sum_{i=0}^{S'} \sum_{j=0}^{B} 1_{ij}^{obj}(C_i - \hat{C}_i)^2 + \lambda_{noobj} \sum_{i=0}^{S'} \sum_{j=0}^{B} 1_{ij}^{obj}(C_i - \hat{C}_i)^2\)
\(+ \sum_{i=0}^{S'} 1_{ij}^{obj} \sum_{C \in class} (P_i(c) - P_i(\hat{c}))^2\).

In this paper, authors refined the loss function to fit for multiple fish application. The proposed loss function is regularized to reduce the small dataset and overfitting problem, L2 regularization is to add a regularization function after the cost function which is listed in the Equations (6) and (7).

Loss = \(\sum_{i=0}^{S'} (coordError + IoUError + classError)\)
+ L2 Regularization,

![](bbox=[0.15, 0.49, 0.85, 0.82])

**Figure 16.** Effect of data augmentation on overfitting.