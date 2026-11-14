random cropping, brightness normalization, horizontal and vertical flipping, and small elastic distortions to enhance the learning process.

For handling the imbalance problem and enhancing the robustness of the model towards different imaging conditions, these techniques are applied to minority classes specifically. To ensure computational efficiency, all images are resized to 256 x 256 pixels upon preprocessing. Pixel intensity values are normalized to bring them within the range of [0, 1]. In addition, features such as nucleus area, perimeter, compactness, and nucleus-to-cytoplasm ratio parameters, which are all known to be important in cytological analysis are derived based on the nucleus and cytoplasm segmentation masks.

The existence of single-cell segmentation masks is an essential element of this dataset, allowing it to be applied to detection and segmentation-based approaches in conjunction with classification. The Herlev dataset provides a solid foundation for developing and contrasting cervical cancer classification systems based on contextual and morphological information due to its richness.

# Table 1: Class-wise distribution of the Herlev Pap smear dataset.

| S. no. | Diagnostic class | Abbreviation | Number of images |
| :--- | :--- | :--- | :--- |
| 1 | Normal squamous epithelial | NS | 242 |
| 2 | Normal columnar epithelial | NC | 146 |
| 3 | Mild dysplasia | MD | 182 |
| 4 | Moderate dysplasia | MOD | 146 |
| 5 | Severe dysplasia | SD | 197 |
| 6 | Carcinoma in situ | CIS | 182 |
| 7 | Rare/undefined atypical cells | Outlier | 26 |
| | Total | | 917 |

# Table 2: Dataset split summary: train, validation, and test sets by class (stratified sampling).

| No. | Class name | Total images | Training set (70%) | Validation set (15%) | Test set (15%) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Normal squamous epithelial (NS) | 242 | 169 | 36 | 37 |
| 2 | Normal columnar epithelial (NC) | 146 | 102 | 22 | 22 |
| 3 | Mild dysplasia (MD) | 182 | 127 | 27 | 28 |
| 4 | Moderate dysplasia (MOD) | 146 | 102 | 22 | 22 |
| 5 | Severe dysplasia (SD) | 197 | 138 | 30 | 29 |
| 6 | Carcinoma in situ (CIS) | 182 | 127 | 27 | 28 |
| 7 | Rare/atypical (outlier) | 26 | 18 | 4 | 4 |
| | Total | 917 | 783 | 168 | 166 |