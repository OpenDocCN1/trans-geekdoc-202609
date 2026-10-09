
## SOL-257 CH.SOL- 8.81.

1.  Usually data augmentation is a technique that is heavily used during training, especially for increasing the number of instances of minority classes. In this case, augmentations are used during inference, and this method is entitled Test Time Augmentation (TTA).

2.  Here are several image augmentation methods for TTA, with two augmentations shown also in PyTorch.
    - Horizontal flip
    - Vertical flip
    - Rotation
    - Scaling
    - Crops

    ```python
    transforms.HFlip(p=1)(image)
    transforms.VFlip(p=1)(image)
    ```

    ![](img/574135cb1d7125b50cf484d943cdd676_339_0.png)

## SOL-258 CH.SOL- 8.82.

- i Unseen
- ii Overfitting

## 8.3.9 Optimization, Loss

### Stochastic gradient descent, SGD

## SOL-259 CH.SOL- 8.83.

There is no relation to random number generation; the true meaning is the use of batches during the training process.

## SOL-260 CH.SOL- 8.84.

A larger batch size decreases the variance of the gradient estimation of SGD. Therefore, if your training loop uses larger batches, the model will converge faster. On the other hand, smaller batch sizes increase the variance, leading to the opposite phenomena; longer convergence times.

## Momentum

## SOL-261 CH.SOL- 8.85.

Momentum introduces an extra term which comprises a moving average which is used in gradient descent update rule to exponentially decay the historical gradients. Using such term has been demonstrated to accelerate the training process ( [1] ) requiring less epochs to converge.

## SOL-262 CH.SOL- 8.86.

The answers are as follows:

1.  The derivative of the logistic activation function is extremely small for either negative or positive large inputs.
2.  The use of the $\tanh$ function does not alleviate the problem since we can scale and translate the sigmoid function to represent the $\tanh$ function:

    $$ \begin{align} \operatorname{tanh}(z) = 2\sigma(2z) - 1 \end{align} $$

    While the sigmoid function is centred around 0.5, the $\tanh$ activation is centred around zero. Similar to the application of BN, centring the activations may aid the optimizer converge faster. Note: there is no relation to SGD; the issue exists when using other optimization functions as well.

## SOL-263 CH.SOL- 8.87.

The answers are as follows

- i. True.
- ii. False. In stochastic gradient descent, the gradient for a single sample is quite different from the actual gradient, so this gives a more noisy value, and converges slower.
- iii. True.
- iv. False. SGD requires less memory.

### Norms, L1, L2

## SOL-264 CH.SOL- 8.88.

1.  The L2 norm.
2.  The Euclidean distance which is calculated as the square root of the sum of differences between each point in a set of two points.
3.  The Manhattan distance is an L1 norm (introduced by Hermann Minkowski) while the Euclidean distance is an L2 norm.
4.  The Manhattan distance is:
    $|6-2| + |1-8| + |4-3| + |5-(-1)| = 4+7+1+6 = 18$ (8.77)
5.  The Euclidean distance is:

$$ \begin{aligned} & \sqrt{(6-2)^{2}+(1-8)^{2}+(4-3)^{2}+(5-(-1))^{2}} \\ & =\sqrt{102} \end{aligned} $$

(8.78)

## SOL-265 CH.SOL- 8.89.

The PyTorch implementation is in (8.83). Note that we are allocating tensors on a GPU but first they are created on a CPU using numpy. This is also always the interplay between the CPU and the GPU when training NN models. Note that this only works if you have GPU available; in case there is no GPU detected, the code has a fallback to the CPU.

```python
% reset - f
import torch
import numpy

use_cuda = torch.cuda.is_available()
device = torch.device("cuda" if use_cuda else "cpu")
print(device)
x1np = numpy.array([6,1,4,5 ])
x2np = numpy.array([2,8,3,-1])
x1t=torch.FloatTensor(x1np).to(device) # Move to GPU if available
x2t= torch.FloatTensor(x2np).to(device)
dist = torch.sqrt (torch.pow(x1t - x2t, 2). sum())
dist
> cuda
> tensor(10.0995 , device= 'cuda:0')
```

![](img/574135cb1d7125b50cf484d943cdd676_342_0.png)

## SOL-266 CH.SOL- 8.90.

The L2 loss is suitable for a target, or a response variable that is continuous. On the other hand, in a binary classification problem using LR we would like the output to match either zero or one and a natural candidate for a loss function is the binary cross-entropy loss.

## References

- F. T. B. Fuglede. ‘Jensen-Shannon Divergence and Hilbert space embedding’. In: *IEEE Int. Sym. Information Theory* (2004) (cit. on pp. 243, 295).
- C. Bennett. ‘Information Distance’. In: *IEEE Trans. Pattern Anal. Inform. Theory*. 44:4 (1998), pp. 1407–1423 (cit. on pp. 242, 296).
- B. Bigi. ‘Using Kullback-Leibler Distance for Text Categorization’. In: *In Proceedings of the ECIR-2003, Lecture Notes in Computer Science, Springer-Verlag 2633* (2003), pp. 305–319 (cit. on pp. 243, 296).
- G. Chen. *Rethinking the Usage of Batch Normalization and Dropout in the Training of Deep Neural Networks*. 2019. arXiv: *1905.05928* [cs.LG] (cit. on p. 322).
- Y. S. Chen et al. ‘Deep photo enhancer: Unpaired learning for image enhancement from photographs with gans’. In: *IEEE Conference on Computer Vision and Pattern Recognition*. 2018, p. 6306 (cit. on p. 229).
- I. Ciucu and J. A. Ware. ‘Layered neural networks as universal approximators’. In: *Computational Intelligence Theory and Applications*. Ed. by B. Reusch. Berlin, Heidelberg: Springer Berlin Heidelberg, 1997, pp. 411–415 (cit. on p. 302).
- T. Floyd. *Digital Fundamentals*. Prentice Hall, 2003 (cit. on p. 250).
- H. Gejer and M. Gejer. ‘Added value of double reading in diagnostic radiology, a systematic review’. In: *Insights into Imaging* 9 (Mar. 2018). DOI: 10.1007/s13244-018-0599-0 (cit. on pp. 280, 324, 325).
- X. Glorot and Y. Bengio. ‘Understanding the difficulty of training deep feedforward neural networks’. In: *Journal of Machine Learning Research - Proceedings Track* 9 (Jan. 2010), pp. 249–256 (cit. on pp. 256, 310).
- S. Gomari, M. Mirhassani and M. Ahmadi. ‘Precise digital implementations of hyperbolic tanh and sigmoid function’. In: *2016 50th Asilomar Conference on Signals, Systems and Computers* (2016) (cit. on p. 252).
- I. Goodfellow, Y. Bengio and A. Courville. *Adaptive computation and machine learning*. MIT Press, 2016 (cit. on p. 328).
- J. Gurmeet Singh Manku. ‘Detecting near-duplicates for web crawling’. In: *Proceedings of the 16th International Conference on World Wide Web* (2007), p. 141 (cit. on pp. 242, 243, 296).
- K. He. *Deep Residual Learning for Image Recognition*. 2015. arXiv: 1512.03385 (cit. on p. 277).
- K. He et al. *Delving Deep into Rectifiers: Surpassing Human-Level Performance on ImageNet Classification*. 2015. arXiv: 1502.01852 [cs.CV] (cit. on pp. 256, 271).
- A. Ignatov et al. ‘Dslr-quality photos on mobile devices with deep convolutional networks’. In: *IEEE International Conference on Computer Vision (ICCV)*. 2017, pp. 3297–3305 (cit. on p. 229).
- S. Ioffe and C. Szegedy. ‘Batch Normalization’. In: *CoRR* abs/1502.03167 (2015). arXiv: 1502.03167 (cit. on pp. 271, 322, 326).
- R. Kohavi. ‘A Study of Cross-Validation and Bootstrap for Accuracy Estimation and Model Selection’. In: *Morgan Kaufmann*, 1995, pp. 1137–1143 (cit. on pp. 229, 287).
- A. Krizhevsky, I. Sutskever and G. E. Hinton. ‘ImageNet Classification with Deep Convolutional Neural Networks’. In: *Advances in Neural Information Processing Systems* . Ed. by F. Pereira et al. Vol. 25. Curran Associates, Inc., 2012, pp. 1097–1105 (cit. on pp. 250, 304 ).
- Libtorch: The PyTorch C++ frontend is a C++14 library for CPU and GPU tensor computation . 2020 (cit. on pp. 252, 254 ) .
- A. Paszke et al. ‘Automatic differentiation in PyTorch’. In: *31st Conference on Neural Information Processing Systems* . 2017 (cit. on pp. 264, 265 ) .
- P. Ramachandran. *Searching for Activation Functions* . 2017. arXiv: 1710.05941 [cs.NE] (cit. on pp. 257, 258 ) .
- D. E. Rumelhart and G. E. Hinton. ‘Learning Representations by Back Propagating Errors’. In: *Neurocomputing: Foundations of Research* . Cambridge, MA, USA: MIT Press, 1988, pp. 696–699 (cit. on pp. 234, 250, 258, 290, 304 ) .
- S. Sengupta et al. ‘Sfsnet: Learning shape, reflectance and illuminance of faces in the wild’. In: *Computer Vision and Pattern Recognition (CVPR)* . 2018 (cit. on p. 229 ) .
- Z. Shu, E. Yumer and S. Hadap. ‘Neural face editing with intrinsic image disentangling’. In: *Computer Vision and Pattern Recognition (CVPR) IEEE Conference* . 2017, pp. 5444–5453 (cit. on p. 229 ) .
- K. Simonyan and A. Zisserman. *Very Deep Convolutional Networks for Large-Scale Image Recognition* . 2014. arXiv: 1409.1556 [cs.CV] (cit. on pp. 261, 263 ) .
- P. Sledzinski et al. ‘The current state and future perspectives of cannabinoids in cancer biology’. In: *Cancer Medicine* 7.3 (2018), pp. 765–775 (cit. on pp. 264, 265 ) .
- C. Szegedy et al. ‘Inception v4, Inception-ResNet and the Impact of Residual Connections on Learning’. In: *ICLR 2016 Workshop* . 2016 (cit. on p. 322 ) .
