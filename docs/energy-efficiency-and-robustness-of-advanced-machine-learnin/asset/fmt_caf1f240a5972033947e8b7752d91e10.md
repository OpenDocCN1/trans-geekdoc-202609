
At the output, our methodology generates the approximated version of a given CapsNet, which is ready to execute in a specialized hardware accelerator for inference with approximate components. To save area and energy for each operation, we select the approximate components from a given library that correspond to their resiliency level. Therefore, more aggressive approximations are chosen for more resilient operations without significantly affecting the classification accuracy of the CapsNet inference.

### 3.6.4 Evaluation of the ReD-CaNe Methodology

#### 3.6.4.1 Experimental Setup

We train each given CapsNet model for a given dataset using TensorFlow \[[1](#refbib.xhtml#refbib1)\], running on two Nvidia GeForce RTX 2080 Ti GPUs. The trained model is an input to our ReD-CaNe methodology. The noise is injected into the arrays, and then the accuracy is monitored to identify the resilience of the operations.

We test our methodology on the DeepCaps \[[220](#refbib.xhtml#refbib220)\] and the original CapsNet \[[236](#refbib.xhtml#refbib236)\]. We use the CIFAR10 \[[112](#refbib.xhtml#refbib112)\], SVHN \[[186](#refbib.xhtml#refbib186)\], MNIST \[[118](#refbib.xhtml#refbib118)\], and Fashion-MINST \[[284](#refbib.xhtml#refbib284)\] datasets. The accuracy results obtained for different datasets are reported in [Table 3.13](#chapter3.xhtml#tbl3_13). [Table 3.14](#chapter3.xhtml#tbl3_14) shows the partition of the CapsNet operations into groups, which is then used in the group extraction step.

 [Table 3.13:](#chapter3.xhtml#b3tbl3_13) Classification accuracy results using accurate multipliers. 

| Architecture || Dataset || Accuracy |
| --- | --- | --- |
| DeepCaps || CIFAR10 || 92.74 |
| SVHN || 97.56 |
| MNIST || 99.72 |
| CapsNet || Fashion-MNIST || 92.88 |
| MNIST || 99.67 |

[Table 3.14:](#chapter3.xhtml#b3tbl3_14) Grouping the operations of the CapsNet inference.

| # | Group Name | Description |
| --- | --- | --- |
| 1 | MAC Outputs | Outputs of the matrix multiplications |
| 2 | Activations | Output of the activation functions (Squash or ReLU) |
| 3 | Softmax | Results of the softmax (*c* coefficients in dynamic routing) |
| 4 | Logits Update | Update of the logits (*b* coefficients in dynamic routing) |

The proposed methodology is implemented in TensorFlow \[[1](#refbib.xhtml#refbib1)\]. First, the network is trained using standard techniques. We modified the computational graph in *protobuf* format by including our noise injection model in the *Graph tool*. We implemented a custom node for the noise injection, where the values of *NA* and *NM* may be specified as inputs to this node. Hence, for each node *τ*, a new set of nodes *T* is added to the graph. These nodes have the same shape as *τ* and they consist of adding a Gaussian noise with *s**t**d* = *N**M** ⋅ *R*(*τ*) and *m* = *N**A** ⋅ *R*(*τ*), given the range *R* of the node *τ*.

We use the EvoApprox8b library \[[179](#refbib.xhtml#refbib179)\], which consists of 358-bit unsigned components. We select an 8-bit wordlength since it is accurate enough in the computational path of the CapsAcc.

#### 3.6.4.2 Detailed Analysis for the CIFAR10 Dataset

As a case study, we report detailed results for the DeepCaps on the CIFAR10 dataset. We selected an *N**M** ∈ \[0.5…0.001\]. To analyze the general scenario of error resilience, we selected the average error *N**A** = 0. In the experiment for **Step 2** of our methodology, we inject the same noise amount to every operation within a group while keeping the other groups accurate. From the results shown in [Figure 3.57](#chapter3.xhtml#fig3_57), we notice that the *Softmax* and the *Logits update* groups are more resilient than *MAC outputs* and *Activations* because the CapsNet accuracy starts decreasing with a relatively lower *NM*. Note that for low *NM*, the noise injection slightly increases the accuracy due to a regularization effect similar to the dropout \[[256](#refbib.xhtml#refbib256)\].

![Figure 3.57: Group-wise resilience for the CIFAR10 dataset. (a) Complete results. (b) Zoomed view of the accuracy drop, centered at 0\\%.](images/fig3_57.jpg)

[Figure 3.57:](#chapter3.xhtml#b3fig3_57) Group-wise resilience for the CIFAR10 dataset. **(a)** Complete results. **(b)** Zoomed view of the accuracy drop, centered at 0%.

#### 3.6.4.3 Evaluating the Selection of Approximate Components

The selection of the approximate component for each operation depends on the level of *NM* that corresponds to a tolerable accuracy loss (typically null or very low). Recalling Equation (3.12), the parameters *NM* and *NA* are dataset-dependent since their values change accordingly to the input range *R*. In our case study (DeepCaps for CIFAR10), we select a subset of 10⁶ elements from the inputs of every *Conv2D* layer of the DeepCaps, with their corresponding distributions (frequency of occurrence) shown in [Figure 3.58a](#chapter3.xhtml#fig3_58). The distribution is approximately Gaussian, but the peak between 40 and 50 in the input feature maps is caused by a specific distribution of the input dataset. Indeed, such a peak occurs in the first Caps2D layer, as shown in [Figure 3.58b](#chapter3.xhtml#fig3_58).

![Figure 3.58: (a) Distribution of 10⁶ random samples from the inputs of the convolutions in the DeepCaps for the CIFAR10 dataset. (b) A focus on some layers, showing the peak in the first Caps2D layer.](images/fig3_58.jpg)

[Figure 3.58:](#chapter3.xhtml#b3fig3_58) **(a)** Distribution of 10⁶ random samples from the inputs of the convolutions in the DeepCaps for the CIFAR10 dataset. **(b)** A focus on some layers, showing the peak in the first Caps2D layer.

Hence, in [Table 3.15](#chapter3.xhtml#tbl3_15) we measure the *NM* and *NA* parameters of the selected multipliers in the library. We use two different input distributions, the *modeled* one that is based on random inputs generated with a uniform distribution, and the *real* one, which is based on the input distribution previously shown in [Figure 3.58](#chapter3.xhtml#fig3_58). Note that these values slightly differ because the *NM* and *NA* parameters are dataset-dependent. The major differences are due to our modeled distribution overestimating the *NM* and *NA*. Hence, the selection of approximate components based on our models may be systematically employed for designing approximate CapsNets.

 [Table 3.15:](#chapter3.xhtml#b3tbl3_15) Power, area, and noise magnitude, calculated with a modeled input dataset (with uniform distribution) and using a real input distribution *I*, for different approximated multipliers from the EvoApprox8B library. We have randomly selected 14 components representative of the complete library.

| Multiplier | Power | Area | Modeled *Δ*[*X*] | Real *Δ*[*X*] |
| --- | --- | --- | --- | --- |
| mul8u_ | μW | μm² | NA | NM | NA | NM |
| 1JFF | 391 (-0%) | 710 (-0%) | 0.0000 | 0.0000 | 0.0000 | 0.0000 |
| 14VP | 364 (-7%) | 654 (-8%) | 0.0000 | 0.0001 | 0.0000 | 0.0001 |
| GS2 | 356 (-9%) | 633 (-11%) | 0.0004 | 0.0017 | 0.0001 | 0.0013 |
| CK5 | 345 (-12%) | 604 (-15%) | 0.0000 | 0.0002 | 0.0000 | 0.0002 |
| 7C1 | 329 (-16%) | 607 (-14%) | 0.0011 | 0.0033 | 0.0007 | 0.0026 |
| 96D | 309 (-21%) | 605 (-15%) | 0.0035 | 0.0077 | 0.0020 | 0.0051 |
| 2HH | 302 (-23%) | 542 (-24%) | -0.0001 | 0.0007 | -0.0001 | 0.0007 |
| NGR | 276 (-29%) | 512 (-28%) | 0.0001 | 0.0008 | 0.0002 | 0.0009 |
| 19DB | 206 (-47%) | 396 (-44%) | 0.0010 | 0.0019 | 0.0010 | 0.0021 |
| DM1 | 195 (-50%) | 402 (-43%) | 0.0003 | 0.0025 | 0.0005 | 0.0025 |
| 12N4 | 142 (-64%) | 390 (-45%) | 0.0018 | 0.0054 | 0.0019 | 0.0056 |
| 1AGV | 95 (-76%) | 228 (-68%) | 0.0027 | 0.0080 | 0.0026 | 0.0117 |
| YX7 | 61 (-84%) | 221 (-69%) | 0.0484 | 0.0741 | 0.0268 | 0.0347 |
