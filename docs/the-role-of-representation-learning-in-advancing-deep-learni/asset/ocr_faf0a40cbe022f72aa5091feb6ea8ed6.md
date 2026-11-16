```
Algorithm 3.1 Meta-learning the base network [91]
Input: \(\alpha\): learnable inner step size
Input: \(\beta\): outer step size hyperparameter
Uniformly initialize base network \(\theta\) and encoder \(\psi\)
while not do do
Sample mini-batch \(\mathcal{B}\) of data \(\{(\mathbf{x}_{ij}, y_{ij})\}_{i \in \mathcal{D}}_{j \in \mathcal{B}}\)
Initialize functas \(\phi_j \leftarrow 0 \forall j \in \mathcal{B}\) do
for \(t = 1\) to \(T_{inner}\) and \(\forall j \in \mathcal{B}\) do
\(m_j = \psi(\phi_j)\)
\(\phi_j \leftarrow \phi_j - \alpha \nabla_{\phi_j} \mathcal{L}(\{f_{\theta, m_j}(\mathbf{x}_{ij}), y_{ij}\}_{i \in \mathcal{D}})\)
end for
\(\theta \leftarrow \theta - \beta \nabla_\theta \sum_{j \in \mathcal{B}} \mathcal{L}(\{f_{\theta, \psi, m}(\mathbf{x}_{ij}), y_{ij}\}_{i \in \mathcal{D}} |_{m=\psi(\phi_j)}\)
\(\psi \leftarrow \psi - \beta \nabla_\psi \sum_{j \in \mathcal{B}} \mathcal{L}(\{f_{\theta, \psi, m}(\mathbf{x}_{ij}), y_{ij}\}_{i \in \mathcal{D}} |_{m=\psi(\phi_j)}\)
end while
```

tions by introducing a damping factor to render the function semi-periodic [237] or by employing complex Gabor-wavelet activations [226]. While these approaches show potential, our work adheres to the basic sinusoidal activation function proposed by [245] and concentrates on its application for super-resolution tasks.

# C.1.3 Swin Transformer Model

In this subsection, we expand on details of the architecture of the Swin transformer, shown in fig. C.1.2.

**Shifting Window.** We employ the shifting windows mechanism introduced with the Swin Transformer [172]. In the first layer, the image is divided into non-overlapping windows of a fixed size (see fig. 5.4). In the subsequent layer, the windows are shifted by a certain stride (typically half the window size). Applying self-attention to such windows is computationally inefficient due to the varying sizes of border windows. Most deep learning frameworks are optimized for fixed-size tensors. Therefore, we cyclically shift the data by half a window. In a cyclic shift, the data (e.g., pixels) that are shifted out of the frame are repositioned on the opposite side of the axis. The window partition is then readjusted to ensure consistent size. To prevent border window fragments from attending to each other, we apply an attention mask (marked by the orange line). In practice, the attention mask can be precomputed, and during the forward pass, only the data needs to be cyclically shifted. The