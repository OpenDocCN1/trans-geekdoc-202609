
## Pooling

`Max pooling` chooses the largest element from the receptive field. `Average pooling` takes the average value of the receptive field, and `Sum pooling` takes the sum of the feature map elements.

### 5.7.3 Batch Normalization

`Batch Normalization` allows every layer in `CNN` to perform more independent learning. You may simply consider this as a layer used to normalize the output of the previous layer. The activations scale the input layer in normalization. `Batch Normalization` can be used to produce more accurate and efficient `CNN` models, which avoids the problem of overfitting. This layer is typically placed after convolution and pooling layers.

### 5.7.4 Fully connected layer

After the convolution and pooling layers, the rest is similar to any feed forward networks. We flattened our matrix into the vector and fed it into a `Fully connected layer` like a neural network. Consider the obtained feature map matrix is converted and turned to a vector ![](Image00390.jpg), this is fed to `Fully connected` layers to create a model. We can apply any activation function at this stage to produce an output. The choice of the activation function is the freedom of the model designer. You can choose activation functions such as `softmax`, `sigmoid`, etc.

## 5.8 Types of Convolutional Neural Networks (CNN)

There are several Convolutional neural networks, and some of them are listed below.

### 5.8.1 LeNet-5

[LeNet- 5](https://towardsdatascience.com/illustrated-10-cnn-architectures-95d78ace614d#e276) `LeNet` is an exceptional `CNN` introduced to perform object classification. It is exceptional in its performance, accuracy, and capability. This algorithm was initially developed and trained to classify 0-9 hand-written digits from the `MNIST` dataset. `LeNet` consists of 7 layers, and the activation function applied is `ReLU`.

### 5.8.2 AlexNet

[AlexNe t](https://towardsdatascience.com/illustrated-10-cnn-architectures-95d78ace614d#e971) `AlexNet` was introduced by Alex Krizhevsky, Ilya Sutskever, and Geoffery E. Hinton and won `ImageNet ILSVRC-2012` competition. This `CNN` is very similar to the `LeNet` structure but consists of many filters compared to the original `LeNet`. `AlexNet` is able to classify large set of objects. To deal with overfitting issues, `AlexNet` uses `dropout` instead of regularization to deal with overfitting.

### 5.8.3 VGGNet-16

[VGGNet-1 6](https://towardsdatascience.com/illustrated-10-cnn-architectures-95d78ace614d#c5a6) `VGGNet-16` was designed by Simonyan and Zisserman and became the runners up of the `ILSVRC-2014` competition. `VGGNet` is exceptional for feature extraction because of the simple pattern that it follows. The hyper-parameters for the filter size and the strides for both the convolution and pooling layers are constant: Filters of size `3 X 3` and `stride = 1` used at the convolution layer, and the `max-pooling` layer make use of filters of size `2 X 2` and `stride = 2`. Such layers are applied in a particular order all over the network.

### 5.8.4 ResNet

[ResNe t](https://towardsdatascience.com/illustrated-10-cnn-architectures-95d78ace614d#e4b1) `ResNet` provided better performance than `VGGNet` and came first in all the awards of the `ILSVRC 2015` for classification, detection, and localization. `ResNet` is otherwise called Residual Networks and was the most groundbreaking development in the area of `CNN` so far. `ResNet` makes use of `skip-connections` and `batch-normalizations` to aid training with thousands of layers without performance degradation. Performance degradation means the problem of "vanishing gradient," where the back-propagated gradient becomes infinitely small. `ResNet` used the idea of `identity shortcut connection` that transfers results to few deeper layers and skips some other layers in between.

### 5.8.5 GoogleNet/Inception

## CHAPTER 6 References

1. Alvarez-Melis, D., & Tommi, S. (2018). On the robustness of interpretability methods. arXiv preprint arXiv:1806.08049.
2. Baldi, P. & Brunak, S. (2002). Bioinformatics: A Machine Learning Approach. Cambridge, MA: MIT Press.
3. Baldi, P., Frasconi, P., Smyth, P. (2003). Modeling the Internet and the Web - Probabilistic Methods and Algorithms. New York: Wiley.
4. Bishop, C. M. (1995). Neural Networks for Pattern Recognition. New York: Oxford University Press.
5. Breiman, L. (2001). Random Forests. Machine Learning. Springer.
6. Brown, Tom B. (2017). Adversarial patch. arXiv preprint arXiv:1712.09665
7. Chakrabarti, S. (2003). Mining the Web, Morgan Kaufmann.
8. Christoph, M. & Martin, B. (2020). Multi-Objective Counterfactual Explanations. In: Bäck T. et al. (eds) Parallel Problem Solving from Nature – PPSN XVI. PPSN 2020. Lecture Notes in Computer Science, vol 12269. Springer, Cham.
9. Cohen, P.R. (1995). Empirical Methods in Artificial Intelligence. Cambridge, MA: MIT Press.
10. Cook, R. Dennis. (1977). Technometrics: Detection of influential observation in linear regression.
11. Cowell, R.G., Dawid, A.P., Lauritzen, S.L., & Spiegelhalter,D.J. (1999). Graphical Models and Expert Systems.Berlin: Springer.
12. Cristianini, N. & Shawe-Taylor, J. (2000). An Introduction to Support Vector Machines. London: Cambridge University Press.
13. Doshi-Velez, F. & Been, K. ( 2017). Towards a rigorous science of interpretable machine learning, no. Ml: 1–13.
14. Duda, R., Hart, P., & Stork, D. (2001). Pattern Classification. New York: Wiley.
15. Fanaee-T, H. & Joao, G. (2013). Event labeling combining ensemble detectors and background knowledge. Progress in Artificial Intelligence. Springer Berlin Heidelberg, 1–15.
16. Fisher, A., Cynthia, R. & Francesca, D. (2018). Model Class Reliance: Variable importance measures for any machine learning model class, from the ‘Rashomon’ perspective.
17. Friedman, H. & Bogdan P. (2008). Predictive learning via rule ensembles. The Annals of Applied Statistics. JSTOR, 916–54.
18. Friedman, J. H. (2001). Greedy function approximation: A gradient boosting machine. Annals of statistics. 1189-1232.
19. Greenwell, M., Bradley, C. & Andrew, J. (2018). A simple and effective model-based variable importance measure. arXiv preprint arXiv:1805.04755.
20. Hastie, T., Tibshirani, R., & Friedman, J. (2001). The elements of Statistical Learning - Data Mining, Inference, and Prediction. Berlin: Springer-Verlag.
21. Holte, Robert C. (1993). Very simple classification rules perform well on most commonly used datasets. Machine learning. 63-90.
22. Jordan, M. (2003). Probabilistic Graphical Models. Professor Jordan has kindly shared a pre-publication draft.
23. Kaufman, L. & Peter, R. (1987). Clustering by means of medoids. North-Holland.
24. Kearns, M. & Vazirani, U. (1994). Computational Learning Theory. Cambridge, MA: MIT Press.
25. Laugel, T. (2017). Inverse classification for comparison-based interpretability in machine learning. arXiv preprint arXiv:1712.08443.
26. Letham, B. et al. (2015). Interpretable classifiers using rules and Bayesian analysis: Building a better stroke prediction model. The Annals of Applied Statistics 9.3: 1350-1371.
27. Lundberg, M. & Su-In, Lee. (2017). A unified approach to interpreting model predictions. Advances in Neural Information Processing Systems.
28. Miller, T. (2017). Explanation in artificial intelligence: Insights from the social sciences. arXiv Preprint arXiv:1706.07269.
29. Mitchell, T. (1997). Machine Learning. New York: Mc Graw-Hill.
30. Russel, S. & Norvig, P. (2003). Artificial Intelligence: A Modern Approach. 2nd Edition. New York: Prentice-Hall.
31. Szegedy, C. (2013). Intriguing properties of neural networks. arXiv preprint arXiv:1312.6199.
32. Štrumbelj, E. & Igor, K. (2014). Explaining prediction models and individual predictions with feature contributions." Knowledge and information systems 41.3: 647-665.
