
## CHAPTER APPENDIX

## 6.A EFFECT OF HYPER-PARAMETERS ON COVERAGE:

The optimal configuration of hyper-parameters and bin priors have been determined using 700 evaluations using TPE. The space of parameters explored is as follows, presented in the hyperopt API for transparency:

```
# Shared
C: uniform(2, 10, 1) * 2 + 1,
dropout rate: uniform(0.01, .95),
lr: logiform(log(0.0001), log(0.01)),
batch_size: qloguniform(log(32), log(512), 1)
# SQUAD & Gaussian
kl_multiplier: logiform(log(1e-6), log(0.01)),
init_scale: logiform(log(1e-3), log(20)),
# SQUAD
use_bin_probs: choice(['uni', 'gaus']),
use_bins: choice(['equal_prob_gaus',
'linearly_spaced']),
learn_bin_values: choice([
'per_neuron', 'per_layer', 'fixed']),
```

In figure 6.A.1 we visualize the pairwise effect of these hyper-parameters on the coverage. The optimal configuration found in the main SQUAD model are: batch size: 244, KL multiplier: 0.0027, per layer, p(z): uniform, v: linearly spread over (-3.5,3.5), lr: 0.0008, C: 15, initialization scale: 3.214.

![](img/3013a5e7af0c305d337644a32207e3ef_97_0.png)

**Figure 6.7:** This figure serves to provide intuition on how a variety of distributions come about in our model. We show the set of weights used to predict the probability for the C bins of a randomly selected latent variable $z_{f=1,k=12}$ from the first layer in a converged 2-layer SQUAD model (reshaped to a 28x28 squares for comparison with the data). We then present 5 data-points for which the neuron predicts a stereotypical distribution, as visualized in the last bar-plot.

![](img/3013a5e7af0c305d337644a32207e3ef_98_0.png)

**Figure 6.A.1:** This figure visualizes the pairwise relationship between hyperparameters of SQUAD and the effect on coverage. The top-60 configurations are highlighted. Green values are good, red values are bad. We have filtered on the optimal settings for bin values and prior to reduce clutter.

## 7 CONCLUSION

In this thesis we revisited the core components of the deep learning toolkit and reevaluated them in the context of medical image image analysis. We identified three main areas where deep learning is falling short. In part I, we explored the benefit of integrating expert knowledge on structure and constraints in the model. Part II followed with a study on how deep learning modes can better leverage the vast amounts of unlabeled medical imaging data available. Finally, in part III, we explored how to extract better uncertainty estimates from the model to provide diagnostic risk. Let us now consider the research questions posed at the beginning of this work.

**Research Question 1**: Can roto-reflective equivariance improve accuracy and robustness of deep learning models in a large scale medical setting?

Certain medical imaging problems come with symmetry modes and nuisance factors found in the real world images typically studied in deep learning for computer vision. We explored this problem in the context of histopathology for the task of detecting metastatic tissue. Using the framework of CNNs, we designed a new architecture that captures the rotational symmetries of slide images. This new model outperforms traditional CNN architectures, even under strict equivalence of computational cost and parameter count. Moreover, the new model proved more robust to perturbations. We can conclude that in the right circumstances and especially in the face of limited data, incorporating expert knowledge in the form of model invariance improves the robustness and accuracy of deep learning models.

Looking forward, we consider that the research area of group equivariant neural networks have progressed since Cohen and Welling, 2016. Incorporating these novel methods to enable scale equivariance, continuous rotation equivariance and perhaps color equivariance, can potentially improve performance further. However, the effectiveness of integrating expert knowledge as priors in a deep learning model remains a point of contention. As discussed in the bitter lesson, Sutton, 2019, expert knowledge might hamper a deep learning model from discovering efficient solutions to a decision problem. General methods that benefit from scale in data and compute have historically outperformed custom methods. GPT-style language models contain little to no expertise from linguistics, and have proven to be highly effective. Incorporating invariants should be evaluated on a case-by-case basis. And as the size of models and datasets grows, we might find that they provide a diminishing impact on performance.

**Research Question 2:** How can we motivate the deep learning research community to optimize models for real medical problems?

To aid the study of deep learning for medical problems, we proposed PCAM, a dataset derived from Camel16. This dataset is structured similarly to typical deep learning benchmarks such as CIFAR-10. We demonstrate improvement on the PCAM benchmark. Since its release, PCAM has been the center of a Kaggle challenge, and the accompanying paper has been cited 175 times since. (Radford et al., 2021).

**Research Question 3:** Do medical imaging deep learning models benefit from contrastive representation?

Next, we studied how contrastive representation learn medical imaging. We found that CPC on its own performs well, but suffers from nuisance factors in medical images. By carefully incorporating a set of augmentations specific to the tasks, we found improved representations which translated to better prediction in both histopathology and X-ray data.

**Research Question 4:** Can we optimize deep learning models effectively?

As the scale of deep learning architecture grows, the cost of building the training infrastructure explodes. To enable gradient backpropagation across the full network, computational nodes need to be connected with high-bandwidth channels and physically colocated. We found that our proposed method, GIM, outperforms its supervised counterpart and enables training layers of a network in relative isolation.

**Research Question 5:** Can latent variable quantization enable more expressive mean-field posterior distributions?

Finally, we explored the problem of uncertainty. We considered the hypothesis that variational inference infers from a too restrictive class of approximate posterior functions. Based on this, we proposed a novel mean-field approximate posterior based on quantizing latent variables called SQUAD. We demonstrate that this posterior can be effectively trained in a DLVM setting, does not need batch norm, and yields quality that reduces risk.

Since this, the use of quantization as a way of modeling density over a continuous domain has taken off. Quantization such as the VQ-VAE (Oord et al., 2017b) has played a crucial role in the image generation tool DALL-E and quantile regression in reinforcement learning, Dabney et al., 2017b. This continues to be an interesting approach to approximate posterior modeling, and can be studied in a variety of variational inference settings.

The search for a proper Bayesian treatment of deep learning is ongoing. This area of research has fallen out of favor, as various studies to train deep learning models in a Bayesian manner reached negative conclusions (Wenzel et al., 2020). Only recently, Chen et al., 2024 demonstrate that with an adapted optimizer, achieving well-calibrated uncertainty from large probabilistic neural networks is possible.

## CLOSING WORDS

Deep learning brings a tremendously exciting realm of possibilities for the field of medical image analysis and medicine in general. Capturing expertise in statistical models enables humanity to improve diagnostic quality.
