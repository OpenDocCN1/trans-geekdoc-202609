# # Chapter 14. Neural networks for images

![](bbox=[0.05, 0.08, 0.95, 0.48])



One of the simplest and most widely used is known as MNIST [LeC+98; YB19]. This is a dataset of 60k training images of size 28 × 28 × 1 illustrating handwritten digits from 10 categories; see Fig. 3.19a for an illustration.

Nowadays since MNIST classification is considered “too easy”, so other datasets have been collected. A simple alternative to MNIST is known as FashionMNIST [XRV17]. This is a dataset of 60k images of size 28 × 28 × 1 illustrating clothing items from 10 categories; see Fig. 14.13a for an illustration.

Another grayscale dataset is EMNIST [Coh17] which is a dataset of ~730k images of size 28 × 28 × 1 illustrating handwritten digits and letters from 47 classes. For small color images, the most common dataset is CIFAR [KH09]. This is a dataset of ~50k images of size 32 × 32 × 3 representing everyday objects from 10 or 100 classes; see Fig. 14.13b for an illustration.

> 3. CIFAR stands for “Canadian Institute For Advanced Research”.