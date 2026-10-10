
# Training and Optimization of DCNN Model

## Model Training

In order to practise for all images in data bases, the middle was cut down using `224 = 224` moves. The model was learned by reverse propagation of the Stochastic Gradient (`SGD`). The learning rate was extremely low at `0.0001` with age `30` `SGD`. It has been maximally optimised. Negative Log Likelihood (`NLL`) has been used in `SGD` testing as an objective function or criterion. For N-classification issues, `NLL` is also used. Gaussian, zero and `0.01` were used to initialise weights for all layers. In the three completely connected layers `1` and `0`, the biases for `CVL2`, `CVL4`, and `CVL5` have already been known. The study rate has continuously been maintained and the learning rate decreased for all storm gradients, including `0.0001`, but in turn the duration of the training increased. Another argument for continuous learning is that our data have already been developed with a very low learning rate, and it clearly requires additional staff and more resources to reduce it. A `0.0422` training error for up to `30` planning times was used to customise the model. `SGD` is the most widely used neural network algorithm and is highly effective in the analysis of discriminatory linear classifications under a convex-loss function, such as `SVM` or logistic regression. The two main benefits of `SGD` includes reliability and ease of deployment including coordination options for networks, such as number of iterations, learning rate, decay in rates, etc. The need for hyperparameters such as numerous times or iterations and control parameters include some of the disadvantages of `SGD`. For each sample of `xi` and `yj` training `SGD` updates the parameters. The `SGD` parameter is modified. The most common neural networking algorithm is back propagation in combination with certain optimization strategies, such as the `SGD`. All back propagation parameters determine the gradients.

![Figure 4.3 Training of image with DCNN.](html/images/9780367720919_C004_003.jpg)

**Figure 4.3** Training of image with DCNN.

When the objective function is reduced, the `SGD` receives measured gradients and updates them as inputs. Returns include the known objective for the determination of the input losses, i.e. the actual class mark. The chain rule is used to measure the gradients in relation to the loss function for each layer. Each layer consists of three important back stretching phases, that is, the forward transition, the reverse transition and the derivative of operation, where the layer includes parameters as shown in [Figure 4.3](#ch12.xhtml#f31). There is no parameter available for such layers, such as the pooling layer, and the derivative should not be specified. Parameters and derivatives of the cost function system w.r.t. parameters would be defined if the layer has parameters. An input is provided to each layer and an output is produced. The loss `E` is taken from the output layer and spread backwards from each layer. Many of these layers exist in each layer and the vector parameters should be familiar with all the layer parameters.

## 4.3.2 Phase 2

Reprinted features may be obtained from the last three fully connected model layers, e.g., `FSC1` – `FCL 3`, as soon as the `DCNN` model is refined and trained for identification of multimodal medical images. For creating a database, the features `F1i`, `F2i` and `F3i` are then extracted from fully connected `1–3` layers of that specific image by feed from a trained `DCNN` classification model, respectively. Similarly, `F1i`, which is a function database extracted from `FCL1` and `F2i` and `F3i`, reflects `FCL2` and `FCL3` databases where `i=1` to `P` and `P` equals the number of training samples.

In any query formulation, similar images to those in a query image can be found using

```
d(a,b) = sqrt(sum_{i=1}^{P} (a_i - b_i)^2)  (4.3.1)
```

When `ai` and `bi` are query- and database-image functions, by comparing feature representations extract for the query-image, using Euclidian distance metric. Finally, comparative analysis of the efficiency of feature recovery from `FCL1` to `FCL3` are carried out.

## 4.3.3 Phase 3: Optimization

### 4.3.3.1 Spotted Hyena Optimizer (SHO)

In this subsection, `SHO` algorithm ([Dhiman 2018](#ch12.xhtml#r119)) are mathematical models, i.e. search, encircle, hunt, and attack prey.

#### 4.3.3.1.1 Encircling Prey

The current best candidate solution is seen as the target prey to mathematically form the social hierarchy of spotted hyenas. Now the other quest agents update their best approach.

```
D_h = | B * P_p(x) - P(x) |  (4.3.2)
P(x + 1) = P_p(x) - E * D_h  (4.3.3)
```

Where `Dh` defines the distance of the prey from the spotted hyena, `x` indicates current isolation, `B` and `E` are coefficient vectors, `Pp` indicates the location vector of the prey, `P` is the location vector of the spotted hyena. The vectors `B` and `E` are as follows:

```
B = 2 * r * d_1  (4.3.4)
E = 2 * h * r * d_2 - h  (4.3.5)
h = 5 - (Iteration * (5 / Max_Iteration))  (4.3.6)
```

Where, `Iteration=1,2,3,..., Max[Iteration]`

`h` is reduced linearly from `5` to `0` over the course of full iterations to balance discovery and operation (`MaxIteration`). In addition, with an increase in iteration value, this process facilitates greater exploitation. `Rd1` and `rd2` are, however, random vectors within `[0, 1]`.

#### 4.3.3.1.2 Hunting

It is believed that the best search agent knows the location of prey in order to mathematically identify the hunting behaviour of spotted hyenas. The other search officers form a cluster of trustworthy friends to the best search officer and have been able to offer the best options so far to update their position. In this mechanism, the following equations are proposed:

```
D_h = | B * P_h - P_k |  (4.3.7)
P_k = P_h - E * D_h  (4.3.8)
C_h = P_k + P_{k+1} + ... + P_{k+N}  (4.3.9)
```

Where `Ph` determines the first best spotted hyena location, and `Pk` indicates the other spotted hyena position. The number of hyenas contained here as measured as follows, is indicated by `N`:

```
N = count_nos(P_h, P_{h+1}, P_{h+2}, ..., (P_h + M))  (4.3.10)
```

Where `M` is a random vector in the area of `[0.5, 1]`, and `nos` defines the number of solutions and includes all the solutions used, after the addition of `M`, which is very similar to being the best solution in a given search field.

#### 4.3.3.1.3 Attacking

The value of vector `h` is reduced in order to mathematically model the attack on a prey. Vector `E` variance is also minimized by changing the value in Vector `h` from `5` to `0` during the iteration process. The following is the mathematical formula for attacking the prey:

```
P(x + 1) = C_h / N  (4.3.11)
```

When `P(x+1)` saves the best solution and changes other search agents' location in accordance with the best search agent's position. The `SHO` algorithm enables its search agents to update its location and attack it.

#### 4.3.3.1.4 Searching
