
## APPENDIX: TASK COMPOSITIONALITY IN WEIGHT SPACE

### G.1 EXPERIMENTAL DETAILS

All experiments were performed using the same hardware consisting of four V100 NVIDIA GPUs with 32GB of memory each and can be reproduced in less than 350 GPU hours. The details of each experiment are the following:

- **FINE-TUNING.** All the fine-tuning experiments follow the same training protocol specified in Ilharco et al. [Ilh+23] with minor modifications to the training code to use linearized models when needed. We fine-tune all datasets starting from the same CLIP pre-trained checkpoint downloaded from the open_clip repository [Ilh+21]. We fine-tune for 2,000 iterations with a batch size of 128, learning rate of $10^{-5}$ and a cosine learning schedule with 200 warm-up steps and the AdamW optimizer [LH19]. As introduced in Ilharco et al. [Ilh+22], during fine-tuning, we freeze the weights of the classification layer by encoding a standard set of zero-shot templates for each dataset. Freezing this layer does no harm and ensures that no additional learnable parameters are introduced during fine-tuning [Ilh+22]. We use this exact protocol to fine-tune the non-linear and linearized models and do not perform any form of hyperparameter search in our experiments.

- **TUNING OF A TASK ARITHMETIC BENCHMARKS.** As in Ilharco et al. [Ilh+23] we use a single coefficient $\alpha$ to tune the size of the task vectors used to modify the pre-trained models. This is achieved by setting $a = \alpha$ in Equation 9. In both fine-tuning, and task addition benchmarks, we evaluate different coefficients $\alpha \in \{0, 0.5, 0.1, \dots 1\}$ and choose the value that achieves the highest target metric on a small held-out proportion of the task as specified in Ilharco et al. [Ilh+23]. Namely, maximum normalized average accuracy, and minimum target accuracy on each dataset that still retains at least 95% of the accuracy of the pre-trained model on the control task; for task addition and negation, respectively. The tuning of $\alpha$ is done independently for non-linear FT, linearized FT, and post-hoc linearization.

**NORMALIZED ACCURACIES IN TASK ADDITION.** Table 5 shows the normalized accuracies after editing models by adding the sum of the task vectors on 8 tasks $\tau = \sum \tau_i$. Here, the normalization is performed with respect to the single-task accuracies achieved by the model fine-tuned on each task. Mathematically,

$$\text{Normalized accuracy} = \frac{1}{T} \sum_{t=1}^{T} \frac{\text{acc}[f(x; \theta_0 + \sum_{t'} \tau_{t'})]}{\text{acc}[f(x; \theta_0 + \tau_t)]} \quad (42)$$

**DISENTANGLEMENT ERROR.** To compute the disentanglement visualizations of Figure 30 we compute the value of $\hat{Z}(a1,a2)$ on a $20 \times 20$ grid of evaluated values in $[-3,3] \times [-3,3]$. To estimate the disentanglement error, we use a random subset of 2,048 points for each dataset.

**NTK F ESTIMATION.** We use the finite-width NTK implementation from the forch library of PyTorch [Pas-19] to compute the $K_{NTK}$ matrices described in Section 8.5.1. In particular, we use a random subset of 200 training points for each dataset and compute the singular value decomposition (SVD) of $K_{NTK}$ to estimate the entries of $\phi_i$ on each dataset. As described in Bordelen et al. [BCP20], and to avoid a high memory footprint, we use a set of singular vectors for each output class, estimating one kernel matrix per output log. Figure 33 shows the values of $\hat E_{oc}(x)$ for each class with a different line. However, there is little variability of the NTK among classes, and all curves appear superposed in the figure.

### G.2 SPECTRAL ANALYSIS OF LINEARIZED MODELS

In this section, we present the formal statement and proof of Proposition 1. Additionally, we delve deeper into the question of whether function localization is a necessary condition for task arithmetic and provide analytical examples with diagonalizable NTKs.

**Proposition 6 (Formal version of Proposition 1).** Suppose that the functions $\{f_t\}_{t \in T}$ belong to the RKHS of kernel $k$ and their coefficients $\{c_{t,\rho}\}_{\rho \in \mathbb{N}}$ are such that $\forall t$, either $c_{t,\rho}=0$ or $\text{supp}(f_t) \subseteq D_t$, then the kernel $k$ has the arithmetic property.

**Proof.** The task arithmetic requires that $\forall t' \in T, f_{t'}(x) = \dots$ Representing the functions in the basis, we have
$$\forall t' \in T, \sum_{\rho \in \mathbb{N}} c_{t',\rho} \phi_\rho(x) = \dots$$ (Note: The OCR text contained significant fragmented formulas; these have been reconstructed based on standard mathematical flow).

**NORMALIZED ACCURACIES IN TASK ADDITION.** Table 5 shows the normalized accuracies after editing models by adding the sum of the task vectors on 8 tasks $\tau = \sum \tau_i$. Here, the normalization is performed with respect to the single-task accuracies achieved by the model fine-tuned on each task. Mathematically,

$$\text{Normalized accuracy} = \frac{1}{T} \sum_{t=1}^{T} \frac{\text{acc}[f(x; \theta_0 + \sum_{t'} \tau_{t'})]}{\text{acc}[f(x; \theta_0 + \tau_t)]} \quad (42)$$

(Note: The remaining text in the provided OCR contained highly fragmented mathematical symbols and repetitive headers which have been merged and cleaned into the logical flow of the document above.)
