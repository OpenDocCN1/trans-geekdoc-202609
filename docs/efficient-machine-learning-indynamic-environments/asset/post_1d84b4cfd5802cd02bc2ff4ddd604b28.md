
![](img/32fe6d02b4faa69c4646a6e93e0375fc_36_0.png)

![](img/32fe6d02b4faa69c4646a6e93e0375fc_36_1.png)

![](img/32fe6d02b4faa69c4646a6e93e0375fc_36_2.png)

![](img/32fe6d02b4faa69c4646a6e93e0375fc_36_3.png)

![](img/32fe6d02b4faa69c4646a6e93e0375fc_36_4.png)

![](img/32fe6d02b4faa69c4646a6e93e0375fc_36_5.png)

![](img/32fe6d02b4faa69c4646a6e93e0375fc_36_6.png)

![](img/32fe6d02b4faa69c4646a6e93e0375fc_36_7.png)

Figure 2.3: Accuracy vs. inference-time. Inference time is reported as a fraction of teacher's inference time on the x-axis along with average ensemble accuracy and error bars (y-axis). B-DISTIL performs this trade-off at runtime. For the baseline NO-RESHED, at inference time \(\tau_w\) on the x-axis, the y-axis denotes the accuracy of a best single model that is allowed \(|\tau_w - 0|\) time for inference. Similarly, for the baseline RESHED, at \(\tau_w\), y-axis is the accuracy of an ensemble of models, where the model \(w\) is allowed \(|\tau_w - \tau_{w-1}|\) time to perform its inference. This is also the latency between the successive predictions from B-DISTIL. We can see that B-DISTIL (green) remains competitive to the oracle baseline (NO-RESHED, blue) and outperforms weighted averaging (RESHED, yellow).

is usually only available after the execution is finished or is interrupted. Under this assumption, we can essentially pick the best models at various inference time constraints, e.g., by keeping a Pareto-frontier of models, and picking the one that fits the current inference budget. We refer to this baseline as NO-RESHED and compare B-DISTIL to it on both synthetic and real-world datasets in Figure 2.3. This idealized baseline is an upper bound on the accuracy of B-DISTIL for a fixed inference budget.

B-DISTIL can improve on its initial prediction whenever inference jobs are allowed to be rescheduled. To contextualize this possible improvement, we consider the case where the execution is interrupted and rescheduled (with zero-latency, for simplicity) at times \(\{\tau_1, \tau_2, \dots, \tau_W\}\). We are required to output a prediction at each \(\tau_w\). As an idealized baseline, assume we know these interrupt points in advance. One possible solution then is as follows: select models with inference budgets \(|\tau_1|, |\tau_2 - \tau_1|, \dots, |\tau_w - \tau_{w-1}|\). Sequentially evaluate them and at each interrupt \(\tau_w\), and output the (possibly weighted) average prediction of the \(w\) models. We call this baseline RESHED. Since the prediction at \(\tau_w\) is a weighted average of models, we expect its performance to serve as a lower-bound for the performance of B-DISTIL (Figure 2.3).

| Dataset | Algorithm | T = 50% | | T = 75% | | T = 100% |
|---|---|---|---|---|---|---|
| | | Acc (%) | Frac | Acc (%) | Frac | Acc (%) |
| Google-13 | E-RNN | 88.31 | 0.48 | 88.42 | 0.65 | 92.43 |
| | B-DISTIL | 87.41 | 0.49 | 89.31 | 0.71 | 92.25 |
| DSA-19 | E-RNN | 83.5 | 0.55 | 83.6 | 0.56 | 86.8 |
| | B-DISTIL | 82.1 | 0.53 | 84.1 | 0.58 | 87.2 |

Table 2.1: Early prediction performance. Performance of the ensemble produced by B-DISTIL compared to the E-RNN algorithm [70]. The accuracy and the cumulative fraction of the data early predicted at 50%, 75% and 100% time steps are shown. At T = 100, frac. evaluated is 1.0. The ensemble output by B-DISTIL with the early-prediction loss is competitive to the E-RNN algorithm. Unlike E-RNN, a method developed specifically for early prediction in RNNs, B-DISTIL is more generally applicable across model architectures.

We see that at all interrupt points in Figure 2.3, the predictions provided by B-DISTIL are competitive to that of the idealized baseline RESHED which requires the inference budget ahead of time for model selection, while being able to improve on its initial predictions if rescheduled. For instance, for the CIFAR-100 dataset and at the interrupt point at 0.5 on the x-axis, the predictions produced by B-DISTIL are comparable to a single model of the same inference duration, while being able to allow interrupts at all the previous points.

**Early prediction.** To evaluate the applicability of our method for early prediction in online time-series inference, we compare the performance of B-DISTIL to that of E-RNN from [70]. Unlike B-DISTIL, which can be applied to generic architectures, E-RNN is a state-of-the-art method for early prediction that was developed specifically for RNNs. When training, we set the classification loss to the early-classification loss used in E-RNN training. We evaluate our method on the time-series datasets Google-13 and DSA. The performance in terms of time steps evaluated is compared in Table 2.1. Here, we see that B-DISTIL remains competitive to E-RNN for early prediction. Unlike E-RNN, B-DISTIL also offers early prediction for offline/batch evaluation time-series data. For such cases, a threshold can be tuned similar to E-RNN and B-DISTIL can evaluate the models in its ensemble in order of increasing cost, exiting when the prediction score crosses this threshold.

### 2.4.4 Training Considerations and Scalability

**Connections.** Our method uses intermediate connections to improve its performance. Although these connections are designed to be efficient, they still have an overhead cost over an averaging-based ensemble. The FLOPs required to evaluate intermediate connections corresponding to the distillation tasks we considered in Figure 2.3 is shown in Figure 2.4. Here, we compare the FLOPs required to evaluate the model from round $T$ to the FLOPs required to evaluate the intermediate connections used by this model. Note that summing up all the FLOPs up to a round $T$, in Figure 2.4 gives the total FLOPs required for the ensemble with the first $T$ models. For all our models, the overhead of connections is negligible when compared to the inference cost of the corresponding model. To evaluate the benefits offered by the intermediate connections, we can compare the results of B-DISTIL run with connections and B-DISTIL without connections. The latter case can be thought of as running the AdaBoost algorithm for distillation. Note that this is the same as the RESHED baseline (weighted averaging). On comparing B-DISTIL in Figure 2.3 with RESHED we see the benefit of using intermediate connections.

![](img/32fe6d02b4faa69c4646a6e93e0375fc_38_0.png)

**Figure 2.4:** *Overhead of connections.* The FLOPs required to evaluating the model added in round $T$, compared with evaluate just the connections used by this model. We present the results corresponding to datasets that have models with smaller required FLOPs overall. We see that even for these models the connections add relatively little overhead.

## Overheads of training/distillation.

B-DISTIL requires additional compute and memory compared to a single model's training. Maintaining the two matrices $K_t^+$ and $K_t^-$ requires an additional $\mathcal{O}(NL)$ memory. Even for relatively large datasets with, say, $N = 10^6$ samples and $L = 1000$ classes, this comes out to a few gigabytes. However, since the two matrices can be stored on disk, a batch can be loaded into memory for loss computation asynchronously using data loaders provided by standard ML frameworks. The additional GPU memory requirement therefore becomes quite small, $\mathcal{O}(bL)$ for a mini-batch size $b$, same as the memory required to maintain one-hot classification labels for a mini-batch. Since gradient computation is required only for the model being trained in each round, which typically is smaller than the teacher model, the backward pass is relatively cheap. For large datasets, loading the data for the teacher model forward pass becomes the bottleneck. See Appendix A.4 for discussion on data loading, training time, and resources for an ImageNet distillation.

### Sorting $\{\mathcal{F}\}_t$ using profiling.

As mentioned in Section 2.2 B-DISTIL assumes the hypothesis classes in $\{\mathcal{F}\}_t$ are ordered on some inference-cost metric, say, inference time. In practice, we achieve this at runtime by starting with a small base model, and profiling subsequent models considered in later rounds at runtime. For example, in PyTorch, we can use the `torch.autograd.profiler` module to profile the forward pass of a model. As a heuristic, we then sort the models in $\{\mathcal{F}\}_t$ based on the average inference time of the models in the ensemble.

## 2.5 Conclusions, Limitations & Further Directions

This chapter introduced progressive ensemble distillation, whose goal is to distill a single teacher into an elastic model by creating an ordered ensemble that improves progressively as more components are evaluated. We showed that the ensemble's components indeed form a decomposition and deliver increasingly accurate predictions as additional members are executed, allowing us to greedily set elasticity without access to the current inference budget and to resume seamlessly after interruptions.

We develop an algorithm, B-DISTIL, for performing progressive ensemble distillation and demonstrate its utility for a number of applications in efficient inference. In particular, we experimentally demonstrate the effectiveness of B-DISTIL by decomposing well-established deep models onto ensembles for data from vision, speech, and sensor domains. Our procedure leverages a stochastic solver with log-barrier regularization to find weak learners, profiles candidate models during training and employs intermediary connections to bridge capacity gaps. The key insight behind B-DISTIL is that casting distillation as a two-player zero-sum game that abstracts architecture details into base class construction $\mathcal{F}$. This means that, conditioned on finding a ‘weak learner’ from the base class, we retain the guarantees of the classical boosting setup. Since these weak learners are only required to produce small improvements between rounds, we are able to reliably find such models.

A caveat of abstracting away the details of weak learners is that practitioners must still design a base class $\mathcal{F}$. Moreover, since B-DISTIL fundamentally depends on the distillation procedure, all cases where distillation or re-training itself is practically infeasible, are also infeasible for B-DISTIL. We assume that retraining or distillation is feasible at the resources, data, and model sizes desired.

Although this chapter focused on on-device continuous inference, the same distillation procedure also benefits cloud and data-center deployments. This includes tasks like layer-fusion, load-balancing, and improved resource utilization, which merit further investigation. Future work should also examine the impact of our approach on auxiliary metrics such as fairness and robustness [92, 108, 136]. In short, B-DISTIL turns a rigid expert model into an elastic ensemble with provable guarantees and practical impact across domains.
