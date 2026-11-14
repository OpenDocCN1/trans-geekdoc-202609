# 3.2 Data Preprocessing

To ensure data consistency and enhance the performance of deep learning models, a rigorous preprocessing pipeline was implemented to address the image quality, scale, and lighting variations in the ChestX-ray14 dataset. To ensure compatibility with popular CNN architectures such as ResNet and DenseNet, all the images were initially downsampled uniformly from their original resolution of 1,024 × 1,024 pixels to 224 × 224 pixels. This lowered the computational load without sacrificing desirable diagnostic characteristics. To encourage faster convergence and uniform gradient flow through training, pixel intensities were subsequently scaled to the [0, 1] interval using division by 255.

Contrast limited adaptive histogram equalization (CLAHE) was employed to enhance contrast and render fine anatomical structures more visible; this method is particularly effective for low-contrast or underexposed radiographs. During training, a robust data augmentation method was employed in real time to address class imbalance and prevent overfitting. The model’s ability to generalize to unseen data was greatly improved by these augmentations, which comprised random horizontal flipping, minor rotations (±10°), translations, zooming (±10%), and brightness changes. Moreover, to reduce high-frequency noise while preserving essential edge and lesion details, a Gaussian blur filter with a standard deviation (σ) of 0.5 was applied. To eliminate images that were either overexposed or underexposed, which is often due to acquisition issues, outlier filtering was ultimately performed using histogram-based intensity thresholding. This preprocessing operation successfully normalized the dataset and prepared it for solid and accurate feature extraction in the next tasks.

# 3.3 Proposed Feature Extraction

MSAG-DFE is a robust, modular, and hierarchical feature extraction technique that combines the advantages of attention mechanisms with multi-scale convolutional learning to produce more discriminative and relevant features. Figure 2 shows the multi-scale fusion and Figure 3 depicts the attention mechanism framework.

**Step 1:** Load the input chest X-ray image \( I \in \mathbb{R}^{224 \times 224} \) from the preprocessed NIH ChestX-ray14 dataset.

**Step 2:** Initialize three parallel convolutional branches with kernel sizes 3×3, 5×5, and 7×7 to extract features at different scales.

**Step 3:** Pass the image through each branch to obtain multi-resolution feature maps:

```
\( F_k = \text{ReLU}(W_k \star I + b_k), k \in \{3, 5, 7\} \) (1)
```