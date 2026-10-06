
## Uncertainty Estimation in Classification

![](img/f01928df50903c99ce023dd3c527a33d_812_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_812_1.png)

- When the classification network is sure about what it sees, it assigns a high probability to the class

Source: https://www.inovex.de/de/blog/uncertainty-quantification-deep-learning/

## Uncertainty Estimation in Classification

Do not mistake output probability for model certainty!

![](img/f01928df50903c99ce023dd3c527a33d_813_0.png)

- The output probabilities will be unreliable if the input is very different than training

## Distribution shift

- The main problem is the distribution shift
- i.e. we ask the network for data it has not been trained on (out of distribution samples)
- Neural networks often produce wrong answers
- However... they are really confident about it

## Typical behavior: DNNs are overconfident

- Example: CIFAR 100
- Predict 100 different classes from an image
- Predictions typically also come with a confidence level

![](img/f01928df50903c99ce023dd3c527a33d_814_0.png)

## Overconfidence in Deep Learning

Lets apply different noise levels during testing (i.e. out of distribution)

![](img/f01928df50903c99ce023dd3c527a33d_815_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_815_1.png)

![](img/f01928df50903c99ce023dd3c527a33d_815_2.png)

![](img/f01928df50903c99ce023dd3c527a33d_815_3.png)

**Confidence:** How confident the neural network is (on average)
**Accuracy:** What is the actual prediction error?

**Observations:**

- There is always a gap between confidence and accuracy (this gap is called calibration)
- This gap typically becomes bigger for a bigger distribution shift

## Calibration for Deep Learning

A network is well calibrated if predictions with a certain confidence probability are accurate with the same probability, i.e.,

$p(\hat{y} = y|conf(x) = p) = p, \quad \forall p \in [0, 1]$

## Confidence plots:

![](img/f01928df50903c99ce023dd3c527a33d_816_0.png)

## Types of Uncertainty

| Ground truth | Prediction | Confidence interval | Observations |
| :--- | :--- | :--- | :--- |
| Observed domain | Unobserved domain | | |

## Predictive uncertainty

### Aleatoric uncertainty
Data uncertainty

### Epistemic uncertainty
Model uncertainty

![](img/f01928df50903c99ce023dd3c527a33d_817_0.png)

Source: https://www.biorxiv.org/content/10.1101/2020.08.11.247072v1.full.pdf

## Aleatoric vs. Epistemic Uncertainty

![](img/f01928df50903c99ce023dd3c527a33d_818_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_818_1.png)

Credits: http://introtodeeplearning.com

Gerhard Neumann | Machine Learning | KIT | SS2024 14

## Applications of uncertainty

## Uncertainty

## Safety

## Active Learning

## Reinforcement Learning

## Trustworthy ML/DL

## Bayesian Optimisation

Better decision making: Calculating the risk vs reward associated with prediction (worst case vs average case)

Select new data where we can learn the most (epistemic uncertainty is high)

An uncertainty-aware model would let the agent know where it has a high chance of an undesired outcome

Knowing when to trust model's predictions, especially under dataset shift

Optimization of probability distribution to better estimate predictions.

## Bayesian Learning

## So far ... “Non-Bayesian” Learning

- We mainly considered algorithms that optimize a single model using a given loss
- The algorithms do not know what they really know... and what is uncertain

- However, ...
- As the data is noisy, the estimated optimal parameter vector $\theta^*$ is also uncertain
- i.e. parameters are just random variables
- So far not really know how wrong / uncertain our estimate $\theta^*$
- We have also seen that multiple models (ensembles) work better!
- Prediction might be arbitrary wrong far from the data
- And we do not know when this is case

## Bayesian Learning - Motivation

Most algorithms can be reformulated in Bayesian way

- Idea: Estimate uncertainty in $\theta^*$
- Use this uncertainty estimate to quantify uncertainty of the prediction
- Find a more robust predictor by averaging over “plausible” predictors that are supported by the training data
- Each predictor is weighted by the probability of “right”
- Quantify epistemic (model) uncertainty
- Predictors will agree on test inputs close to the training data
- But disagree on inputs farther from the training data
- Bayesian Deep Learning can considerably outperform standard learning
- Similar benefits as ensembles... less variance/overfitting, small bias
- In their generalization capability and “calibration”

## Learning Outcomes

What will we learn today?

- Understand the “Bayesian formulation” of machine learning
- What are 2 basics steps for Bayesian learning
- What are the advantages of being “Bayesian”?
- For which representations can Bayesian learning be done in closed form?
- How to compute the posterior and predictive distribution for Bayesian Regression?
- How to compute the posterior and predictive distribution for Gaussian Processes?

## Today’s Agenda!

## Bayesian Learning:

- Posterior and Predictive Distribution
- Bayesian estimation for Gaussians
- Maximum A posteriori (MAP) Estimates

## Basics:

## Gaussian Identities:

- Completing the Square
- Gaussian Bayes Rules
- Gaussian Propagation

## Bayesian Algorithms:

- Bayesian Linear Regression
- Gaussian Processes

## Bayesian Learning

2 Steps:

1. Compute parameter posterior
2. Compute predictive distribution

## 1-step: Compute posterior

Compute the probability of “being right” for a parameter $\theta$ using Bayes theorem:

![](img/f01928df50903c99ce023dd3c527a33d_826_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_826_1.png)

- Prior: Can encode our subjective belief
- Posterior: Probability of parameter vector given the data
- Likelihood: Specified by our model $\mathcal{D}$
- Evidence: Normalization, can be used for model comparison (later)

## 2-step: Compute predictive distribution

Predicting a new data-point $x^*$:

$p(y^*|x^*, \mathcal{D}) = \int p(y^*|x^*, \theta) p(\theta|\mathcal{D}) d\theta \approx \frac{1}{N} \sum_{\theta_i \sim p(\theta|\mathcal{D})} p(y^*|x^*, \theta_i)$
$\text{marginal likelihood} \quad \text{likelihood} \quad \text{posterior}$

- Parameter vector $\theta$ is integrated out
- Likelihood $p(y^*|x^*, \mathcal{D})$ is now purely determined by the data $\mathcal{D}$
- $p(y^*|x^*, \mathcal{D})$ is often called marginal likelihood as $\theta$ is marginalized out

**Intuition:** If you assign each parameter estimator a “probability of being right”, the average of these parameter estimators will be better than the single one

- Weighted ensemble method (with potentially infinite amount of models if integral can be solved exactly)
- ..., samples from $p(\theta|\mathcal{D})$ are used to approximate the integral (finite number of models in this case)

## Example:

## Bayesian Linear Regression
(math comes later...)

## Observation:

- The posterior becomes more narrow with more data

![](img/f01928df50903c99ce023dd3c527a33d_828_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_828_1.png)

![](img/f01928df50903c99ce023dd3c527a33d_828_2.png)

![](img/f01928df50903c99ce023dd3c527a33d_828_3.png)

![](img/f01928df50903c99ce023dd3c527a33d_828_4.png)

![](img/f01928df50903c99ce023dd3c527a33d_828_5.png)

![](img/f01928df50903c99ce023dd3c527a33d_828_6.png)

![](img/f01928df50903c99ce023dd3c527a33d_828_7.png)

![](img/f01928df50903c99ce023dd3c527a33d_828_8.png)

$p(\theta|\mathcal{D})$

Samples from posterior

Posterior integrated out

## Function View

- Each parameter sample represents a function
- More uncertainty when functions disagree

![](img/f01928df50903c99ce023dd3c527a33d_829_0.png)

training data — predictions (mean)

Gerhard Neumann | Machine Learning | KIT | SS2024
