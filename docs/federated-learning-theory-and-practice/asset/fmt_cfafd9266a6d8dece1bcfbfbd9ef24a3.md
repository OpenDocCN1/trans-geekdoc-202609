
In most practical scenarios, partial/all devices' hardware configurations cannot be obtained. Therefore, we leverage the proposed time-based approximation to fast identify the stragglers. In this case, our approach will assign each device with a lightweight test bench (only train a few iterations) and quickly record their training time cost. Then the approach will rank all devices based on their training time cost values and obtain an approximate index `T = {T[1], T[2], …, T[N]}` (where `T[1]` represents the longest time cost). Based on FL requirements, the top-`k` devices in the index are identified as potential stragglers.

### 19.3.3 Optimization target determination

After finding the potential stragglers, it is important to identify the optimization target, namely, the expected model volumes of stragglers in each training cycle to achieve acceleration. The expected model volume can be selected with a pre-defined volume or adapted to a specific value according to the resource constraints.

For the former, we can define multiple model volume levels in advance and assign each straggler with a model volume level according to the training time cost index `T`. The model volume will be dynamically adjusted to an optimal point during the first several training cycles in the FL process.

### 19.3.4 Soft-training on straggling mobile devices

With identified potential stragglers and corresponding model volumes from initialization, we propose a “soft-training” scheme to adapt the optimized model to specific resource constraints while guaranteeing convergence effectiveness. [Fig. 19.3](#Chp019_343-352_B9780443190377000296.xhtml#f0020) shows the entire “soft-training” flow, and we take neurons as our minimum model parameter structure. The algorithm can be divided into three steps:

![Figure 19.3 Soft-training scheme flow.](OEBPS/images/B9780443190377000296/gr003_u9.jpg)

Figure 19.3 Soft-training scheme flow.

**Step 1. Straggler model shrinking.** In order to achieve acceleration, we only select a set of neurons from stragglers' models to join the training cycle, thereby meeting the optimization targets (the expected model volume). As aforementioned, methods in Section [19.3](#Chp019_343-352_B9780443190377000296.xhtml#s0020) only approximately identify stragglers and their expected model volume. Therefore, `Helios` needs the first few training cycles to finalize the stragglers and model volumes by dynamically adjusting the model volumes to accommodate normal devices with respect to training time cost.

During the partial training, two types of neurons are selected to achieve an optimized convergence performance: the neurons with the higher contributions to the collaboration convergence (primary converge guarantee) and some other random neurons (further converge optimization). Then we define the contribution metric by leveraging the assumption in [[1]](#Chp019_343-352_B9780443190377000296.xhtml#br0005) that the neurons with larger weight parameter changing values will provide larger impacts to the global model. We assume the weight parameters of the `j`th neuron in the `i`th layer after training epoch `S[k]` as `θ[s, r, n]^(ij)(S[k])`, and the neuron's collaboration contribution `U^(ij)(S[k])` will be calculated by summing the changes in the current training cycle as

```
U^(ij)(S[k]) = θ[s, r, n]^(ij)(S[k]) − θ[s, r, n]^(ij)(S[k − 1]),
```
(19.1)

where a larger `U^(ij)` represents the target neuron, demonstrating a higher collaboration contribution. We will elaborately show how to select these two types of neurons in each training cycle in Steps 2 and 3.

**Step 2. Neuron rotation for model integrity.** With partial training in Step 1, model training consumption on stragglers can be adapted to the specific device resource constraints. Some previous methods leverage fixed model pruning to achieve partial training [[6](#Chp019_343-352_B9780443190377000296.xhtml#br0030), [7]](#Chp019_343-352_B9780443190377000296.xhtml#br0035). However, without an optimized training algorithm to keep a rather complete model structure, the pruned model parameters will permanently lose their contribution to the collaboration, thereby inevitably hurting convergence accuracy and speed.

Therefore, in our “soft-training,” we solve the conflict between the optimization targets and model integrity by letting different parts of model parameters (i.e., neurons) alternately join training cycles. As [Fig. 19.3](#Chp019_343-352_B9780443190377000296.xhtml#f0020) illustrates, in the `i`th training cycle, we first choose `P[s]` proportion of neurons:

```
Θ(S[k]) − Θ(S[k − 1]) = TopK(U^(ij)) ∪ Rand(U^(ij)), where K = P[s] * P[i] * n[i],
```
(19.2)

where `Θ(S[k])` represent the model parameter of the straggler and `Rand` operation is randomly selecting `(1 − P[s]) * P[i] * n[i]` neurons' `U^(ij)`. Next, in the `(i + 1)`th training cycle, since the neurons with the highest contribution do not change, we still select them in the training to provide the primary converge guarantee. On the contrary, a different set of neurons with lower contributions will be selected. By alternately joining each training cycle, every neuron on a straggler has opportunities to keep model integrity to the global model convergence.

**Step 3. Aggregation and local model updating.** After finishing a local training cycle, each local mobile device will upload the gradients of the selected neurons to the global device during the aggregation cycle. Meanwhile, the global device will average the uploaded model parameters to update the global model. The discussions of the global average convergence proof can be found in Section VI.B in our full paper. Once the new global model parameters are obtained, they will be sent to each local device for local model updating and the local mobile devices can start the next training cycle.

With the above three steps, models on the stragglers adapted to the optimization targets while still maintaining a rather complete model structure and balanced contribution, thereby guaranteeing the global model convergence performance.
