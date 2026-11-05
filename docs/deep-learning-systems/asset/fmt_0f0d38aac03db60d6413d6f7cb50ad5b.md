
An interesting and counterintuitive phenomenon unique to various DL topologies is the deep double descent, illustrated in [Figure 4.3](#14_Chapter04.xhtml#fig4-3) \[NKB+20\]. As the topology complexity increases (that is, as the model grows in depth), the validation error first follows the expected trajectory of decreasing and then increasing, but then it begins to decrease again. That is, increasing the size of the topology can lower the test error in some scenarios. The exact reason is not well understood as complex models should result in overfitting. A tentative (hand-wavy) reason is that very large topologies can explore a larger solution space leading to superior solutions. Understanding this phenomenon and the impact on the recommended training techniques is ongoing research. Most practitioners safely ignore this phenomenon or are not aware of it.

Another source of poor generalization may be sharp minima \[HS97\]. This hypothesis is based on empirical evidence. [Figure 4.4](#14_Chapter04.xhtml#fig4-4) illustrates the intuition with a toy 1D example using only one weight or feature (the `x`-axis). Training involves iteratively updating the model and moving to an area in the solution space with lower training error. The training cost function (solid blue line) is similar but slightly different than the testing cost function (dotted green line). This difference is because the test samples are similar but not identical to the training samples. In this example, the flat minimum solution and the sharp minimum solution have the same training error but different test errors. These errors are represented by `J(w)` along the `y`-axis. The flat minimum solution has a low test error, while the sharp minimum solution has a high test error (the green dot). A measurement of flatness is the trace of the Hessian; a small trace indicates a flat minimum \[DYC+19\].

![image](images/fig4_3.png)
Figure 4.3: An illustration of the deep double descent observed in some DL topologies; as the complexity increases, the validation error decreases and then increases as expected, but then it begins to decrease again. Based on \[NKB+20\].

![image](images/fig4_4.png)
Figure 4.4: In this toy example, the cost function with respect to the test dataset is slightly shifted from the cost function with respect to the training dataset. The sharp minimum solution has a high test error. The flat minimum has a small test error. Based on \[KMN+17\].

While a flat minimum generalizes better to unseen data, a sharp minimum does not necessarily indicate overfitting, and a flat minimum does not necessarily indicate low validation error \[ML18\]. Also, the functions resulting in a flat minimum can be altered to result in a sharp minimum without affecting the validation error, demonstrating the hypothesis above does not always hold \[DPB+17\].

There are various techniques to improve generalization, often by simplifying (regularizing) the model. The most common ones are as follows:

### Larger datasets
Larger datasets is the best technique to avoid overfitting. The toy example above only used four samples to train the fourth-order polynomial. Adding more samples while keeping the same model complexity (fourth-order polynomial) results in a more affine-like function that better generalizes to data not in the training set. OpenAI recommends for NLP models increasing the number of parameters by 2.55× whenever the dataset doubles to improve learning capacity and avoid over/underfitting \[KMH+20\].

### Weight decay
Weight decay (also known as `L`[2]-regularization) penalizes the magnitude of the weights and reduces overfitting. In the fourth-order polynomial example above, this would penalize the magnitude of the coefficients and result in a more affine-like function. The objective function incorporates the weight decay by adding a penalty term:
![image](images/pg77_1.png)
where `λ` ≥ 0 is the regularization factor and `w` is the model weights (the polynomial coefficients in the regression example above). The bias weight does not have a multiplicative interaction with the `activations`; therefore, it is not regularized. Note that `L`[1] (rather than `L`[2], as shown above) regularization is less common.

### Smaller batches
Smaller batches improves generalization \[ML18\]. A training iteration involves processing a batch of data. Larger batches can have computational advantages (they have higher data reuse), but often large batches result in sharp minima. The ideal is a medium size batch where the model converges to a flat minimum and has high compute utilization. Finding an adequate batch size requires experimentation.

### Better optimizer
Better optimizer that finds a solution with a lower validation error. In [Section 4.3](#14_Chapter04.xhtml#sub4-3), we discuss the gradient descent optimizer and others less prone to sharp minima solutions, such as LARS, LAMB, and RangerLARS.

### Topology pruning
Topology pruning means forcing some of the smaller weights to zero or removing parts of the model. In [Section 6.3](#16_Chapter06.xhtml#sub6-3), we discuss pruning in more detail.

### Label-smoothing regularization (LSR)
Label-smoothing regularization (LSR) modifies the ground-truth one-hot vector by adding a small `ϵ`/`M` value to all the zero entries, where `M` is the number of classes and `ϵ` is a small value, such as `ϵ` = 0.1 \[SVI+15\]. The “1” entry in the one-hot vector is changed to 1 – `ϵ` to maintain a valid probability distribution. Reducing the difference between the largest logit and all others reduces the confidence of a model and results in better adaptation to non-training samples.

### Early stopping
Early stopping means the training stops when the validation error begins to increase. Similarly, the model is evaluated on the validation dataset and saved every `n` training iterations, and the model with the lowest validation error is selected. There are mixed opinions on using early stopping. Regularization via weight decay without using early stopping can lead to bet ter results when the computational resources are available to experiment with multiple weight penalties. In practice, early stopping is a simple and effective technique to reduce overfitting and commonly used. Note, somewhat related, that Hoffer et al. demonstrated better generalization with additional training cycles when the validation error has plateaued, but the training error continues to decrease \[HHS17\].

### Model ensemble
Model ensemble is where an ensemble (group) of models is trained for a particular task. During inference, a combination of the models’ predictions is used, such as the average. Combining the predictions reduces the impact of each model overfitting. More formally, model ensemble reduces the variance of the validation error.

In addition, normalization and dropout (discussed in [Sections 2.6](#12_Chapter02.xhtml#sub2-6) and [2.9](#12_Chapter02.xhtml#sub2-9)) are other forms of regularization which reduce overfitting.

## 4.2 Weight Initialization
Training a model is the process of learning the weight values for a topology for a particular task. The initialization of the model weights at the start of training can significantly impact the learning (training convergence), particularly for deeper networks.

Initializing all the weights to the same value results in the weights having the same update and therefore prevents learning. The weights (including the biases) are typically sampled from random distributions. They are initialized such that the distribution of the `activations` has unit variance across a layer. This initialization reduces the likelihood of having exploding or diminishing gradients during the backpropagation step when multiplying gradients across several layers.
