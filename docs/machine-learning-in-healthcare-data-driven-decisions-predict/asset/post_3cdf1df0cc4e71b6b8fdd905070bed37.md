
Whereas categorical variables are imputed through k-Nearest Neighbor (KNN) imputation (k = 5) in the Euclidean distance, continuous attributes are imputed through the Multivariate Imputation by Chained Equations (MICE) method. Normalization is done through Z-score normalization, and isolation forests are employed for detecting outliers

Z = (X - μ) / σ

where μ and σ represent the mean and standard deviation of the attribute.

Before scaling every image to 224 × 224 pixels for CNN architecture compatibility, imaging data preparation includes histogram equalization for enhancing contrast. Image denoising is done using Non-Local Means Denoising (NLM), and data augmentation techniques such as rotation (±15°), horizontal flip, and random zoom (±10%) are performed to enhance generalization and reduce overfitting. Pixel values are rescaled to the range [0, 1] by dividing by 255.

## 3.3 Feature Extraction

An autoencoder model is employed to derive features from tabular data. A deep autoencoder, with three encoding layers (512, 256, and 128 neurons) and three decoding layers, symmetrically reconstructs the input for extracting latent features. Compressed representations are utilized for subsequent classification by the bottleneck layer of the encoder. As a point of comparison, a fully ResNet-50 Convolutional Neural Network is employed to extract visual data from ChestX-ray14. The last fully connected layer of the pretrained ResNet-50 is replaced with a customized classification layer of 128 units that was trained on the medical dataset.

The L2 normalization comes after Global Average Pooling (GAP) is applied to obtain the intermediate features from the second last layer. A Long Short-Term Memory (LSTM) network is employed in MIMIC-III to learn temporal features from time-series inputs. The network employs a hidden layer dimension of 128 to learn dynamic relationships, without ceasing to monitor patient vitals (like blood pressure, oxygen saturation, and heart rate hourly). To establish a multimodal feature space, they are concatenated with autoencoder and image features. Principal Component Analysis (PCA) is applied to reduce the dimensionality, at the expense of 95% variance to keep computing cost and redundancy low.

Start
Input Multimodal Data (EHR + Imaging + Signals)
Data Preprocessing (Missing Value Imputation, Normalization, Augmentation)
Structured Features via MLP (EHR)
Temporal Features via BiLSTM (Signals)
Visual Features via CNN (Imaging)
Hybrid Feature Fusion (Self-Attention + GNN) *
Fully Connected Layers for Risk Prediction
SHAP Explainability (Feature Attribution) *
Initialize Learning Rate
Bayesian Adaptive Scheduler *
Update Learning Rate based on Convergence
Converged?
Final Risk Prediction Output
End

Figure 1: Proposed framework.

## 3.4 Hybrid Attention-Driven Network Algorithm

To overcome the major limitations of existing ML frameworks in the healthcare sector, the Hybrid Attention-Driven Network (HAD-Net) was proposed as a trustworthy and interpretable multimodal learning model. Existing approaches often fall short of being interpretable, tend to generalize poorly across diverse populations of patients, and fuse heterogeneous data sources such as EHRs, physiological signals, and medical images in an acceptable way. HAD-Net achieves modeling of temporal, spatial, and structural dependencies in multimodal data through the synergy of self-attention mechanisms, graph neural networks (GNNs), and bidirectional long short-term memory (BiLSTM) units. The method includes SHAP (Shapley Additive exPlanations) for enhanced model prediction transparency and employs a Bayesian Adaptive Learning Scheduler for optimizing convergence dynamically. Figure 1 shows the proposed framework.

- Step 1: Clean and normalize EHR data \( X_{EHR} \). Handle missing values using statistical or learned imputation methods.
- Step 2: Resize and normalize input medical images (e.g., chest X-rays) \( X_{IMG} \). Augment data using rotation, flipping, and contrast variation.
- Step 3: Extract sequences of physiological signals (e.g., heart rate, SpO\(_2\)) as time series \( X_{TS} \), with time steps aligned across patients.
- Step 4: Encode categorical features using embedding layers and concatenate with numerical features to form structured representation \( f_{ehr} \in R^{d_1} \)
- Step 5: Use a pretrained CNN (e.g., ResNet-50) to extract visual features

```
\( f_{img} = CNN(X_{IMG}), f_{img} \in R^{d_2} \)
```

- Step 6: Pass physiological time series through BiLSTM to capture bidirectional dependencies

```
\( f_{ts} = BiLSTM(X_{TS}), f_{ts} \in R^{d_3} \)
```

- Step 7: Construct a domain-specific graph \( G = (V, E) \), where nodes represent clinical entities (e.g., symptoms, diagnoses) and edges encode relations (co-occurrence, causality).
- Step 8: Apply GNN (e.g., GAT or GCN) to learn contextual embeddings

```
\( h_v^{(l+1)} = \sigma \left( \sum_{u \in N(v)} a_{vu} W h_u^{(l)} \right) \)
```

where \( a_{vu} \) are attention weights over neighbors.

- Step 9: Apply multi-head self-attention to fuse \(f_{ehr}, f_{img}, f_{ts}, h_G\)

\(SA(Q, K, V) = softmax \left( \frac{QK^T}{\sqrt{d_k}} \right) V\)

where \(Q, K, V\) are projections of inputs from each modality.

- Step 10: Fuse modality embeddings using learned attention scores

\(f_{fused} = \sum_{i=1}^M a_i f_i \text{ where } a_i = \frac{\exp(w^T f_i)}{\sum_j \exp(w^T f_j)}\)

- Step 11: Concatenate or merge fused representation with GNN output

\(f_{context} = Concat(f_{fused}, h_G)\)

- Step 12: Initialize learning parameters using Bayesian Optimization (e.g., learning rate, dropout rate, hidden size).

- Step 13: Use validation loss to adaptively adjust learning rate

\(\eta_{t+1} = \begin{cases} \eta_t \cdot \gamma, & \text{if no improvement for k epochs} \\ \eta_t, & \text{otherwise} \end{cases}\)

- Step 14: Pass final embeddings through dense layers for risk prediction

\(\hat{y} = Softmax(Wf_{context} + b)\)

- Step 15: Compute cross-entropy loss for multi-class/multi-label predictions

\(L_{CE} = - \sum_i y_i log(\hat{y}_i)\)

- Step 16: Apply SHAP on the trained model to compute feature importance for interpretability

\(\phi_i = E_{S \subseteq F \setminus \{i\}} \left[ \frac{|S|!(|F| - |S| - 1)!}{|F|!} (f(S \cup \{i\}) - f(S)) \right]\)

- Step 17: Map predicted probability to risk category (low, medium, high) using thresholds defined by clinicians.

- Step 18: Generate SHAP-based visual plots to explain decisions (summary plots, force plots, and decision plots).

- Step 19: Loop in expert feedback for active learning or model refinement. Store hard-to-predict cases for future fine-tuning.

Through addressing the basic limitations of conventional ML paradigms, the HAD-Net algorithm offers an end-to-end, smart, and explainable solution for healthcare prediction analytics. HAD-Net constructs a consistent multimodal representation space by integrating sequential physiological signals, unstructured imaging data, and structured EHR information. Important dependencies between and within modalities can be modeled by the system using GNN-based relational learning and attention-based fusion. Though SHAP-based interpretability provides clinicians with evidence-based reasons for risk, the Bayesian learning scheduler improves training generalizability and stability. In totality, HAD-Net is an adaptable and clinically reliable algorithm that aids precision medicine in bridging the interpretability-prediction power gap.

## 4 Experimental Results

The experimental evaluation of the devised HAD-Net architecture was performed in a closely monitored computing environment. Python 3.9 with PyTorch 1.13 for DL extensions and Scikit-learn 1.2 for comparative ML baseline benchmarking was used to deploy the end-to-end pipeline. The machine on which the experiments were carried out had an Intel Xeon Silver 4216 processor, Ubuntu 20.04, 256 GB RAM, and NVIDIA RTX A6000 GPU (48 GB VRAM). Standard clinical ML metrics, e.g., accuracy, precision, recall, area under the receiver operating characteristic curve (AUROC), and F1-score, were used to evaluate performance. These measures were averaged across five times of cross-validation to ensure robustness across data partitions.

The model was tested on a combined multimodal dataset that was built by combining EHRs in the MIMIC-III clinical database with imaging data in the NIH ChestX-ray14 dataset for the sole reason of verifying the usefulness of HAD-Net. EHRs were z-score normalized for numerical attributes and one-hot encoded for categories, while imaging data was histogram equalized and resized to 224 × 224 pixels for normalization. A k-nearest-neighbors strategy was applied to impute missing values with reference to the patient comorbidities and demographics. Early stopping and dropout (rate = 0.3) were used to avoid overfitting. A hybrid Adam-Bayesian adaptive learning scheduler optimizer for dynamic learning rate updating was used to train the HAD-Net.

HAD-Net was compared with traditional ML methods (logistic regression and random forest) and sophisticated deep architectures, i.e., a CNN-BiLSTM hybrid architecture and a transformer-based multimodal architecture, for comparative investigation. Grid search was utilized to tune all baseline models. The HAD-Net outperformed the best traditional baseline (CNN-BiLSTM) by 9.5% in AUROC and 12.4% in F1-score with an AUROC of 94.3%, a classification accuracy of 91.7% (Figure 2), and an F1-score of 92.1% (Figure 3). The inclusion of SHAP (SHapley Additive exPlanations) further increased the model’s decision transparency and the ability to identify clinically important biomarkers like abnormal PaO2/FiO2 ratios, troponin elevation, and radiographic evidence of pulmonary infiltrates. Table 1 shows the tuning parameters.
