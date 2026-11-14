
Structured clinical data like age, sex, comorbidities, NIHSS scores, and corresponding laboratory results, including important patient demographics and stroke severity. Moreover, the data include multimodal MRI scans like DWI, FLAIR, and ADC that provide accurate anatomical and pathological characteristics of ischemic lesions and adjacent brain tissue. These imaging modalities facilitate high-level spatial analysis of stroke effects. Functional outcome labels in the form of mRS scores, commonly measured at 90 days following stroke, provide a standardized measure of disability and recovery. The combination of clinical factors, high-resolution imaging, and outcome data provides strong modeling of risk stratification and long-term functional prediction to allow the design of advanced hybrid learning schemes.

## 3.2 Data Preprocessing

For model preparedness and quality maintenance of the data, stringent preprocessing operations are carried out on both structured data and imaging data. Ordered clinical variables like age, NIHSS scores, and laboratory values are z-score normalized to standardize feature measurements and enhance model convergence. Random rotations, cropping, and changes in contrast are used on MRI scans in imaging data to simulate variability in anatomical presentation and image acquisition, enhancing model robustness and generalization. The augmentations are especially valuable for training DL models to identify stroke features across various conditions. Missing values in the structured dataset are also filled in by using a clinical-knowledge-driven imputation scheme. It utilizes domain-specific rule-based and practical clinical correlations (such as the estimation of missing blood glucose values based on the foundation of well-established comorbid conditions such as diabetes) to calculate more physiologically reasonable values than would otherwise be calculated under regular statistical procedure. This modified preprocessing pipeline guarantees integrity and functionality of the dataset to utilize in later hybrid model training, without negatively impacting such critical clinical and imaging characteristics essential for the prediction of stroke outcomes [21].

## 3.3 Model Architecture

This work introduces a new multimodal ML paradigm that combines multimodal patient information for risk stratification and functional outcome prediction in stroke survivors. The structure is a 3D CNN for imaging [22], a GNN [23] for clinical relations, and conventional ML for hand-crafted features. These different representations are combined into a shared latent vector optimized via multitask learning. This facilitates accurate, interpretable predictions through the use of complementary data sources and task-specific tasks. The model architecture for the prediction of stroke survivors is shown in Figure 1.

![](img/106ef0dba620d314f9842503e8ef40c8_77_0.png)

Figure 1: Proposed model architecture for stroke prediction.

### 3.3.1 Deep CNN for Imaging Data

A 3D CNN is used to scan volumetric CT/MRI images and obtain high-level spatial features related to ischemic lesions and cerebral abnormalities. The imaging data is processed in the CNN using several layers of 3D convolutions, batch normalization, and ReLU activation and captures hierarchical features like lesion size, location, and intensity. The last convolutional outputs are flattened and fed into a fully connected (FC) layer to generate a fixed-size image-derived embedding vector z_img, which is the learned representation of the patient's neuroanatomical state. This vector contains imaging-derived information critical to stroke severity and recovery prediction [24]. To mathematically represent the 3D CNN for imaging data formally, define the process in a layer-wise abstraction that captures the transformation from raw CT/MRI volumes to the embedding vector z_img: Let the volume of the input image be

```
X_{img} \in \mathbb{R}^{H*W*D} (1)
```

where \(X^{(0)} = X_{img}\), * denotes the 3D convolution operation, \(W^{(l)}, b^{(l)}\) are the weights and biases of layer l, BN is the batch normalization, and \(\sigma\) is the ReLU activation function. Hierarchical spatial features are extracted by stacking many of these layers.

The output tensor is flattened following the last convolutional layer, L

\(f_{flat} = \text{Flatten}\big(X^{(L)}\big)\)

A dense (FC) layer is traversed by the flattened vector and it is represented as follows:

\(z_{img} = \varnothing(W_{fc} \cdot f_{flat} + b_{fc})\)

where \(\varnothing\) is a nonlinear activation (ReLU or tanh) and \(W_{fc}, b_{fc}\) are the weights and bias of the FC layer. The output is given by

\(z_{img} \in \mathbb{R}^k\)

The fixed-length image-derived embedding that captures neuroanatomical information is this final vector, \(z_{img}\).

### 3.3.2 Graph Neural Network (GNN) for Clinical Data

Clinical information is represented by modeling with a GNN, with each patient as a node and edges representing clinical similarity, that is, Euclidean distance in normalized space of variables like age, laboratory values, and comorbidities. Each of the nodes is preloaded with a feature vector containing vitals, lab results, and categorical indicators of conditions such as hypertension or atrial fibrillation. Through iterative graph convolution operations, the GNN aggregates information from neighboring patients, enabling the model to learn relational patterns between clinically similar patients. The final node embedding \(z_{clin}\) summarizes the clinical profile in a latent space that captures complex inter-patient dependencies relevant to outcome prediction [25].

Let the clinical dataset be represented as a graph

\(G = (V, E)\)

where \(V\) is the set of nodes (patients) and \(E\) is the set of edges representing clinical similarity. Let \(X \in \mathbb{R}^{N*d}\), an input feature matrix, where each row \(x_i \in \mathbb{R}^d\) represents a patient's clinical features. Let \(A \in \mathbb{R}^{N*N}\) adjacency matrix of the graph, where \(a_{ij} = 1\), if node i is connected to node j, 0 otherwise. The self-loop is added as follows: \(\hat{A} = A + I\) and the degree matrix \(\hat{D}_{ij} = \sum_j \hat{a}_{ij}\).

A single GCN layer updates the node features as follows:

\(H^{(1)} = \sigma(\hat{D}^{-\frac{1}{2}} \hat{A} \hat{D}^{-\frac{1}{2}} X W^{(0)})\)

where \( W^{(0)} \in \mathbb{R}^{d \times k} \) is the learnable weight matrix, and \( \sigma(\cdot) \) is the nonlinear activation function (e.g., ReLU). The process is repeated for \( L \) layers as follows:

\( H^{(t+1)} = \sigma \left( \hat{D}^{-\frac{1}{2}} \hat{A} \hat{D}^{-\frac{1}{2}} X W^{(t)} \right) \), \( H^{(0)} = X \tag{8}\)

The final node embedding after \( L \) GNN layers for each patient node is

\( Z_{\text{clin},i} = H_i^{(L)} \in \mathbb{R}^k \tag{9}\)

where \( z_{\text{clin},i} \) is the learned embedding for the \( i \)th patient that summarizes clinical information and neighborhood influence. The graph embedding output is specified as follows:

\( Z_{\text{clin}} = H^{(L)} \in \mathbb{R}^{N*k} \tag{10}\)

Subsequent tasks like classification and fusion use this embedding matrix.

### 3.3.3 Clinical Feature Projection Using Traditional ML

In parallel, a selected set of handcrafted clinical features, such as stroke subtype, prior transient ischemic attacks (TIA), and pre-existing conditions, are fed into a ML model LightGBM [26]. These models are adept at handling tabular data with high interpretability. The outputs of these models are a probability vector representing risk predictions is then transformed into a dense embedding vector, \( z_\text{ml} \) using a learnable projection layer. This step ensures compatibility with other latent vectors and integrates expert-driven features into the hybrid framework. The manually created clinical feature vector, represented as follows:

\( X_\text{ml} \in \mathbb{R}^{d'} \tag{11}\)

which captures structured, manually curated patient information that are essential for stroke outcome prediction. These features are categorical and binary variables like stroke subtype (e.g., cardioembolic and thrombotic), history of previous episodes of TIA, and established risk factors or comorbidities like diabetes and hypertension. These domain-knowledge-informed features are selected on the basis of clinical significance and act as a starting point input to conventional ML algorithms, providing interpretability and taking advantage of expert knowledge to improve prediction quality. The handcrafted feature vector \( X_\text{ml} \) is passed into a traditional classifier. For a gradient-boosted decision tree model LightGBM:

\( \hat{p} = f_\text{LightGBM}(X_\text{ml}) \in \mathbb{R}^C \tag{12}\)
