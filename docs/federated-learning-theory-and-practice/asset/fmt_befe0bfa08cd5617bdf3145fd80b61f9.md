
These are attacks designed to make the model unusable by preventing the training process, more specifically, the aggregation algorithm at the server, from converging to a `good` minimum. A Byzantine client can in principle send an update that can deviate arbitrarily from the update that it is supposed to send. However, to avoid detection at the server, the adversarial update is suitably modified depending on the (`full` or `partial`) knowledge of the system – including the aggregation rule, the estimate of the updates from other clients and so on [\[5](#Chp004_75-90_B9780443190377000120.xhtml#br0025),[6\]](#Chp004_75-90_B9780443190377000120.xhtml#br0030). In response to the threat of Byzantine attacks, a host of defenses with different properties and applicability have been proposed (see Section [4.4.1.1](#Chp004_75-90_B9780443190377000120.xhtml#s0085)). In an emerging arms race, Byzantine attacks with modifications have been proposed [\[3](#Chp004_75-90_B9780443190377000120.xhtml#br0015),[23](#Chp004_75-90_B9780443190377000120.xhtml#br0115),[43\]](#Chp004_75-90_B9780443190377000120.xhtml#br0215) to circumvent Byzantine resilient aggregation rules, at least in practical settings. One such attack is local model poisoning [\[15\]](#Chp004_75-90_B9780443190377000120.xhtml#br0075). In this attack, compromised clients send carefully crafted updates in each iteration of FL. The updates are optimized to push the global model parameters towards the inverse of the direction along which the global model parameters would change without the attack. This attack has been shown to be highly successful against Byzantine-resilient aggregation mechanisms.

### 4.3.1.2 Backdoor attacks

These attacks are aimed at manipulating a subset of training samples by injecting `triggers` such that the machine learning models trained on the poisoned dataset will make incorrect predictions on test samples with the same embedded trigger [\[2](#Chp004_75-90_B9780443190377000120.xhtml#br0010),[42\]](#Chp004_75-90_B9780443190377000120.xhtml#br0210). Unlike Byzantine attacks, backdoor attacks are not designed to degrade the overall performance of the model or cause indiscriminate errors on test samples. Instead, the goal of a backdoor attack is to inject a `stealthy` or undetectable backdoor in the model, such that it predicts a target label `τ` on any input data that embeds the attacker-chosen trigger. Furthermore, backdoor attacks explicitly optimize their objective to allow training convergence and high model performance (in terms of chosen metrics such as accuracy) on most test samples (i.e., simultaneously fit both the backdoor and the main tasks). Depending on how the global trigger is injected into the model, we can further group proposed attacks into `centralized` and `distributed` backdoor attacks. In the centralized setting, all the malicious clients embed the same trigger in their updates, i.e., the global trigger is shared. In the decentralized setting, the global trigger is decomposed into local patterns and these smaller trigger patterns are then shared with the malicious clients.

**Centralized sample-based trigger.** One of the first centralized model poisoning-based backdoor attacks was introduced in [\[4\]](#Chp004_75-90_B9780443190377000120.xhtml#br0020). They analyze the feasibility of a successful backdoor attack with a single malicious client, and also with `M` colluding malicious clients sharing the same auxiliary dataset, i.e., `𝒟[aux, m] = 𝒟[aux]` for `m = 1, …, M`, under probabilistic selection. In this attack, every data sample in the auxiliary dataset is a trigger with target label `τ[i]`. In other words, for a given classifier `f`, the adversarial objective is to maximize the targeted misclassification of every sample in `𝒟[aux]` (or equivalently, minimize loss) as follows:

```
L_attack(𝒟_m ∪ 𝒟_aux, w̃^(t)) = max_{w̃^(t)} ∑_{i=1}^r 1[f(x_i; w̃^(t)) = τ_i],
```
(4.4)

where `1[·]` is the identity function that produces an output of 1 when the condition is satisfied and 0 otherwise. Note, in Eq. [(4.4)](#Chp004_75-90_B9780443190377000120.xhtml#deq4), `w̃^(t) = w^(t-1) + α_m δ_m^(t)` is used an estimate of the global model at timestep `t`. This is because the malicious agent, in practice, is expected to have limited to no visibility into the updates shared by the other (benign) clients.

The authors also defined a second accuracy objective to ensure that the performance of the malicious update on the test dataset (denoted by `𝒟[test]`) is close to that of the global model (updated with data from all clients expect the malicious one). Formally,

```
∑_{(x_j, y_j) ∈ 𝒟_test} 1[f(x_j; w_{S_t \ m}^(t)) = y_j] - 1[f(x_j; w̃^(t)) = y_j] < γ_t,
```
(4.5)

where `γ_t` is the threshold that a server could use to reject an update. A small value of `γ_t` implies that the malicious update should be very similar to the benign updates and hence highly stealthy.

An `alternating minimization strategy` is used for simultaneously optimizing Eqs. [(4.4)](#Chp004_75-90_B9780443190377000120.xhtml#deq4) and [(4.5)](#Chp004_75-90_B9780443190377000120.xhtml#deq5). For a certain number of steps, the malicious objective in Eq. [(4.4)](#Chp004_75-90_B9780443190377000120.xhtml#deq4) is optimized using the samples in `𝒟[aux]` to generate an update. This update is then used for optimizing the accuracy objective over `𝒟[m]`. These two steps are alternately repeated until a stealthy and malicious update is successfully generated.

**Centralized semantic-based trigger.** This attack was conceptualized in [\[2\]](#Chp004_75-90_B9780443190377000120.xhtml#br0010) and evaluated for `M` colluding malicious clients sharing the same auxiliary dataset `𝒟[aux]`. The triggers are defined based on the semantic properties of the data. For example, a semantically backdoored image-classification model would misclassify all `purple cars` as `birds`. In this case, `𝒟[aux]` would contain the images with label `purple car` and the target label for the entire class will be set to `bird`. The malicious client is free to choose either naturally occurring features in the data sample, or features that cannot occur without the client's involvement (e.g., images of a special hat or glasses that only the malicious client has).

The malicious client performs `model replacement` to insert the backdoor. The idea is to substitute the global model with a model `w̃` given by

```
w̃ = w^(t-1) + (η/n) ∑_{k ∈ S_t} δ_k^(t),
```
(4.6)
