# 17.5.6 Connection with logistic regression

We have see that data points that are on the correct side of the decision boundary have ξₙ = 0; for the others, we have ξₙ = 1 − ŷₙ f(xₙ). Therefore we can rewrite the objective in Eq. (17.120) as follows:

ℒ(w) = Σₙ₌₁ᴺ ℓₕᵢₙgₑ(ŷₙ, f(xₙ)) + λ‖w‖²  (17.133)

where λ = (2C)⁻¹ and ℓₕᵢₙgₑ(y, η) is the hinge loss function defined by

ℓₕᵢₙgₑ(ŷ, η) = max(0, 1 − ŷη)  (17.134)

As we see from Fig. 4.2, this is a convex, piecewise differentiable upper bound to the 0-1 loss, that has the shape of a partially open door hinge.

By contrast, (penalized) logistic regression optimizes

ℒ(w) = Σₙ₌₁ᴺ ℓᵤ(ŷₙ, f(xₙ)) + λ‖w‖²  (17.135)

where the log loss is given by

ℓᵤ(ŷ, η) = −log p(y|η) = log(1 + e⁻ŷη)  (17.136)

This is also plotted in Fig. 4.2. We see that it is similar to the hinge loss, but with two important differences. First the hinge loss is piecewise linear, so we cannot use regular gradient methods to optimize it. (We can, however, compute the subgradient at ŷη = 1.) Second, the hinge loss has a region where it is strictly 0; this results in sparse estimates.

We see that both functions are convex upper bounds on the 0-1 loss, which is given by

ℓ₀₁(ŷ, y) = 𝕀(ŷ ≠ y) = 𝕀(ŷ y < 0)  (17.137)

These upper bounds are easier to optimize and can be viewed as surrogates for the 0-1 loss. See Sec. 4.3.2 for details.

# 17.5.7 Multi-class classification with SVMs

SVMs are inherently a binary classifier. One way to convert them to a multi-class classification model is to train C binary classifiers, where the data from class c is treated as positive, and the data from all the other classes is treated as negative. We then use the rule ŷ(x) = arg max_c f_c(x) to predict the final label, where f_c(x) = log[p(c=1|x)/p(c=0|x)] is the score given by classifier c. This is known as the one-versus-the-rest approach (also called one-vs-all).

Unfortunately, this approach has several problems. First, it can result in regions of input space which are ambiguously labeled. For example, the green region at the top of Fig. 17.18(a) is predicted to be both class 2 and class 1. A second problem is that the magnitude of the f_c's scores are not calibrated with each other, so it is hard to compare them. Finally, each binary subproblem is likely to suffer from the class imbalance problem (Sec. 10.3.8.2). For example, suppose we have 10