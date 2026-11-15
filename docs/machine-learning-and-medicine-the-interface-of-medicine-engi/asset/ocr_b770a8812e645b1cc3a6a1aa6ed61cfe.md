super-resolution models, focusing on reducing the discrepancies between the actual and computed outputs to enhance image quality.

# 4. Experiments and Results

# 4.1. The Dataset

In our research, we harness specialized datasets that are designed specifically for super-resolution tasks, such as Figshare and the Kidney Stone collections. These datasets are expertly structured to facilitate the training and evaluation of sophisticated super-resolution models. As integral components of our study, they include a comprehensive array of images meticulously prepared and annotated to support the development of cutting-edge image enhancement technologies. These datasets are instrumental in advancing techniques that precisely enhance image resolution, catering to the unique demands of super-resolution applications. Each dataset includes a diverse set of images from various scenarios, enriched with detailed annotations that delineate critical areas within the images, thereby providing high-quality data crucial for refining model accuracy and performance. The characteristics of the datasets used for testing, namely Figshare and Kidney Stone, are presented below. These datasets were carefully selected to provide a diverse range of medical images, ensuring that the proposed model could be effectively evaluated across different medical imaging modalities (Table 1).

# Table 1. Characteristics of the Figshare and Kidney Stone datasets used in our experiments.

| Dataset | Number of Images | Image Resolution | Modality | Description |
|---|---|---|---|---|
| Figshare | 500 | 512 x 512 | CT and MRI | A diverse set of medical images annotated for super-resolution tasks, covering multiple anatomical regions. |
| Kidney Stone | 300 | 256 x 256 | Ultrasound | A specialized dataset focusing on kidney stone images, annotated for improved clarity in super-resolution tasks. |

Table 1 provides a clear overview of the datasets used, detailing the number of images, their resolution, the imaging modality, and a brief description of the dataset content. Including this information allows for better reproducibility of this study and transparency regarding the data used.

# 4.2. Data Preprocessing

The data preprocessing phase for the Figshare and Kidney Stone datasets, which are tailored for medical super-resolution tasks, involves a pipeline rigorously designed to enhance the robustness and accuracy of the proposed model. Initially, all images are resized to ensure uniformity, meeting the specific input requirements of the proposed model and maintaining consistency across the dataset. Considering the variability in medical imaging, such as differing modalities and scan qualities, we introduce a series of augmentations. These adjustments include random rotations, flips, and variations in brightness and contrast, which help to mimic the diverse conditions found in real-world medical settings. Additionally, to replicate common imaging challenges like noise and slight blurring, which may occur due to machine imperfections or patient movement, Gaussian noise and blurring are applied. Through this preparation process we aim to acclimate the model to potential real-world imperfections it might encounter.

Normalization of each image follows, standardizing pixel values to align with the neural expectations of the proposed model, thus promoting stable and efficient learning. If the datasets include specific annotations, such as regions of interest around kidney stones, these are meticulously adjusted to maintain accuracy after image transformations. Lastly, to ensure comprehensive training and prevent model bias, we balance the dataset by