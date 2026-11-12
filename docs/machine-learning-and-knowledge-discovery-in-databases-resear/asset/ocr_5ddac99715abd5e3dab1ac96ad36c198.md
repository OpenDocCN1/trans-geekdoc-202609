**Gradient Flow Improvement.** Furthermore, when \( f \rightarrow 1 \), the gradient \( F'(x) \) has a peak near zero that helps maintain sufficient gradient flow through the layers, especially during backpropagation. This prevents gradients from vanishing in deeper layers and improves convergence.

In summary, the theoretical analysis shows that AB-STE effectively maintains gradient stability and smoothness through careful control of the blending factor \( f \) and the scaling parameter \( k \). The variance of the gradient \( F'(x) \) is reduced as \( f \) increases, ensuring stable updates, while the Lipschitz continuity of \( F'(x) \) guarantees smooth gradient flow, reducing the risk of vanishing or exploding gradients. By gradually increasing \( f \), AB-STE ensures effective gradient flow throughout the network, leading to improved convergence during training, particularly for deep binarized models.

# 4 Experimental Setup and Results

# 4.1 Datasets and Training Setup

This study uses two popular datasets commonly employed in the binary neural network literature: **CIFAR-10** [18] and **ImageNet ILSVRC-2012** [17].

The CIFAR-10 dataset consists of 50,000 training images and 10,000 testing images across 10 categories, with each image having a resolution of \( 32 \times 32 \) and three RGB color channels. The ImageNet ILSVRC-2012 dataset is a large-scale dataset with over 1.2 million training images and 50,000 validation images, each at a resolution of \( 224 \times 224 \), covering 1,000 categories.

To ensure a fair comparison with existing methods, we adopted similar training settings as other binary methods [1,19,20]. We used pre-processing techniques such as RandomCrop, RandomHorizontalFlip, and Normalize for both CIFAR-10 and ImageNet. The models were trained using Stochastic Gradient Descent (SGD) with an initial learning rate of 0.1, and a cosine learning rate decay schedule was employed to gradually reduce the learning rate during training.

For CIFAR-10, the models were trained for 1,000 epochs, while for ImageNet, training was conducted for 250 epochs. The hyperparameter \( k \), which controls the iterative nature of the adaptive blending, was fixed at 10 throughout the experiments. We varied the blending factor \( f \) between 0.2 and 0.8 to study its impact on training performance and gradient stability. Importantly, parameter quantization was employed during training, whereas activations were kept at full precision to maintain expressive feature representations and ensure stable gradient flow.

# 4.2 Results and Analysis

The proposed Adaptive Blended Straight-Through Estimators (AB-STE) were evaluated using the CIFAR-10 and ImageNet datasets, focusing on both accuracy and training stability compared to the existing state-of-the-art methods.