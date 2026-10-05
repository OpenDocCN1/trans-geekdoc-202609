# 3
THE ROLE OF DEPTH AND SPATIAL ADAPTIVITY

The previous chapter established how compositionality and locality allow kernel methods and shallow neural architectures to overcome the curse of dimensionality. We showed that when the target function is a sum of local components, the generalization performance is governed by the size of the receptive field rather than the input dimension. However, real-world data rarely exhibit flat structure. Instead, they are widely believed to possess a hierarchical organization, where features at higher levels are composed of sub-features at finer scales.

Although many works have this idea [Bie87; Pog+17a; KT18; ZXS18; Dez+20; KKW20; PBL19; SH20; FSH21; GRSH22], we miss a qualitative understanding of how hierarchy affects the learning curve $eta$ – which characterizes the decay rate of generalization error $\mathcal{E}$ with the number of training samples $P$. Specifically, there are no theoretical predictions for $eta$ in the context of deep networks on tasks with varying degrees of locality or a hierarchical structure.

In this chapter, we address this gap by developing convolutional neural networks (CNNs) in the overparameterized regime. In this limit, the width of each hidden layer tends to infinity, and the network's output converges to that of a corresponding kernel method [JGH18; Lee+19]. While real-world networks do not generally operate in such a regime, the correspondence with kernel regression provides powerful theoretical tools for computing the decay of the learning curves. Namely, as discussed before, given an infinitely wide neural network, its generalization performance depends on the spectrum of the induced kernel [CDV07; BCP20].

The central challenge, becomes the characterization of the kernel spectrum, especially when kernels exhibit complex structure and are defined recursively [Aro+19]. This characterization is the primary outcome of this chapter, along with the subsequent study of generalization in deep CNNs.

Parts of this chapter have been previously published in:
Cagnetta, F., Favero*, A. and Wyart, M., 2024. What can be learned with convolutional neural networks? Journal of Statistical Mechanics: Theory and Experiment, 2024(10), p.10420.
Cagnetta, F., Favero*, and Wyart, M., 2023. What Can Be Learnt With Wide Convolutional Neural Networks. In Proceedings of the 40th International Conference on Machine Learning (ICML), PMLR 202, pp. 3347–3379.
These authors contributed equally.