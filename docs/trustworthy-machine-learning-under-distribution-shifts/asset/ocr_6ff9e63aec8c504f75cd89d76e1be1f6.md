objective is:

$$\mathcal{L}_{pos} = \mathcal{L}_d(g_c(\mathbf{x}; 	heta_c), g_c(\mathbf{x} + \mathbf{e}; 	heta_c)) - \mathcal{L}_{cc}(f_s(g_s(\mathbf{x} + \mathbf{e}); \phi_s), d),$

where the first term $\mathcal{L}_d(\cdot)$ indicates the distance measured between the contents extracted from the original instance and its perturbed version, and the second term $\mathcal{L}_{cc}(\cdot)$ denotes the cross-entropy loss. By minimizing $\mathcal{L}_{pos}$, the perturbation $e$ would not significantly affect the content feature, while introducing a novel style that is distinct from its original domain $d$. Consequently, the augmented data with novel styles can be utilized to train a style-invariant model that is resistant to domain shift. Moreover, a specific style with domain $d'$ can be injected by modifying $\mathcal{L}_{pos}$ as:

$$\mathcal{L}_{pos} = \mathcal{L}_d(g_c(\mathbf{x}; 	heta_c), g_c(\mathbf{x} + \mathbf{e}; 	heta_c)) + \mathcal{L}_{cc}(f_s(g_s(\mathbf{x} + \mathbf{e}); \phi_s), d').$$

Different from Equation (2.7), we hope to minimize the cross-entropy loss that the perturbed instance can contain the style information from a target domain $d'$. As a result, the augmented data can successfully bridge the gap between source domain and target domain, and further improve the test performance in the target distribution.

As negative data augmentation, the intervention objective is defined as:

$$\mathcal{L}_{neg} = \mathcal{L}_d(g_s(\mathbf{x}; 	heta_s), g_s(\mathbf{x} + \mathbf{e}; 	heta_s)) - \mathcal{L}_{cc}(f_c(g_c(\mathbf{x} + \mathbf{e}); 	heta_c), y).$$

By minimizing $\mathcal{L}_{neg}$, the perturbation would not greatly change the style information but deviate the content from its original with class label $y$. Subsequently, recognizing the augmented data as unknown, the trained model would be robust to deforming anomalies with familiar styles, boosting the OOD detection performance.

To accomplish the adversarial data augmentation process, we perform multi-step perturbed gradient descent. Formally, the optimal $\mathbf{x}$ and $	ilde{\mathbf{x}}$ are iteratively found:

$$\mathbf{x}^{t+1} = \tilde{\mathbf{x}}^t + \text{arg min}_{\mathbf{e} : ||\mathbf{e}||_p < \epsilon} \mathcal{L}_{pos}(	ilde{\mathbf{x}}^t + \mathbf{e}), \tilde{\mathbf{x}}^{t+1} = \tilde{\mathbf{x}}^t + \text{arg min}_{\mathbf{e} : ||\mathbf{e}||_p < \epsilon} \mathcal{L}_{neg}(	ilde{\mathbf{x}}^t + \mathbf{e}).$$

where the final iteration $t$ is set to 15 in practice. Further, the optimal augmented data will be incorporated into model training, which is described in the next section.