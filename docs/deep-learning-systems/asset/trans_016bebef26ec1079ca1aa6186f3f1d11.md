
All the above optimizers share a common challenge that `LARS` and `LAMB` addresses. To maintain stability, weights with a small magnitude should have a small weight update magnitude, and vice versa. However, every layer in a model often has vastly different ![image](images/pg85_4.png) ratios. A small ratio can lead to training instability (divergence), and a large ratio can lead to slow learning. `LARS` and `LAMB` improve training stability by normalizing the step size in each layer. This additional stability allows training with large-batches (up to some size determined experimentally).

Layer-wise Adaptive Rate Scaling (`LARS`) uses a local LR `α^(l)` proportional to the ratio of the magnitude of the weights to the magnitude of the gradients \[YGG17\]. `LARS` is applied to `SGD` as follows:

![image](images/pg85_1.png)

where `α[0]` is the global LR.

`LARS` can be used with `SGDM` or with `Adam`, known as `LAMB` \[YLR+20\]. `LAMB` was successfully used by Google to train `BERT` and `ResNet-50` with batch size `32K` with little hyperparameter tuning. The `Adam` equations are modified as follows in `LAMB`:

![image](images/pg85_2.png)

Other influential optimizers are `AdaGrad` (in particular, for sparse data), `RMSProp`, `AdaDelta`, `Nadam`, `Nesterov` accelerated gradient (`NAG`), `AdamW`, `AMSGrad`, and `Novo-Grad` \[DHS11, HSS12, Zei12, Doz16, BLB17, LH19, RKK19, GCH+20\]. [图 4.9](#14_Chapter04.xhtml#fig4-9) shows an estimated pedigree of optimizers. These are first-order optimizers. `AdaHessian` is a second-order optimizer that converges to a better minimum than first-order optimizers without the prohibited computational cost of other second-order optimizers \[YGS+20\]. Given the promising results, `AdaHessian` adoption may grow.

Stochastic weight averaging (`SWA`) and LookAhead (`LA`) are complementary techniques that improve generalization by converging to a better (flatter) minimum \[IPG+19, ZLH+19\]. The motivation for `SWA` is that during the later training iterations, `SGD` bounces between the borders of a wider minimum. The average of the bounces is a better solution. `SWA` maintains a separate set of averaged weights `w[SWA]` in addition to the regular set of weights `w` used by the optimizer. `w[SWA]` is initialized with `w` after completing at least 75% of the training iterations. Then, after completing several iterations, `w[SWA]` is updated as follows:

![image](images/fig4_9.png)

图 4.9: A pedigree of optimization algorithms.

![image](images/pg86_1.png)

where `n[cycle]` is the number of completed cycles after initializing `w[SWA]`, and `w` is the model learned by the optimizer. One cycle consists of multiple iterations, typically one epoch, but this can vary depending on the dataset’s size.

For training, `SWA` requires `sizeof(w[SWA])` additional memory, which is relatively small compared to the activations and requires negligible additional computations to update. No additional memory or computations is required for serving.

LookAhead (`LA`) follows a similar approach to `SWA` \[ZLH+19\]. The primary difference is that the optimizer updates its weights to `w[LA]` after some iterations: `w := w[LA]`. That is, the moving average `w[LA]` changes the optimization trajectory.

`Ranger` is a combination of `RAdam` and `LA`, and `RangerLARS` applies `LARS` techniques to `Ranger` \[Wri19\]. We recommend using `Ranger` as the go-to optimizer and `RangerLARS` when using large batches.

## 4.4 反向传播

The rediscovery of the backpropagation algorithm in the 1980s facilitated multilayer `NN` training. Backpropagation provides an efficient way to compute the gradients, which are then used by the optimization algorithm. This section introduces some of the mathematics behind back-propagation to demystify the learning process; for a reader who may not be interested in all these details, the main takeaway is that backpropagation boils down to multiplications and additions.

The cross-entropy cost function, also known as the log-cost or logistic cost, is as follows:

![image](images/pg87_1.png)

where `N` is the number of samples in a training batch, ![image](images/pg87_8.png) is 1 if sample `n` belongs to class `k` and 0 otherwise, ![image](images/pg87_9.png) is the model’s prediction (as a probability) that sample `n` belongs to class `k`. The intuition is that when the model predicts a low probability for the correct class, the cost for that sample is high and vice versa. When ![image](images/pg87_10.png), as ![image](images/pg87_11.png) approaches zero, the loss approaches infinity. Note that in practice, the cost function includes a weight decay penalty (shown here but often omitted to simplify the notation):

![image](images/pg87_2.png)

where `λ ≥ 0` is the regularization factor.

This objective function is minimized using an optimizer from [第 4.3 节](#14_Chapter04.xhtml#sub4-3) chosen by the data-scientist. The input to the optimizer is the gradient or partial derivatives of the cost with respect to each weight ![image](images/pg87_12.png):

![image](images/pg87_3.png)

which needs to be computed for all the weights in a layer and for all the layers of the topology. Each partial derivative is a metric of how a change in the respective weight changes the cost. The optimizer specifies how to nudge each weight to decrease the cost.

[图 4.10](#14_Chapter04.xhtml#fig4-10) illustrates how backpropagation works in a toy model to compute one such partial derivative, specifically ![image](images/pg87_4.png), where ![image](images/pg87_5.png) to simplify the notation. This partial derivative depends on the next layer’s gradient, which depends on the following layer’s gradient, and so on. The partial derivative in the color boxes are computed from the forward propagation equations, and their numerical values can be plugged into the chain of equations to determine ![image](images/pg87_6.png). Note that the hidden layer assumes a `ReLU` activation function. In practice, the partial derivatives for an entire layer are computed as a group using matrix algebra.

![image](images/fig4_10.png)

图 4.10: Using the chain rule to compute the partial derivative of the cost with respect to a weight in the model. For simplicity, the bias is omitted from the figure.

## 4.5 训练技术

Training a model involves preparing the dataset and tuning various hyperparameters, such as choosing a topology, selecting an optimizer, and specifying a batch size. In this section, we describe general guidelines in dataset preparation, topology design, and debugging training. These guidelines are based on the current best heuristics rather than a closed-form optimal solution. Thus, experimentation may be required to determine if a guideline is beneficial to a specific training task.

### 4.5.1 训练数据集
