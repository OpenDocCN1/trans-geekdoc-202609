
### Figure 5.2: Federated learning
(a) An untrained global model (represented by the green dot) is broadcasted to the client devices. (b) The training happens in each client device, and only the updated client model (represented by the various geometric figures) is transmitted to the cloud to update the global model. (c) The updated global model (represented by the gray pentagon) is broadcasted to all the client devices, and the process repeats. Based on \[Sas19\].

Federated learning is a generalized form of Sync SGD but, rather than synchronizing after every iteration, the weights are synchronized after some local epochs. The more infrequent the synchronizations, the more likely the model has convergence challenges. However, frequent synchronizations consume significant network bandwidth, which is prohibited in some devices. The primary challenge of federated learning is to reduce the synchronization frequency (by increasing the number of local epochs) and maintain the expected training convergence.

Two additional challenges can affect convergence. First, the data in each device is typically not independent and identically distributed (IID); data within a client is more similar than data across clients, and the number of samples between clients varies. This non-IID violates the guidance to randomize the order of the samples in the training dataset so each batch has IID samples.

Second, the local devices have heterogeneity both in computational capacity and network reliability across devices. In particular, mobile phones vary significantly in memory, compute, and network connectivity with approximately two-thirds of operating mobile phones in the world being over six years old \[Haz18\].

The server uses an average of the local models weighted by the number of training samples in each device to compute a global model update. Alternatively, a more stable approach is to randomly choose the clients (assuming a large pool of candidates) with probability proportional to the number of training samples in each device, and use an unweighted average to compute the global model update \[LSZ+19\].

A federated learning system uses more clients than needed to train local models to mitigate device and network unreliability. A system may assign 300 devices to train local models but only needs to collect local models from 256 devices. Assuming each device uses a local batch size of 16, then the global batch size is 256 × 16 = 4096, which may be the limit (the largest batch size that converges to an adequate minimum) for some topologies.

A simple technique to improve robustness to both non-IID batches and local models that are unable to complete the local number of epochs is to use a proximal term. This term is a small adaptable penalty in the objective function for significant deviations from the global model. Note that it is better to communicate a local model that has not completed the requested epochs than to ignore it \[LSZ+19\].

Communication overhead can be reduced by quantizing with rotations and communicating the weight changes \[KMY+17\]. A randomly applied mask can further reduce the number of communicated parameters. Traditional data compression techniques can also be used. These techniques also apply to conventional Sync SGD data parallelism to decrease network traffic but are more critical in federated learning due to the higher communication cost. Optimization techniques, such as LAMB and RangerLARS, used in data centers, can be applied to federated learning to increase the number of client devices and accelerate training. Also, TensorFlow provides an API to simulate federated learning with a couple of additional lines of code.

## Areas of Caution

Three areas of caution are as follows:

1. Training and communicating a model can be expensive (in terms of battery and data consumption). These expenses are mitigated by limiting training to periods when the device is plugged in and idled and communicating the local model when the device is on a free wireless connection.
2. Despite not transmitting the training data, some information about the local training data can be extracted from local models \[HAP17\]. To preserve privacy, for instance, Google uses secure aggregation where the local models are only unencrypted and averaged when multiple models become available to the server \[BIK+17\]. OpenMined developed PySyft on top of PyTorch to improve privacy. [Section 10.3](#20_Chapter10.xhtml#sub10-3) discusses other ongoing work to maintain privacy.
3. Older devices with limited computational and memory capacities, and devices in remote areas may not proportionally contribute to the overall training. This imbalance results in a model that learns characteristics biased toward more affluent populations. Further work is required to mitigate this.

## 5.4 Collective Communication Primitives

There are various communication functions, known as collective communication primitives, and library implementations. These primitives are used in data parallelism to communicate and then aggregate the local gradients, in model parallelism to communicate the activations and their respective gradients, and in transitioning between model and data parallelism to rearrange the data properly. Some common collective communication primitives are as follows:

- **Broadcast**: `M` elements in the root node are copied to the other `P` – 1 processor nodes, as shown in [Figure 5.3a](#15_Chapter05.xhtml#fig5-3).
- **Scatter**: `M` elements in the root node are partitioned, and each partition with `M/(P - 1)` elements is copied to a different processor node, as shown in [Figure 5.3b](#15_Chapter05.xhtml#fig5-3).
- **Reduce**: the root node receives `M` elements from each of the others `P` – 1 processor nodes and performs a reduction operation, such as sum, maximum, minimum, mean, or product, across each of the `P` – 1 elements.
- **Gather**: the root node receives `M/(P - 1)` elements from each of the other `P` – 1 processor nodes and concatenates them (equivalent to [Figure 5.3b](#15_Chapter05.xhtml#fig5-3) with the arrows reversed).
- **AllReduce**: Equivalent result as Reduce + Broadcast.
- **AllToAll**: `M` elements in each node are partitioned, and each partition with `M/(P - 1)` elements is copied to a different processor node where the received partitions are concatenated. Equivalent result to Scatter and Gather for all nodes, as shown in [Figure 5.3c](#15_Chapter05.xhtml#fig5-3).
- **AllGather**: Equivalent result as Gather + Broadcast.
- **ReduceScatter**: Equivalent result as Reduce + Scatter.

The `AllReduce`, `AllToAll`, and `AllGather` primitives do not require a dedicated root node. While their end-result is equivalent to sequentially using two simpler primitives, they typically use more efficient implementations. Later in this section, we analyze various `AllReduce` implementations.

The MPICH, OpenMPI, Intel MPI, and MVAPICH libraries implement primitives using the Message Passing Interface (MPI) standard specifications. The MPI is a library specification that operates at the transport layer implemented by MPICH and other libraries in C/C++ and Fortran with message-passing standards and APIs. In the MPI specification, each processor node has a unique address space. The literature on collective communication primitives is extensive, including their optimizations for clusters connected by switched networks and a study of MPI usages \[TRG05, LMM+19\].

![image](images/fig5_3.png)

### Figure 5.3
(a) The broadcast primitive copies a set of elements in the root node to the other nodes. (b) The scatter primitive copies a separate partition of a set of elements in the root node to the other nodes. Note that reversing the arrows results in the gather primitive. (c) The all-to-all primitive (also known as transpose) copies a separate partition of a set of elements in each node to the other nodes, where the received partitions are concatenated.
