# TASK COMPOSITIONALITY IN WEIGHT SPACE

![](bbox=[0.373, 0.073, 0.703, 0.223])

Figure 32: Single-task accuracies of nonlinear FT, f(; θ*) and linearly FT, $fin(; 	heta_{lin})$, models.

linearization. In Figure 32, we observe that linearized fine-tuning significantly reduces the advantage of nonlinear models, and in most cases the performance of $f_{lin}(; \theta_0 + \tau)$ is very similar to the one of $f(; \theta_0 + \tau)$ (cf. Figure 29).

Remarkably, as we show in Section G.3, this increase in single-task performance does not compromise weight disentanglement, which remains as high as for the post-hoc linearized models in Figure 30. As result, linear fine-tuning allows improved arithmetic compared to standard nonlinear fine-tuning. In particular, Table 5-6 in their last rows show linearized fine-tuned models significantly outperform their nonlinear counterparts and state-of-the-art results on the task addition and negation benchmarks [Ill+23]. The linearized fine-tuned models achieve higher multi-task accuracies through task addition (up to 5.8 points more) and can forget more through task negation (up to 13.1 points more) while maintaining a similar level of accuracy on the control task. Additionally, we observe that the advantage of the linearized models over the nonlinear ones is higher for the smaller Vit-B/32 and progressively diminishes as the model size increases to Vit-L/14.

In general, thanks to the efficiency of the Jacobian-vector product implementations in most deep learning frameworks [NSDS22], training and inference in linearized neural networks only require $O(1)$ increase in computational costs with respect to their nonlinear counterparts. In this regard, the superiority of task arithmetic of linearized models can make this technique appealing for practical applications. Identifying the right trade-offs between computational cost and performance, as well as faster linearization techniques, is an exciting avenue for future work.

# 8.5 TOWARDS UNDERSTANDING TASK ARITHMETIC

We conclude by providing further fundamental insights that can aid our understanding of task arithmetic. In particular, we ask whether any kernel can satisfy Property 1, and we establish a connection