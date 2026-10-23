# 19.4.4 Interactions between Learning and Inference

Using approximate inference as part of a learning algorithm affects the learning process, and this in turn affects the accuracy of the inference algorithm.

Specifically, the training algorithm tends to adapt the model in a way that makes the approximating assumptions underlying the approximate inference algorithm become more true. When training the parameters, variational learning increases

𝔼_{h~q} log p(v, h). (19.68)

For a specific v, this increases p(h | v) for values of h that have high probability under q(h | v) and decreases p(h | v) for values of h that have low probability under q(h | v).

This behavior causes our approximating assumptions to become self-fulfilling prophecies. If we train the model with a unimodal approximate posterior, we will obtain a model with a true posterior that is far closer to unimodal than we would have obtained by training the model with exact inference.

Computing the true amount of harm imposed on a model by a variational approximation is thus very difficult. There exist several methods for estimating log p(v). We often estimate log p(v; θ) after training the model and find that the gap with ℒ(v, θ, q) is small. From this, we can conclude that our variational approximation is accurate for the specific value of θ that we obtained from the learning process. We should not conclude that our variational approximation is accurate in general or that the variational approximation did little harm to the learning process. To measure the true amount of harm induced by the variational approximation, we would need to know θ* = max_θ log p(v; θ). It is possible for ℒ(v, θ, q) ≈ log p(v; θ) and log p(v; θ) ≪ log p(v; θ*) to hold simultaneously. If max_q ℒ(v, θ*, q) ≪ log p(v; θ*), because θ* induces too complicated of a posterior distribution for our q family to capture, then the learning process will never approach θ*. Such a problem is very difficult to detect, because we can only know for sure that it happened if we have a superior learning algorithm that can find θ* for comparison.

# 19.5 Learned Approximate Inference

We have seen that inference can be thought of as an optimization procedure that increases the value of a function ℒ. Explicitly performing optimization via iterative procedures such as fixed-point equations or gradient-based optimization is often very expensive and time consuming. Many approaches to inference avoid