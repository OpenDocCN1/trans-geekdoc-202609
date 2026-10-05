# 8.2 TASK ARITHMETIC IS NOT A CONSEQUENCE OF LINEAR-TUNING

Table 5: Task addition. Average absolute (%) and normalized accuracies (%) of different CLIP ViTs edited by adding the sum of the task vectors of 8. We report results for the nonlinear and linearized models of Section 8.2 and 8.4 normalizing performance by their single-task accuracies.

| Method | ViT-B/32 | ViT-L/14 |
|---|---|---|---|--|
| | Abs. (↑) | Norm. (↑) | Abs. (↑) | Norm. (↑) |
| Pre-trained | $f(:; \theta)$ | 48.4 | - | 64.4 | - |
| Non-lin. FT | $f(:; \theta_0 + \tau)$ | 71.4 | 76.5 | 85.1 | 88.8 |
| Post-hoc lin. | $f_{lin}(; \theta_0 + \tau)$ | 57.1 | 81.9 | 75.2 | 90.0 |
| Linear. FT | $f_{lin}(; \theta_0 + \tau_{lin})$ | 76.5 | 85.4 | 88.5 | 93.5 |

Table 6: Task negation. Minimum accuracy (%) of different CLIP ViTs edited by adding a task vector from a task while retaining 95% of their performance on the control task. We report average performances over eight tasks on nonlinear and linearized models as introduced in Section 8.2 and 8.4.

| Method | ViT-B/32 | ViT-L/14 |
|---|---|---|---|--|
| | Targ. (↓) | Cont. (↑) | Targ. (↑) | Cont. (↑) |
| Pre-trained | $f(:; \theta)$ | 48.4 | 63.4 | 64.4 | 75.5 |
| Non-lin. FT | $f(:; \theta_0 - \tau)$ | 24.0 | 60.7 | 18.0 | 72.5 |
| Post-hoc lin. | $f_{lin}(; \theta_0 - \tau)$ | 14.8 | 60.3 | 12.1 | 71.8 |
| Linear. FT | $f_{lin}(; \theta_0 - \tau_{lin})$ | 10.9 | 60.8 | 7.9 | 72.5 |

and RESISC45 [CHL17]. We observe that the single-task performance of $f_{lin}(; \theta')$ is significantly lower than that of $f(:; \theta')$ for ViTs of all sizes. A nonlinear advantage [For+20] is a clear sign that fine-tuning has not appeared in a linear regime as shown by Wortsman et al. [Wor22b].

Yes, this observation is not enough to rule out that task arithmetic can be explained by linearizing the network function. Even if the nonlinear components are important for single-task performance, they might not be used during task arithmetic, which is the objective of this task. To show, the tangent space could be the only useful component.

We now show this is also not the case, as doing task arithmetic with nonlinearly fine-tuned task vectors over $f_{lin}$ decreases performance. To show this, we employ the benchmark posted in Ilharco et al. [Ilh+23] to evaluate the task arithmetic ability