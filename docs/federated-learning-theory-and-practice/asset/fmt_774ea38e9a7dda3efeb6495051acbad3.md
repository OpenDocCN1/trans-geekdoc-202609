
# Federated Learning

Federated learning is a machine learning setting that enables millions of clients (mobile or edge devices) to jointly train a deep learning model using their private data without compromising their privacy. The training procedure in federated learning is orchestrated by a central server responsible for providing the shared global model to participants and aggregating their submitted model updates to generate the new global model. The key appeal of federated learning is that it does not require centralizing participating users' training data, which makes it ideal for privacy-sensitive tasks.

## Standard FL Setting

A standard FL setting consists of `P` participating clients. Each client `i` holds a shard of training data `D[i]` which is private to the client and is never shared with the orchestration server. In each round `t` of federated learning, the central server randomly selects a set `ζ^(t)` of `c` clients, and broadcasts the current global model `G^(t)` to them. The selected set of clients `ζ[t]` is referred to as *training cohort* of round `t`. Each client `i` in the training cohort locally and independently trains the joint model `G^(t)` using stochastic gradient descent (SGD) optimization algorithm for `E` epochs on its local training data `D[i]` to obtain a new local model `L[i]^(t+1)`, and submits the difference `L[i]^(t+1) − G^(t)` as its model update to the central server. Next, the central server averages model updates submitted by clients in the training cohort and updates the shared global model using its learning rate `η` to obtain the new global model `G^(t+1)`, as shown below:

```
G^(t + 1) = G^(t) + (η/n) * Σ(i=1 to n) (L_i^(t + 1) - G^(t))
```

Model training resumes until the global model converges to acceptable performance, or certain training rounds are completed.

## 9.2.2 Secure Aggregation

Secure aggregation (SecAgg) [[5]](#Chp009_161-179_B978044319037700017X.xhtml#br0025) is a secure multi-party computation protocol that can reveal the sum of submitted model updates to the server (or aggregator) while keeping each individual update uninspectable at all times. Secure aggregation consists of three phases: *preparation*, *commitment*, and *finalization* [[4]](#Chp009_161-179_B978044319037700017X.xhtml#br0020). In the preparation phase, shared secrets are established between the central server and participating clients. Model updates from clients who drop out during the preparation phase will not be included in the aggregate. Next, in the commitment phase, each device uploads a cryptographically masked model update to the server, and the server computes the sum of the submitted mask updates. Only clients that successfully commit their masked model updates will contribute to the final aggregate. Lastly, in the finalization phase, committed clients reveal sufficient cryptographic secrets to allow the server to unmask the aggregated model update.

## 9.2.3 Robust Aggregation Rules and Defenses

Numerous studies have proposed robust aggregation rules [[3](#Chp009_161-179_B978044319037700017X.xhtml#br0015), [21](#Chp009_161-179_B978044319037700017X.xhtml#br0105), [30]](#Chp009_161-179_B978044319037700017X.xhtml#br0150) to ensure convergence of distributed learning algorithms in the presence of adversarial actors. The majority of studies in this line of work assume a Byzantine threat model in which the adversary can cause local learning procedures to submit any arbitrary update to ensure the convergence of learning algorithms to an ineffective model. In addition to robust aggregation rules, several works have proposed novel defenses [[9](#Chp009_161-179_B978044319037700017X.xhtml#br0045), [26]](#Chp009_161-179_B978044319037700017X.xhtml#br0130) against backdoor and poisoning attacks in federated learning. In what follows, we review several of the techniques which we experiment with in Section [9.5](#Chp009_161-179_B978044319037700017X.xhtml#s0045).

### Krum

The Krum algorithm, proposed by [[3]](#Chp009_161-179_B978044319037700017X.xhtml#br0015), is a robust aggregation rule which can tolerate `f` Byzantine attackers out of `n` participants selected at any training round. Krum has theoretical guarantees for the convergence should the condition `n ≥ 2f + 3` hold true. At any training round, for each model update `δ[i]`, Krum takes the following steps: (a) computes the pairwise Euclidean distance of `n − f − 2` updates that are closest to `δ[i]`, (b) computes the sum of squared distances between update `δ[i]` and its closest `n − f − 2` updates. Then, Krum chooses the model update with the lowest sum to update the parameters of the joint global model.

### Coordinate-wise Median

In coordinate-wise median (CWM) aggregation rule [[30]](#Chp009_161-179_B978044319037700017X.xhtml#br0150), for each `j`th model parameter, the `j`th coordinates of received model updates are sorted, and their median is used to update the corresponding parameter of the global model.

### Trimmed Mean

Trimmed mean (TM) is a coordinate-wise aggregation rule [[30]](#Chp009_161-179_B978044319037700017X.xhtml#br0150). For `β ∈ [0, 1/2)`, the trimmed mean computes the `j`th coordinate of the aggregate of `n` model updates as follows: (a) it sorts the `j`th coordinate of the `n` updates, (b) discards the largest and smallest `β` fraction of the sorted updates, and (c) takes the average of remaining `n(1 − 2β)` updates as the aggregate for the `j`th coordinate.

### RFA

RFA [[21]](#Chp009_161-179_B978044319037700017X.xhtml#br0105) is a robust privacy-preserving aggregator which requires a secure averaging oracle. RFA aggregates local models by computing an approximation of the geometric median of their parameters using a variant of the smoothed Weiszfeld's algorithm [[27]](#Chp009_161-179_B978044319037700017X.xhtml#br0135). RFA appears to be tolerant to data poisoning attacks but cannot offer Byzantine tolerance as it still requires clients to compute aggregation weights according to the protocol. Relying on clients to follow a defensive protocol without a proper means to attest to the correctness of computations on the client-side casts doubts on the practicality of RFA. To the best of our knowledge, RFA is the only existing defense that is compatible with secure aggregation.

### Norm Bounding

Norm bounding (NB) is an aggregation rule proposed by [[26]](#Chp009_161-179_B978044319037700017X.xhtml#br0130), which appears to be robust against false-label backdoor attacks. In this aggregation rule, a norm constraint `M` is set for model updates submitted by clients to normalize the contribution of any individual participants. Norm bounding aggregates model updates as follows: (a) model updates with norms larger than the set threshold `M` are projected to the `l[2]` ball of size `M` and then (b) all model updates are averaged to update the joint global model.
