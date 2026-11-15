
attack spaces embedded in high-dimensional pixel spaces, the convex hull of the attack space associated with an image can contain images belonging to a different class. Thus we cannot certify large intervals of perturbations using a single certification cycle of linear relaxation-based verifiers.

*Explicit input splitting.* As we cannot certify large ranges of perturbation simultaneously, input-splitting is essential for verifying semantic perturbations. It reduces the gap between the linear bounds on activation functions and yields tighter bounds. We observe that

\(\min_{\epsilon^k \in [\ell_1^k \cup U_2^k), h(\epsilon^k) \le \delta} \min_{j \neq c} f_c^{sem}(\epsilon^k) - f_j^{sem}(\epsilon^k)\)
\(= \min_{l \in \{1, 2\}} \min_{\epsilon^k \in [\ell_l^k, h(\epsilon^k) \le \delta} \min_{j \neq c} f_c^{sem}(\epsilon^k) - f_j^{sem}(\epsilon^k).\)

If \(\min_{\epsilon^k \in [\ell^k, h(\epsilon^k) \le \delta} (\min_j f_c^{sem}(\epsilon^k) - f_j^{sem}(\epsilon^k)) > 0\) for both parameter dimensions \(l = \{1, 2\}\), then we have \(\min_{\epsilon^k \in [\ell_1^k \cup U_2^k), h(\epsilon^k) \le \delta} (\min_j f_c^{sem}(\epsilon^k) - f_j^{sem}(\epsilon^k)) > 0\). As a result, we can split the original interval into smaller parts and certify each of them separately to certify the larger interval. The drawback of this procedure is that the computation time scales linearly with the number of divisions as one has to run the certification for every part. However, for the color space experiments, it is found that a few partitions are already sufficient for tight certificate.

*Implicit input splitting.* As a motivating example, in Fig. 10.2(a), we give the form of the activation function for rotation. Even in a small range of rotation angle \(\theta\) (2°), the function is quite nonlinear, resulting in very loose linear bounds. As a result, we find that we are unable to get good verification results for datasets like MNIST and CIFAR-10 without increasing the number of partitions to very large values (\(\approx\) 40,000). This makes verification methods computationally infeasible. We aim at reducing the cost in explicit splitting by combining the intermediate bounds used by linear relaxation methods such as (Raghunathan et al., 2018; Zhang et al., 2018) to compute the suitable relaxation for the layerwise nonlinear activations. The idea is to use the shared linear bounds among all subproblems, and hence we only need to construct the matrices (Def. 3.3 and Cor. 3.7 in Weng et al., 2018a) \(\mathbf{A}^{(k)}\), \(\mathbf{T}^{(k)}\), \(\mathbf{H}^{(k)}\) once for all *S*-subproblems instead of having different matrices for each subproblem. This helps to reduce the cost significantly from a factor of *S* to 1 when *S* is large (which is usually the case to get good refinement).

For implementation, we split the original problem into *S*-subproblems. To derive bounds on the output of a neuron at any given layer *l*, we cal-

![](img/fa92deee3de0f00ea56e92ca0b92c8e4_118_0.png)

(a) Without splitting the input range

![](img/fa92deee3de0f00ea56e92ca0b92c8e4_118_1.png)

(b) Explicit splitting the input (5 divisions)

![](img/fa92deee3de0f00ea56e92ca0b92c8e4_118_2.png)

(c) Implicit splitting the input (20 divisions)

Figure 10.2 Bounds for activation function of SP layer in rotation.

culate the preactivation range for every subproblem. Then we merge the intervals of each neuron among all the subproblems (e.g., set \( u_r = \max u_{r,subi} \) and \( l_r = \min l_{r,subi} \) in Weng et al. (2018a)) to construct the linear relaxation, \( \mathbf{A}^{(k)} \), \( \mathbf{T}^{(k)} \), \( \mathbf{H}^{(k)} \) for the postactivation output of layer \( l \). Continuing this procedure till the last layer gives the bounds on the output of the whole neural network.

Fig. 10.3 illustrates the difference between explicit and implicit input space splittings. Recall that in Fig. 10.2(a), we give the form of the activation function for rotation. Even in a small range of rotation angle \( \theta \) (\( 2^\circ \)), we see that the function is quite nonlinear resulting in very loose linear bounds. Splitting the images explicitly into five parts and running them separately (i.e., explicit splitting as shown in Fig. 10.2(b)) give us a much tighter approximation. However, explicit splitting results in a high computation time as the time scales linearly with the number of splits. To efficiently approximate this function, we can instead make the splits to get explicit bounds on each subinterval and then run them through certification simultaneously (i.e., implicit splitting as shown in Fig. 10.2(c)). As we observe in Fig. 10.2(c), splitting into 20 implicit parts gives a very good approximation with very little overhead (the number of certification cycles used is still the same).

## 10.4 Empirical comparison

Following Mohapatra et al. (2020), we conduct extensive experiments for all the continuously parametrized semantic attack threat models presented in this chapter. The verification of discretely parameterized semantic perturbations can be straightforward using enumeration. We apply Semantify-NN to \( \ell_p \)-norm verification algorithms proposed by Zhang et al. (2018) and Boopathy et al. (2019) to certify multilayer perceptron (MLP) models and convolutional neural network (CNN) models.

- **Baselines.** We calculate the upper and lower bounds for possible value ranges of each pixel \( x_i \) of the original image given perturbation magnitude in the semantic space. Then we use an \( \ell_\infty \)-norm-based verifier to perform bisection on the perturbation magnitude and report its value. We show that directly converting the perturbation range from semantic space to original RGB space and then applying \( \ell_p \)-norm-based verifiers give very poor results in all tables. We also give a weighted-\( \epsilon \) version, where we allow for different levels of perturbation for different pixels.

![](img/fa92deee3de0f00ea56e92ca0b92c8e4_120_0.png)

(a) Explicit splitting

![](img/fa92deee3de0f00ea56e92ca0b92c8e4_120_1.png)

(b) Implicit splitting

Figure 10.3 Illustration of refinement techniques.

- Attack. We use a grid-search attack with the granularity of the order of the size of the subintervals after input splitting. Although this is not the optimal attack value, it is indeed an upper bound for the minimum adversarial perturbation. Increasing the granularity would only result in a tighter upper bound and does not affect the lower bound (the certificate we deliver).

- Semantify-NN: We implement both SP-layers (SPL) and with refinement (SPL+Refine).

The SP-layers are added as fully connected layers for MLPs and as modified convolution blocks for CNN models (we allow the filter weights and biases to be different for different neurons). We evaluate Semantify-NN and other methods on MLP and CNN models trained on the MNIST, CIFAR-10 and GTSRB (German Traffic Sign Benchmark) datasets. We use the released MNIST and CIFAR models, and their standard test accuracy of MNIST/CIFAR models are 98–99%/60–70%. We train the GTSRB models from scratch to have 94–95% test accuracies. All CNNs (LeNet) use 3-by-3 convolutions and two max pooling layers and along with filter size specified in the description for two convolution layers each. LeNet uses a similar architecture to LeNet-5 (LeCun et al., 1998), with the no-pooling version applying the same convolutions over larger inputs. We also have two kinds of adversarially trained models. The models (denoted as sem adv in the table) are trained using data augmentation where we add perturbed images (according to the corresponding threat model) to the training data. The models denoted as $\ell_\infty$ adv are trained using the $\ell_\infty$ norm adversarial training method (Madry et al., 2018). We evaluate all methods on 200 random test images and random targeted attacks. We train all models for 50 epochs and tune hyperparameters to optimize validation accuracy.

Experiment (1): HSL space perturbations. Table 10.1 demonstrates that using $\ell_p$-norm-based verification results in extremely loose bounds because of the mismatch in the dimensionality of the semantic attack and dimensionality of the induced $\ell_p$-norm attack. Explicitly introducing this dimensionality constraint by augmenting the neural networks with our proposed SP-layers gives a significant increase in the maximum certifiable lower bound, resulting in 4–50× larger bounds. However, there is still an apparent gap between the Semantify-NN’s certified lower bound and attack upper bound. Notably, we observe that adding input-space refinements helps us to further tighten the bounds, yielding an extra 1.5–5× improvement. This corroborates the importance of input splitting for the certification against semantic attacks. The transformations for HSL space attacks are fairly linear, so the gap between our certified lower bound and attack upper bound becomes quite small.
