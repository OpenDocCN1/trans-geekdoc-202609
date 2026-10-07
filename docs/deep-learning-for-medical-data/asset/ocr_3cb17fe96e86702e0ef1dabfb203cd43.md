# 58 | GREEDY INFOMAX

| Pretraining Type | CPC | Supervised |
|---|---|---|
| Greedy InfoMax | Greedy Supervised | Random int |

![](bbox=[0.245, 0.142, 0.658, 0.305])

**Figure 5.4:** Speaker Classification error rates on a log scale (layers 1 to 5), as well as the final representation created by the autoregressive layer (corresponding to the results in table 5.3).

tasks. For the phone classification task, we see a steady decline of the performance when we reduce the modeling of temporal dependencies, indicating their importance for solving this task. When classifying the speaker identity, reducing the modeling of temporal dependencies in the ablated models barely influences their performance.

With the image classification results from Section 5.4.1, where no autoregressive model was employed either, this indicates that the GIM performs best on downstream tasks where temporal or context dependencies do not to be modeled by an autoregressive module. In these settings, GIM can outperform the CPC model, which makes use of end-to-end backpropagation, a global objective, and BPTT.

# **INTERMEDIATE MODULE REPRESENTATIONS**

The greedy-wise training of GIM allows us to train arbitrarily models without ever running into a memory constraint. We investigate how the created representations develop in each individual module by training a linear classifier on top of each module and measuring their performance on the speaker classification task. With results presented in Figure 5.4, we first observe that each GIM improves upon the representations of its predecessor. Interestingly, CPC exhibits similar performance in intermediate modules despite these modules relying solely on the error signal from the global loss function on the last module. This is in stark contrast with the supervised end-to-end model, whose intermediate