
gradient-based white-box attacks for generating adversarial examples in the black-box setting.

The ZOO attack finds the adversarial example by also solving the optimization problem (1.3.19). Motivated by the attack loss functions (1.3.6.2) used in the C&W attack, a new hinge-like loss function [35] based on the log probability score vector of the model $f$, instead of $Z$, is proposed as follows:

where is the element of the probability score vector, and the parameter ensures a constant gap between the log probability score of the adversarial example classified as class $t$ and all remaining classes. The log probability score is used instead of a probability score since well-trained DNNs yield a significant high confidence score for a class compared to other classes, and the log function lessens this dominance effect without affecting the order of confidence score. The ZOO attack is defined as follows.

**Definition 11 (ZOO Adversarial Attack by Chen et al. 2017):** A ZOO attack is a score-based black-box attack that generates the adversarial example by solving the following optimization problem using the zeroth-order stochastic coordinate descent with a coordinate-wise ADAM.

subject to the constraint

In the white box setting, finding an adversarial example requires taking the gradient of the model function. However, in the black-box setting, the gradient is inadmissible, and one can use only the function evaluation which makes it a zeroth-order optimization problem. Chen et al. [35] provided a method for estimating the gradient information surrounding the victim sample by watching variations in prediction confidence when the coordinate values of are adjusted [36]. Chen et al. [35] used the following symmetric difference quotient to approximate the gradient:

(1.4.2)

where h is a small constant, and is a standard basis vector. For networks with a large input size e.g., Inception-v3 network [11] with the number of model queries per gradient evaluation is (two function evaluations per coordinate-wise gradient estimation). This is very query inefficient.

To overcome this inefficiency, Chen et al. [29] proposed the five acceleration techniques.

- 1. Use zeroth-order stochastic coordinate descent with a coordinate-wise ADAM to minimize the objective function.
- 2. Evaluate the objective function in batches instead of one by one to take advantage of the GPU.
- 3. Reduce the attack space and perform the gradient estimation from a dimension-reduced space where to improve computational efficiency: specifically, a dimension reduction transformation such as where is used to reduce the attack space. For instance, D can be an upscale operator that scales up an image, such as the bilinear interpolation method, discrete cosine transformation (DCT), or an autoencoder for attack dimension reduction [37]. Although this attack space dimension reduction method reduces the computation costs for high-resolution image datasets (such as ImageNet [38]), the reduced attack space also limits the ability to find a valid attack.
- 4. Use hierarchical attack to overcome the limited search space issue. Instead of just one transformation, a series of transformations with dimensions where are used to find the adversarial example. Starting with the small attack space attackers try to find an adversarial example. If they are unsuccessful, then they increase the attack space to Otherwise, the process stops.
- 5. Choose which coordinates to update based on their “importance.” For instance, the pixel near the edge or corner of an image is less important than a pixel near the main object (usually near center) for an image classifier. Chen et al. [35] divided an image into regions and defined the “importance” as the absolute pixel values change in each region.

Note that acceleration techniques 3–5 are not required when n is small. For instance, Chen et al. [35] did not use techniques 3–5 for the MNIST and CIFAR10 dataset. Although the attack success rate is comparable to the success rate of the C&W attack, the number of required queries is large for gradient estimation despite the proposed acceleration techniques.

## Square Attack

Andriushchenko et al. [26] proposed a square attack (SA), a query-efficient attack on both and -bounded adversarial perturbations. The SA is based on a random search (RS), an iterative technique in DFO methods. Therefore, the SA is a gradient-free attack [39], and it is resistant to gradient masking. SA improves the query efficiency and success rate by employing RS and a task-specific sampling distribution. In some cases, SA even competes with white-box attacks’ performance.

Compared to an untargeted attack, SA is targeted to find a -norm bounded adversarial example by solving the following box-constrained optimization problem:

subject to is a margin-based loss function measuring the level of(1.4.3) confidence with which the model f labels an adversarial input the ground-truth class y over other classes.

In a targeted attack with target class t, an attacker could simply minimize the loss function

However, a cross-entropy loss of the target class t (1.4.4)

is used to make the targeted attack more query efficient. (1.4.5)

This optimization problem can be solved by using the classical RS method. In general, the RS method can be described as follows. Given an objective function g to minimize, a starting point and a sampling distribution D, the RS algorithm outputs an estimated solution after N iterations. For each iteration i, the RS algorithm starts with a random update and then adds this update to the current iteration; i.e., If the objective function evaluated at is less than the best obtained so far, we update and That is, if then and Otherwise, the update is discarded [40]. This process stops after a user-specified number of iterations has been reached. Thus using RS to optimize g does not rely on the gradient of g.

Since Moon et al. [41] showed that when one runs the white-box PGD attacks until convergence on CIFAR10 and ImageNet datasets, the successful adversarial perturbation is mainly found on vertices (corners) of -norm ball [26]. Based on this observation, the SA attack only searches over the boundaries of the or -ball to obtain the potential adversarial perturbation of the current iterate Hence, the perturbation for each pixel (before projection) is either or for the -norm attack, where the perturbation of zero means no perturbation for a given pixel. This critical design makes the SA mechanism different from the standard RS algorithm, and it significantly improves the query efficiency.

Another key difference is that at each step the SA attack limits the modification of the current iterate by updating only a small fraction (a square of side length for each color channel) of the neighboring pixels of This helps reduce the dimension of the search space, especially when the input space is high-dimensional, e.g., n = in the ImageNet dataset [42].

In summary, the SA via random search consists of the following main steps for each iteration i[40]:

- 1. Find the side length of the square by determining the closest positive integer to where is the percentage of pixels of the original image x that can be perturbed and w is the width of an image. p gradually decreases with the iterations, but for the -norm SA. This mimics the step size reduction in gradient-based optimization, in which we begin with initial large learning rates to quickly shrink the loss value [40].
- 2. Find the location of the square with side length for each color channel by uniformly random selection. The square denotes the set of pixels that can be modified.
- 3. Uniformly assign all pixels’ values in the square to either or for each color channel c.
- 4. Add the square perturbation generated in step 3 to the current iterate to obtain the new point
- 5. Project onto the intersection of and the -norm ball of radius to obtain
- 6. If the new point attains a lower loss than the best loss so far, the change is accepted, and the best loss is updated. Otherwise, it is discarded.
