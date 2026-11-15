Table 5.3 Accuracy comparison with the SOTA methods on the ImageNet dataset. “W” and “A” refer to the bit width of weights and activations, respectively.

| Method | Year | W/A | Top-1 |
| :--- | :--- | :--- | :--- |
| ResNet18 | 2016 | 32/32 | 69.6% |
| BWN | 2016 | 1/32 | 60.8% |
| BinaryNet | 2016 | 1/1 | 42.2% |
| DoReFa-Net | 2016 | 1/1 | 52.5% |
| XNOR-Net | 2016 | 1/1 | 51.2% |
| HWGQ | 2017 | 1/2 | 59.6% |
| TBN | 2018 | 1/2 | 55.6% |
| Bireal-Net | 2018 | 1/1 | 56.4% |
| XNOR++ | 2019 | 1/1 | 57.1% |
| Quantization Networks | 2019 | 1/1 | 53.6% |
| Bop | 2019 | 1/1 | 54.2% |
| IR-Net | 2020 | 1/1 | 58.1% |
| LNS | 2020 | 1/1 | 59.4% |
| RBNN | 2020 | 1/1 | 59.9% |
| ReActNet | 2020 | 1/1 | 65.9% |
| **CBN-Net (K = 2)** | 2021 | 1/1 | **66.8%** |

# 5.4.4 Complexity analysis

We evaluated the computational complexity of the proposed CBN-Net on the ImageNet dataset and compared it with other binary neural networks. Table 5.4 lists the state-of-the-art BNNs with over 60% Top-1 accuracy on the ImageNet dataset, including ABC-Net, BENN, Group-Net, and the Circulant BNN [16]. These methods generally made a trade-off between efficiency and accuracy, and used multiple subnets or bases of binary matrices to reduce the drop of classification accuracy.

The computational complexity was measured by the total operations (OPs), which consisted of floating-point operations and binary operations, and we used the same OPs estimation procedure as [37]. In summary, the CBN-Net achieved the 1.8% to 5.7% higher Top-1 classification accuracy compared to these methods. Moreover, the CBN-Net was the most efficient method in terms of inference OPs compared to the state-of-the-art binary neural networks. It was worth noting that even containing two subnets, the CBN-Net was still 5.58× to 8.62× more efficient than the full-precision network due to its binary representation and binary operation.