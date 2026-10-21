The adversarial patch is therefore learned as

```
δ = arg min_δ 𝔼_{(x_k, x_{k+1})∼𝒳, l∼Ω, t∼𝒯} [ ((u, v)·(û, v̂)) / (‖(u, v)‖·‖(û, v̂)‖) ]  (15.3)
```

with

```
(u, v) = f(x_k, x_{k+1})  (15.4)
```

```
(û, v̂) = f(g(x_k, δ, l, t(δ)), g(x_{k+1}, δ, l, t(δ)))  (15.5)
```

where δ is the adversarial patch, l is the pixel location sampled over all the locations Ω in the image, g(·) is the operator that replaces the image pixels with the values of δ at the location l, t(δ) is a 2D transformation sampled from the set of transformations 𝒯 (or their combination) and applied to the adversarial patch δ, and (û, v̂) is the optical flow resulting from the images attacked with the adversarial patch.

OFA works with different types of optical flow models, such as classical (Epic Flow, LDOF), autoencoder-based architectures (FlowNet, FlowNet2), and image-pyramids-based architectures (SpyNet, PWC-Net, Back2Future), in a white-box scenario. In such a scenario, OFA learns a specific adversarial patch for each model independently and of different sizes, while a universal adversarial patch is learned from some of the models and applied to the input videos against other models in a black-box scenario. In both scenarios, the attack on autoencoder models impacts large image areas even with a small patch size (0.1% of the image resolution). Other types of models are instead more robust to such an attack.

# 15.7 Image classification

In this section, we discuss and categorize adversarial examples for image classification.

# 15.7.1 White-box, bounded attacks

White-box bounded attacks commonly generate the perturbations with an ℓ_p-norm constraint so that the distortion of the resulting adversarial example is imperceptible to humans.

L-BFGS (Szegedy et al., 2014) misleads a target classifier with adversarial examples that consist of imperceptible adversarial perturbations added to a normalized input x ∈ [0, 1]. The L-BFGS attack solves a constrained optimization problem whose goal is to find x̂ ∈ [0, 1] with an ℓ_2-norm constraint:

```
c‖x̂ − x‖₂ + ℒ(x̂, ŷ)  (15.6)
```

where c is a hyper-parameter and ℒ(x̂, ŷ) is the cross-entropy loss that measures the difference between the label y predicted by a target classifier from an adversarial input and the target mis-classification label ŷ. This loss encourages the attack to generate x̂ that can mislead the target classifier. The Carlini & Wagner (CW) attack (Carlini and Wagner, 2017) generates an ℓ_p-norm bounded perturbation by solving a constrained optimization problem, similarly