# G.3.3 Weigh disentanglement of linearized and random models

In Figure 78, we present the disentanglement error of a linearized CLIP VIT-B/32 model across three different dataset pairs. By comparing these results with Figure 30, we can clearly see that linearized models exhibit significantly more weight disentanglement compared to their non-linear counterparts, similar to the findings obtained for post-hoc linearization.

Conversely, in Figure 79, we showcase the disentanglement error of a CLIP VIT-B/32 model that was non-linearly fine-tuned starting from a random initialization. In all panels, we observe a high disentanglement error, which supports the claim that weight disentanglement and, consequently, task arithmetic are emergent properties of pre-training.

![](bbox=[0.267, 0.335, 0.823, 0.458])

Figure 78: Visualization of weight disentanglement from linearized models. The heatmaps show the disentanglement error $\xi(a_1, a_2)$ of a VIT-B/32 linearly fine-tuned on different example task pairs. The light regions denote areas of the weight space where weight disentanglement is stronger. The red box delimits the search space used to compute $a$ in our experiments.

![](bbox=[0.267, 0.577, 0.823, 0.701])

Figure 79: Visualization of weight disentanglement from random initialization. The heatmaps show the disentanglement error $\xi(a_1, a_2)$ of a VIT-B/32 fine-tuned from a random initialization non-linearly on different example task pairs. The light regions denote areas of the weight space where weight disentanglement is stronger. The red box delimits the search space used to compute $a$ in our experiments.