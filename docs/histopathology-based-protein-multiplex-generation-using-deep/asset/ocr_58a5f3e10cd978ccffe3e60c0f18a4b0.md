false negatives. HYPE$_{fake}$ and HYPE$_{real}$ are the error rates for generated and real images, respectively.

# HistoPlexer for cell-level analysis

**Pseudo-cells.** Because spatial analyses of IMC data typically rely on cell-level readouts, we created pseudo-single-cell data by extracting circular regions of 10 $\mu$m diameter around nuclei coordinates for both input H&E and GT IMC images. Protein expression was averaged across pixels within each pseudo-cell for individual markers. Nuclei coordinates for H&E images were obtained using the HoVer-Net model$^{28}$, and nuclei coordinates and cell-type labels for GT IMC multiplexes are derived using Ilastik$^{59}$ and CellProfiler$^{46}$, as described in ref. 8. For simplicity, we refer to pseudo-cells as ‘cells’ in the following text.

**Cell typing.** We used a random forest classifier$^{30}$ to categorize cells based on the average expression of 11 markers from the HistoPlexer. The classifier distinguished between tumour cells, B cells, CD8$^+$ T cells, CD4$^+$ T cells and other cells. Training was performed using the scikit-learn library$^{60}$, with hyperparameters (100 base estimators, maximum tree depth of 30) selected based on the lowest out-of-bag error. The model achieved a macro-averaged F1-score of 0.81 on an internal test set. We then applied the trained RF classifier to both GT and generated protein expression data to produce cell-type maps for cells in the test set.

**t-SNE on cell-level marker expression.** To explore spatial patterns beyond pairwise protein interactions, we conducted a low-dimensional embedding analysis of cell-level marker expression. Following the approach commonly used for mass cytometry data$^{61}$, we subsampled 1,000 cells per ROI from both GT and generated IMCs, resulting in total 2,000 cells per ROI. A joint t-SNE dimensionality reduction (two dimensions, perplexity of 50 and 1,000 iterations) was then applied. For visualization, protein abundance was scaled and clipped at the 99th percentile, and the t-SNE plots were coloured according to the scaled protein expression$^{61}$.

# Annotations for immune phenotyping

To stratify samples into immune subtypes based on the spatial distribution of CD8$^+$ T cells, we used annotated regions as established in ref. 5. Our dataset included 109 metastatic melanoma H&E WSIs from the TuPro cohort, with metastatic sites in lymph nodes, soft tissue, brain and other distant locations. The primary region for immune-subtyping, termed the ‘tumour centre’, comprised entirely tumour tissue, which was manually defined as a continuous tumour mass excluding a 500 $\mu$m margin from the tumour–non-tumour boundary. This ‘tumour centre’ was further segmented into two regions: the ‘intratumoral tumour’ region, consisting of dense clusters of malignant melanocytes without outstromal presence, and the ‘intratumoral stromal’ region, which includes extracellular matrix (typically desmoplastic) interwoven within the tumour cell mass but free from malignant melanocytes. These regions were automatically classified using a deep learning model implemented on the HALO$^{AI}$platform, trained with selected H&E WSI regions. Tissue classification was conducted at 0.30–$\mu$m-per-pixel resolution with a minimum object size threshold of 50 $\mu$m$^2$. Excluded regions—such as preexisting lymphatic tissue, large adipose and muscle regions, artifacts, necrosis, haemorrhage and background—were omitted from the analysis. Ultimately, we analysed 34 samples with the highest-quality tissue classifications from the HALO$^{AI}$ model predictions. Extended Data Fig. 4 shows an example H&E WSI with region annotation and classification.

# MIL-based clinical outcome prediction

**Attention-based MIL for survival and immune subtype prediction.** MIL is a weakly supervised learning method for set-based data structures. In MIL, an input $X$ is a bag (that is, permutation-invariant set) of

instances $X = \{x_1, ..., x_N\}$, where $N$ denotes the number of instances in the bag. Given a classification task with $K$ classes, the goal is to learn a function $\mathcal{F}$ from $M$ training pairs $\{(x^{(m)}, y^{(m)})\}_{m=1}^M$ that maps $X$ to a bag-level label $y \in K$ without knowing label $y_i \in K$ for each instance in the bag. In our context, the input is a WSI, and the instances denote the extracted patches. More specifically, we follow the embedding-based MIL approach$^{39}$ and extract a feature vector $\mathbf{h}_i = h(x_i) \in \mathbb{R}^d$ from each patch. Then, an attention-pooling operator aggregates the patch features $\mathbf{h}_{1:N}$ to a single WSI-level representation$^{39}$

$\mathbf{g} = g(\mathbf{h}_i) = \sum_{i=1}^N a_i \mathbf{h}_i,$

where

$a_i = \frac{\exp\{\mathbf{w}^\intercal(\tanh(\mathbf{V}\mathbf{h}_i) \odot \eta(\mathbf{U}\mathbf{h}_i))\}}{\sum_{j=1}^N \exp\{\mathbf{w}^\intercal(\tanh(\mathbf{V}\mathbf{h}_j) \odot \eta(\mathbf{U}\mathbf{h}_j))\}}$

is the gated attention$^{39}$. Here, $\mathbf{w} \in \mathbb{R}^L, V \in \mathbb{R}^{L \times D}, U \in \mathbb{R}^{L \times D}$ are learnable parameters with hidden dimension $L$. $\odot$ is element-wise multiplication, and $\eta(\cdot)$ denotes the sigmoid function. Finally, a classifier $f(\cdot)$ maps the WSI-level representation to a WSI-level label $\hat{y} \in K$.

The end-to-end prediction takes the following general form:

$\hat{y} = \mathcal{F}(X) = f(g(\{h(x_i) : x_i \in X\})). \quad (11)$

For survival prediction, we modelled the time-to-event distributions as an ordinal regression task with right censored data (that is, patient death is unobserved until last known follow-up). Following ref. 40, we defined discrete time intervals and modelled each interval using an independent neuron in the output layer. More specifically, we partitioned the continuous time scale into non-overlapping time intervals $[t_{j-1}, t_j)$. $j \in [1, ..., J]$ based on the quartiles of survival time values, denoted as $y_j$. The continuous time-to-event $t^{(m)}$ for each patient was then replaced by a discrete time label $y_j^{(m)}$, where

$y_j^{(m)} = y_j \quad \text{if } \tau^{(m)} \in [t_{j-1}, t_j) \text{ for } j \in \{0, ... J\}.$

The problem then simplified to classification, where each patient defined by a triplet $(\mathbf{g}^{(m)}, y^{(m)}, c^{(m)})$. Here, $\mathbf{g}$ is the averaged bag features; $c$ is the censoring status, where $c=0$ if the death of the patient is observed and $c=1$ otherwise; and $y$ is the discrete time GT label. We adopt the negative log-likelihood survival loss$^{42}$ for modal optimization, formulated as

$L_{surv} = \{(\mathbf{x}^{(m)}, y_j^{(m)}, c^{(m)})\}_{m=1}^M = \sum_{i=1}^M (-c^{(m)} \log (f_{surv}(y_j^{(m)} | \mathbf{g}^{(m)})) + (1-c^{(m)}) \log (f_{surv}(y_j^{(m)} - 1 | \mathbf{g}^{(m)})) + (1-c^{(m)}) \log (f_{hazard}(y_j^{(m)} | \mathbf{g}^{(m)}))), \quad (12)$

where $f_{hazard}(y|\mathbf{g}) = \text{Sigmoid}(\hat{y}_j)$ is the discrete hazard function and $f_{surv}(y|\mathbf{g}) = \Pi_{k=1}^j (1 - f_{hazard}(y_k|\mathbf{g}))$ is the discrete survival function.

Finally, the patient-level risk was defined as the negative sum of all logits$^{41}$, which enables the identification of distinct risk groups and the stratification of patients.

For immune subtype prediction, we adopted the cross-entropy loss defined as

$L_{ce} = - \sum_{m=1}^M \sum_{k=1}^K y_k^{(m)} \log (\hat{y}_k^{(m)}). \quad (13)$