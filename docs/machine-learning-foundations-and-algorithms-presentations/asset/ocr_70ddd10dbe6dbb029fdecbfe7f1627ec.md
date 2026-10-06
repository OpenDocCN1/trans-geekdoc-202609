# Bayesian Learning - Motivation

Most algorithms can be reformulated in a Bayesian way

+   - Idea: Estimate uncertainty in $\theta*
- Use this uncertainty estimate to quantify uncertainty of the prediction
- Find a more robust predictor by averaging over “plausible” predictors that are supported by the training data
- Each predictor is weighted by the probability of being “right”

+   - Quantify epistemic (model) uncertainty
- Predictors will agree on test inputs close to the training data
- But disagree on inputs farther away from the training data

+   - Bayesian Deep Learning can considerably outperform standard deep learning methods
- Similar benefits as ensembles... less variance/overfitting, small bias
- In their generalization capability and their “calibration”