
- 18. Krizhevsky, A., Hinton, G.: Learning multiple layers of features from tiny images (2009) [online]

- 19. Qin, H., et al.: Forward and backward information retention for accurate binary neural networks. In: Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, pp. 2250–2259 (2020)

- 20. Zhou, S., Wu, Y., Ni, Z., Zhou, X., Wen, H., Zou, Y.: DoReFa-Net: Training low bitwidth convolutional neural networks with low bitwidth gradients. arXiv preprint arXiv:1606.06160 (2016)

- 21. Andri, R., Cavigelli, L., Rossi, D., Benini, L.: YodaNN: an architecture for ultralow power binary-weight CNN acceleration. IEEE Trans. Comput. Aided Des. Integr. Circuits Syst. **37**(1), 48–60 (2017)

- 22. Umuroglu, Y., et al.: FINN: a framework for fast, scalable binarized neural network inference. In: Proceedings of the 2017 ACM/SIGDA International Symposium on Field-Programmable Gate Arrays, pp. 65–74 (2017)

- 23. Rastegari, M., Ordonez, V., Redmon, J., Farhadi, A.: XNOR-Net: ImageNet classification using binary convolutional neural networks. In: European Conference on Computer Vision, pp. 525–542. Cham: Springer International Publishing (2016)

## Memory-Enhanced Invariant Prompt Learning for Urban Flow Prediction Under Distribution Shifts

Haiyang Jiang$^1$, Tong Chen$^{1(\text{\unknown})}$, Wentao Zhang$^2$, Quoc Viet Hung Nguyen $^3$, Yuan Yuan$^4$, Yong Li$^4$, and Hongzhi Yin $^1$

$^1$ The University of Queensland, Brisbane, QLD, Australia
{haiyang.jiang,tong.chen}@uq.edu.au
$^2$ Peking University, Beijing, China
wentao.zhang@pku.edu.cn
$^3$ Griffith University, Gold Coast, Australia
$^4$ Tsinghua University, Beijing, China
y-yuan20@mails.tsinghua.edu.cn, liyong07@tsinghua.edu.cn

Abstract. While Spatial-Temporal Graph Neural Networks (STGNNs) excel at urban flow prediction, they struggle with distribution shifts caused by dynamic spatial-temporal environments. To improve generalizability to out-of-distribution (OOD) data, a typical solution is to disentangle invariant patterns that carry stable causal effects from variant ones that are environment-dependent. Existing OOD-robust methods attempt to model these environments but face challenges in quantifying dynamic changes and suffer from high computational costs. As a solution, we propose Memory-enhanced Invariant Prompt Learning (MIP), which enables environmental interventions directly within the latent space by learning a memory bank from the spatial-temporal urban flow graphs. Then, by performing spatial-temporal interventions on the variant prompts, diverse environments are constructed in the latent space to facilitate invariant learning. The invariant prompts, together with a memory-enhanced causal graph, are fed into an STGNN backbone to produce accurate predictions. Extensive experiments on two public urban flow datasets confirm MIP's effectiveness in improving robustness against OOD data.

Keywords: Spatial-temporal Graph Neural Networks · Out-of-distribution Generalization · Invariant Learning

Supplementary Information The online version contains supplementary material available at https://doi.org/10.1007/978-3-032-06066-2_9.

### 1 Introduction

Urban flow prediction, which forecasts traffic, pedestrian, and public transportation dynamics, is crucial for smart cities [18], public transit management [7, 33],
![](img/f56761e6196132d5b74909d98468408f_206_0.png)

(a) Traffic speed at node A. (b) Traffic speed at node B. (c) Traffic speed at node C.

Fig. 1. The sampled traffic speed recorded by three sensors in the METR-LA dataset, where nodes B and C are two closest sensors of Node A. The records correspond to two Wednesdays in the 3rd and 13th weeks of the dataset.

and ride-sharing services [4,37]. Typically modeled as a spatial-temporal graph, nodes (e.g., traffic sensors or geographical grids [29]) in urban flow are connected based on proximity, with the goal of predicting future traffic flow at each node. To effectively model these spatial-temporal dependencies, recent solutions are built upon deep learning-based approaches, particularly Spatial-Temporal Graph Neural Networks (STGNNs) [17,33,36]. These models leverage Graph Neural Networks (GNNs) [17,33] to capture spatial correlations and sequential models like Recurrent Neural Networks (RNNs) [17,20] and Temporal Convolution Networks (TCNs) [33,36] for learning temporal dependencies. Some STGNNs further enhance predictions by incorporating dynamic graph structures based on temporal feature similarities [3,26,34] or modeling complex spatial-temporal interactions [6,12].

Most STGNNs operate under the assumption that urban flow data adheres to the independent and identically distributed (I.I.D.) nature, which rarely holds true in real-world scenarios. In reality, once deployed, a trained model may need to perform inference on unseen data with patterns that are distinct significantly from the training data, a phenomenon referred to as distribution shift or out-of-distribution (OOD) during the test phase. Figure 1 provides a real example from the METR-LA traffic dataset (see Sect. 5 for details), which demonstrates the traffic of three locations on two Wednesdays. Firstly, urban flow exhibits continuous distribution shifts. For each of the three geographic nodes, the two traffic records demonstrate entirely different patterns. Such continuous distribution shifts at each location disrupt long-term spatial-temporal patterns and hinder the generalizability of STGNNs. Secondly, there are heterogeneous shifts across locations. Although both nodes B and C are adjacent to node A, their patterns shift in distinct manners. This discrepancy complicates spatial correlations, as GNNs propagate noise from affected nodes. In urban flow prediction, spatial-temporal regularities can be easily disrupted by unexpected events such as traffic accidents or extreme weather. Moreover, during inference, it is generally impractical to assume prior knowledge about the occurrence of such perturbations that result in OOD data, thereby compromising prediction accuracy and diminishing the effectiveness of existing STGNNs. While frequent retraining can alleviate this issue, it is computationally prohibitive in such high-throughput applications. Thus, before entering the update cycle, an ideal STGNN should stay accurate for a reasonable period of time by generalizing to changed data distributions.

With the presence of distribution shifts in urban flow prediction, a key to enhancing the generalizability of STGNNs is to discover and leverage the invariant (i.e., causal) patterns within spatial-temporal data. Many studies on OOD generalization [1,25] point out that distribution shifts are driven by the dynamics of underlying environments, where invariant risk minimization [2,22,31] can be leveraged to optimize the model with augmented data drawn from diverse environments. As such, some methods [23,24] decouple invariant patterns from variant ones learned from the data. For example, when handling graph-structured data, [5,32,38] learn two disentangled graph structures that contain either invariant or variant connections between nodes. Unfortunately, these models are misaligned with urban flow prediction tasks as they only focus on a static graph topology that does not assume the temporal evolution of node features.

To this end, we aim to build an OOD-robust STGNN that can distinguish invariant spatial-temporal patterns from urban flow data. Specifically, we propose Memory-enhanced Invariant Prompt learning (MIP), a novel solution to urban flow prediction. In MIP, we attach a memory bank to the STGNN architecture, which learns and memorizes the causal patterns from the dynamic node features. Based on the information stored in the memory bank, a new graph structure reflecting the semantic causality between different locations is built, providing a complementary graph view to the default, distance-based graph structure for node representation learning. Then, the prompt vectors carrying invariant or variant patterns are extracted respectively by attentively querying the memory bank with each node's features. Furthermore, to facilitate end-to-end optimization via invariant risk minimization and ensure disentanglement between invariant and variant patterns, we put forward an innovative intervention pipeline that directly operates on the extracted variant prompts. Different from existing invariant learning methods [35,40], MIP bypasses the need for learning additional representations of different environments, and the designed intervention is a simple-yet-effective approach for implicitly mimicking the effect from data distribution shifts to node representations. The disentangled invariant patterns, along with both the geographical and causal graphs, are eventually fed into a spatial-temporal backbone model to make accurate urban flow predictions. To be concise, our contributions are summarized below:

- New Challenge. We highlight a largely overlooked challenge in urban flow prediction: the pervasive presence of OOD data that hinders model generalizability. To address this, we propose a new framework, namely MIP to mitigate distribution shifts in urban flow prediction.

- New Method. We extract invariant and variant features from a trainable memory bank and generate a supplementary graph structure. By implementing interventions on variant patterns and leveraging an invariant learning
