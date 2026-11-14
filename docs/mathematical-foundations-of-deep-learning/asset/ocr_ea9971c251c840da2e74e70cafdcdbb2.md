data efficiently while maintaining interpretability. Liu et. al. (2024) [217] extended Graph Convolutional Networks (GCNs) by integrating Fourier analysis and spectral wavelets to improve graph expressivity. It bridges the gap between frequency-domain analysis and graph embeddings, making GCNs more effective for complex data structures. Vlasic (2024) [218] presented a Fourier series-inspired feature mapping technique to encode classical data into quantum circuits. It demonstrates how Fourier coefficients can enhance the representational capacity of quantum models, leading to better compression and generalization. Kim et. al. (2024) [219] introduced Neural Fourier Modelling (NFM), a novel approach to representing time-series data compactly while preserving its expressivity. It outperforms traditional models like Short-Time Fourier Transform (STFT) in retaining long-term dependencies. Xie et. al. (2024) [220] explored how Fourier basis functions can be used to enhance the expressivity of tensor networks while maintaining computational efficiency. It establishes trade-offs between expressivity and model complexity in machine learning architectures. Liu et. al. (2024) [221] integrated spectral modulation and Fourier transforms into implicit neural representations for text-to-image synthesis. Fourier analysis improves global coherence while preserving local expressivity in generative models. Zhang (2024) [222] demonstrated how Fourier and Lock-in spectrum techniques can represent long-term variations in mechanical signals. The Fourier-based decomposition allows for more expressive representations of mechanical failures and degradation. Hamed and Lachiri (2024) [223] applied Fourier transformations to speech synthesis models, improving their ability to transfer expressive content from text to speech. Fourier series allows capturing prosody, rhythm, and tone variations effectively. Lehmann et. al. (2024) [224] integrated Fourier-based deep learning models for seismic activity prediction. It explores the expressivity of Fourier Neural Operators (FNOs) in capturing wave propagations in different geological environments.

The Fourier analysis of expressivity in neural networks seeks to rigorously quantify how neural architectures, characterized by their depth and width, can approximate functions through the decomposition of those functions into their Fourier spectra. Consider a square-integrable function \( f : \mathbb{R}^d \rightarrow \mathbb{R} \), for which the Fourier transform is defined as

```
\hat{f}(\xi) = \int_{\mathbb{R}^d} f(\mathbf{x})e^{-i2\pi\xi\cdot\mathbf{x}} d\mathbf{x}
```

where \( \xi \in \mathbb{R}^d \) represents the frequency. The inverse Fourier transform reconstructs the function as

```
f(\mathbf{x}) = \int_{\mathbb{R}^d} \hat{f}(\xi)e^{i2\pi\xi\cdot\mathbf{x}} d\xi
```

The magnitude \( |\hat{f}(\xi)| \) reflects the energy contribution of the frequency \( \xi \) to \( f \). Neural networks approximate \( f \) by capturing its Fourier spectrum, but the architecture fundamentally governs how efficiently this approximation can be achieved, especially in the presence of high-frequency components.

For shallow networks with one hidden layer and a finite number of neurons, the universal approximation theorem establishes that

```
f(\mathbf{x}) \approx \sum_{i=1}^n a_i\phi(\mathbf{w}_i \cdot \mathbf{x} + b_i)
```

where \( \phi \) is the activation function, \( \mathbf{w}_i \in \mathbb{R}^d \) are weights, \( b_i \in \mathbb{R} \) are biases, and \( a_i \in \mathbb{R} \) are coefficients. The Fourier transform of this representation can be expressed as

```
\hat{f}(\xi) \approx \sum_{i=1}^n a_i\hat{\phi}(\xi)e^{-i2\pi\xi\cdot\mathbf{b}_i}
```