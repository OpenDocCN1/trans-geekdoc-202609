# 4.1.2. MJSynth Dataset

Introduced by Jaderberg et al. [20], the MJSynth dataset encompasses 9 million images and 90,000 English words. The dataset’s creation involved a meticulous and deliberate process, ensuring its suitability for a broad array of applications. Font selection within the dataset is marked by its dynamic nature, with each image being meticulously generated through random font selection from a pool of over 1400 fonts sourced from Google Fonts. This deliberate randomness in font selection significantly contributes to the dataset’s diversity and realism, guaranteeing that the text images portray an extensive variety of font styles.

Furthermore, the MJSynth dataset is distinct in its blending of data from various sources. The dataset enriches its corpus by combining each image layer with random crops extracted from images featured in the training dataset of SVT. This blending process introduces a substantial degree of diversity into the dataset. The blending operations incorporate a range of alpha blend modes, including ‘normal’, ‘add’, ‘multiply’, ‘max’, and others, further amplifying the dataset’s complexity and richness.

Given its vast data volume and the relevance of its text content to the experiments, this study employs this dataset for model pre-training, aiming to enhance the model’s performance ceiling. Figure 7 exhibits a selection of images from the MJSynth dataset.

![](bbox=[0.14, 0.4, 0.86, 0.56])

Figure 7. MJSynth dataset.

# 4.2. Implementation Details

Throughout the research, PyTorch served as the primary framework for method implementation. High-resolution images were resized to dimensions of 128 × 32 pixels, while the degraded low-resolution images were adjusted to 64 × 16 pixels. All experiments were conducted on a NVIDIA GeForce RTX 3090 GPU equipped with 24 GB of memory. The Adam optimizer was employed for model training, with a batch size set to 16.

Model training utilized the Adam optimizer with a batch size of 16. The training procedure was divided into two distinct phases. In the initial phase, the training dataset comprise the extensive MJSynth dataset, which consists of 9 million images. Low-resolution images were generated using the pixel-level degradation process introduced in this research. Subsequently, the test dataset encompassed the three challenging test sets from the TextZoom dataset. In the second phase of training, the dataset comprised 17,367 images from the TextZoom training set. Importantly, no modifications were made to the low-resolution images during this stage. The test dataset remained consistent with the first phase evaluation.

When training on the MJSynth dataset, the learning rate was established at $1 \times 10^{-4}$, while for fine-tuning using the TextZoom dataset, it was set at $7 \times 10^{-4}$. For evaluation recognition accuracy, OCR models such as ASTER, MORAN, and CRNN were employed, assessed using the official PyTorch code released on GitHub. To ensure fairness, the study adhered to prior practices in text image super-resolution research, converting all uppercase letters to lowercase. Experimental outcomes were gauged using OCR recognition rates to evaluate the model’s performance.