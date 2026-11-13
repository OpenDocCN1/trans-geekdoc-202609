
### Manual Feature Extraction:

- **Texture Analysis:** For the extraction of texture features, grey level co-occurrence matrices (GLCM) can be used. These matrices allowed us to analyse contrast, correlation, energy, and homogeneity in the image. Retinal images have the potential to reveal valuable insights into different patterns.

- **Shape Analysis:** Shape analysis used to work with computing shape descriptors for the images such as area, perimeter, and eccentricity of segmented regions in retinal fundus and OCT images.

### Automated Feature Extraction:

- **Convolutional Neural Networks (CNNs):** CNNs are capable of learning hierarchical feature representations from raw image data. Through the utilisation of pre-trained models such as Inception-ResNet-V2 and EfficientNet, we were able to refine and optimise our predictions for diabetes by incorporating the relevant features from our collected datasets.

- **Principal Component Analysis (PCA):** PCA was conducted to identify the most significant features for understanding trends within the dataset.

Manual feature extraction is dependent on the user, which results in the interpretation of the specific characteristics that desire to be associated with an image. However, they may need to understand more complex patterns that can be detected by automated techniques like CNNs. While automated techniques are undeniably powerful, they do require significant computational resources and rely heavily on annotated data for training.

### 5.4 Model Training and Evaluation

To get diabetes prediction of the images, ML and DL Models should be used only after training them as well for its evaluation.

### Model Training:

**Training Data Split:** The dataset was split into training, validation and test sets using an 80–10–10 ratio in order to guarantee that the evaluation is robust.

**Training Process:** The models were trained using backpropagation and stochastic gradient descent (SGD) with optimal learning rates along with regularisation methods in order to prevent overfitting.

**Hyperparameter Tuning:** Changing hyperparameters to get the best performance of classifiers.

### Evaluation Metric:

- **Accuracy:** Measures the proportion of correctly predicted instances among the total instances.

- **Sensitivity (Recall):** Measures the model's ability to identify positive cases correctly.

- Specificity: Measures the ability of the model to identify negative cases.

- Area Under the Curve (AUC): Evaluates the model's ability to differentiate between positive and negative cases across different thresholds.

### Cross-Validation:

- K-Fold Cross-Validation: This technique was used to assess model performance and ensure that it generalises well to unseen data. In this study, 5-fold cross-validation was employed to validate the models.

While the chosen evaluation metrics comprehensively assess model performance, they can sometimes present a skewed view if the dataset is imbalanced. For instance, high accuracy in a dataset with a majority class can be misleading. Thus, metrics like AUC, which account for the balance between sensitivity and specificity, are crucial for a more balanced evaluation. Furthermore, while necessary, hyperparameter tuning can be computationally intensive and time consuming.

## 6. Experimental Setup

Table 3. Datasets from various sources.

| Dataset Name | Imaging Modality | Number of Images | Key Features | Source |
| --- | --- | --- | --- | --- |
| Messidor | Retinal Fundus Photography | 1,200 | Diabetic retinopathy grading, lesion annotations | Publicly available |
| Kaggle Diabetic Retinopathy | Retinal Fundus Photography | 88,702 | Lesion annotations, severity levels | Kaggle |
| Zivot | Thermal Imaging | 269 | Skin temperature variations | Clinical collaborations |
| OCT Dataset | Optical Coherence Tomography (OCT) | 5,000 | Retinal thickness, fluid accumulation | Clinical collaborations |
| UK Biobank | Multi-Modal Imaging | 500,000 | Comprehensive health data, including MRI scans | UK Biobank |

Table 4. Tools used for analysis.

| Tool Name | Purpose |
| --- | --- |
| Python | Programming language for data analysis and machine learning |
| TensorFlow/Keras | Deep learning frameworks for building and training models |
| OpenCV | Computer vision library for image processing |
| Scikit-learn | Machine learning library for model building and evaluation |
| Matplotlib/Seaborn | Visualisation libraries for plotting data and results |
| Anaconda | Distribution for managing Python packages and environments |

### Data Collection:

Collected images from the annotated dataset ensured data diversity including imaging modalities: fundus photography, OCT, thermal imaging.

### Data Preprocessing:

- Noise Reduction: Applied Gaussian and median filtering techniques to reduce image artifacts.
- Normalization: Scaled image pixel values using min-max normalization from 0 to 1.
- Segmentation: Segment relevant structures (e.g. optic disc and cup, blood vessels in retinal images, optic cup in OCT images, OCT surfaces) using thresholding and edge detection methods.
- Data Augmentation: Augmented dataset diversity, perform augmentation (rotation, flipping, cropping, etc.)
- Dimensionality Reduction: Applied Principal Component Analysis (PCA) to reduce the dimensionality.

### Feature Extraction:

- Manual Features: Extracted the texture and shape features using GLCM and grey-level co-occurrence matrix (GLCM) and shape descriptors.
- Hand-crafted: ...
- Features: Used pre-trained CNNs (Inception-V3, EfficientNet-V2) for feature extraction.

### Model Training:

- Split the dataset into training (80%), validation sets (10%) and test sets (10%).
- Train CNN models using gradient descent (SGD) and backpropagation, optimizing hyperparameters using grid search and validation to find optimum learning rates, batch sizes, and the number of layers.

### Model Evaluation:

- Perform K-fold cross-validation (K=5) to assess the model's generalization ability.

### Result Visualization:

- Visualize model performance using confusion matrices, and ROC curves.
- Compare performance across different models and imaging modalities.

Fig. 2. Experimental protocol [26].

Table 5. The below metrics were used to evaluate the performance of the machine learning model.

| Metric | Definition |
| :--- | :--- |
| Accuracy | The proportion of correctly predicted instances among the total cases. |
| Sensitivity (Recall) | The ability of the model to correctly identify positive cases (true positives/(true positives + false negatives)). |
| Specificity | The ability of the model to correctly identify negative cases (true negatives/(true negatives + false positives)). |
| Precision | The proportion of true positives among all positive predictions (true positives/(true positives + false positives)). |
| F1 Score | The harmonic mean of precision and recall balances the two metrics. |
| Area Under the Curve (AUC) | The area under the Receiver Operating Characteristic (ROC) curve indicates the model's ability to distinguish between positive and negative cases. |
| Confusion Matrix | This table describes the classification model's performance, showing true positives, false positives, and false negatives. |

## 7. Results

The comparative analysis of different machine learning models reveals insights into their performance for diabetes prediction using medical images.

- a) **Inception-ResNet-V2**: This model demonstrated high accuracy and AUC, indicating its strong ability to distinguish between diabetic and non-diabetic cases. The deep architecture of Inception-ResNet-V2 allows it to capture intricate patterns in retinal images. However, the complexity of the model requires substantial computational resources and large amounts of training data to avoid overfitting.

- b) **EfficientNet**: EfficientNet achieved the highest performance across most metrics, including accuracy, sensitivity, and AUC. Its efficient scaling approach allows for better utilization of computational resources without compromising performance. Like Inception-ResNet-V2, EfficientNet requires extensive computational power and high-quality annotated data.

- c) **CNN (Custom Architecture)**: The custom architecture stood out as the optimal choice in terms of performance and computational cost. As a result of the product's initial development for these datasets, higher sensitivities and specificities were observed. Custom architectures may need to improve their ability to generalise with other datasets, which could require some additional fine-tuning of hyperparameters.

- d) **Support Vector Machine (SVM)**: SVM produced impressive results in terms of precision and specificity. Binary classification tasks are well-suited for this purpose due to their ease of implementation. However, deep learning methods outperformed SVM in terms of both sensitivity and AUC measures. This

### Performance Metrics

![](img/a797255277085a0fa8aa2736cb720e31_36_0.png)

Graph 1. The performance metrics of the machine learning models used in this study. These metrics include accuracy, sensitivity (recall), specificity, precision, F1 score, and the area under the curve (AUC).
