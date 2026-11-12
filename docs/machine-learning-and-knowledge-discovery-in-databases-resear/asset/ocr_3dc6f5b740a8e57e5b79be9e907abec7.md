# Gradient Magnitude Comparison Over 1000 Epochs: ReSTE vs. AB-STE

![](bbox=[0.19, 0.1, 0.83, 0.33])

Fig. 4. Training of ResNet-18 with CIFAR-10 dataset

These results demonstrate that AB-Tanh-STE and AB-ArcTan-STE improve the accuracy of BNNs while significantly reducing training time and computational overhead, making them well-suited for efficient hardware deployment without sacrificing model performance.

# 4.5 Gradient Analysis

In Fig. 4, we present a comparison of the mean gradient magnitude across training epochs for ReSTE (blue) and the proposed AB-Tanh-STE (red). The results demonstrate that AB-STE maintains higher gradient magnitudes in the early training phase, ensuring a stronger learning signal and preventing premature convergence. In contrast, ReSTE exhibits a faster decay in gradient magnitudes, potentially limiting the network's ability to explore the optimization landscape effectively during initial training.

As training progresses, AB-STE stabilizes the gradient magnitudes at a consistently higher level compared to ReSTE, facilitating smoother and more structured training dynamics. The gradual decay of gradients in AB-STE ensures that weight updates remain effective, preventing the issue of vanishing gradients commonly observed in deep networks. In contrast, ReSTE experiences notable fluctuations and sharp drops in gradient magnitude, particularly after epoch 200, suggesting less stable weight updates, which could impact model robustness and convergence stability. Beyond epoch 400, AB-STE exhibits lower gradient variance, indicating that it allows for more controlled and adaptive optimization steps. The consistent gradient flow observed in AB-STE contributes to improved training efficiency, ensuring that the network retains sufficient gradient magnitudes for meaningful updates while avoiding instability. On the other hand,