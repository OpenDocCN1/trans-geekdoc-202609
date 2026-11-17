![](bbox=[0.13, 0.11, 0.86, 0.32])

Figure 10.6 Histograms of residuals for CENN (0 outliers) and LCNN (50 outliers).

# 10.3.3 Outliers in MNIST

The reason why LCNN performed better than CENN can be linked to outliers detected in the MNIST dataset by the robust method. A histogram of LCNN residuals in Figure 10.6 indicates that 50 outliers exist in the data while the histogram for CENN does not show any evidence of outliers. In effect, CENN was able to fit 100% because there are enough parameters to overfit the data, whereas in the case of LCNN, only 97.5% of the digits were recognized and fitted. The remaining 50 images were designated as potential outliers by LCNN. This serves as a form of auto-regularization because the model built by LCNN effectively ignored 50 images. These outlier images are shown in Figure 10.7. Note that many of the circled images are not recognizable as numbers and therefore can be considered as outliers. This is a potentially valuable capability arising from the use of robust methods on the MNIST dataset.

# 10.4 Optimization of Neural Networks

To conclude this chapter, we shift our focus to the critical aspect of optimization of neural networks. Optimization lies at the heart of training deep learning models. It determines how quickly and how effectively the neural network adapts its weights and biases to minimize the loss function. While gradient descent serves as the foundation, recent advancements have introduced more sophisticated optimization algorithms. Among these, the Adam optimizer stands out as a powerful and widely used technique. In this section, the goal is to bridge the gap between neural networks and optimization by describing the Adam optimizer and its role in deep learning. We cover gradient descent with momentum and rmsprop to provide a complete picture for the Adam optimizer. This optimization algorithm can also be used for linear and logistic regression, in addition to neural networks for which it was originally intended.

To review the basic operation of gradient descent, recall that the parameters are updated at each iteration using some fraction of the gradient based on the learning rate, \(\ell\), shown symbolically as follows, with \(t\) as the iteration count

```
\(\mathbf{w}^{(t+1)} = \mathbf{w}^{(t)} - \ell \times \left( \frac{\partial J(\mathbf{w})}{\partial \mathbf{w}} \right)^{(t)} .\) (10.4.1)
```