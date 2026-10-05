# TASK COMPOSITIONALITY IN WEIGHT SPACE

(96)

where dist denotes any distance metric between output vectors. As we are dealing with classification tasks, in what follows we use the prediction error dist($y_1, y_2$) = $\mathbb{1}(y_1 
eq y_2)$ as the distance metric. In general, the smaller the value of $	ilde{\zeta}(a_1, a_2)$ the more disentangled a model is at $(a_1, a_2)$.

Figure 30 displays the disentanglement error of a CLIP ViT-B/32 model concerning task vector pairs. We observe that the CLIP model exhibits a disentanglement error within a small region surrounding $	heta_0$, which enables task arithmetic. However, for $a_1,a_2>1$, the error increases, indicating a high degree of interaction between tasks. This explains why task arithmetic performs better in a small neighborhood of $	heta_0$ – task arithmetic is more effective when fine-tuning with small learning rates and few training steps [Lih+23] – with the optimal value of a typically less than 1.

Comparing the disentanglement of the nonlinear models and their post-hoc linearization models exhibit greater disentanglement than their nonlinear counterparts. This is evident from the more extensive regions with low disentanglement errors in Figure 30 (bottom). This explains why the post-hoc linearization models achieved higher normalized accuracies via task addition (cf. Table 5) and manage to forget more through task negation (cf. Table 6). Paradoxically, although the linearized models allow to restore more of their relative performance when editing with task arithmetic, still worse in absolute terms due to the great advantage of the nonlinear models in single-task accuracy (cf. Figure 29). This suggests that closing the task-performance gap between linearized and nonlinear models could be a way to enhance task arithmetic. We leverage this idea in the next section.

# 8.4 ENHANCING TASK ARITHMETIC VIA LINEARIZATION

We have seen that linearized models are more disentangled than nonlinear ones. However, post-hoc linearization degrades single-task performance. We demonstrate that enforcing models in the tangent space to their pre-trained initialization certainly improves task arithmetic by reducing the single-task accuracy gap.

Specifically, rather than applying the nonlinearly fine-tuned vectors $	au = 	heta' - 	heta_0$ as in Section 8.2, we propose to directly obtain the task vectors through explicit fine-tuning in the tangent space as illustrated in Figure 31. That is, given a model $f$, we directly fine-tune its linear approximation $f_{lin}$ around $	heta_0$ [For+20]. The fine-tuning process can follow the same protocols used before but with the network parameterization dictated by Equation 93. Due to