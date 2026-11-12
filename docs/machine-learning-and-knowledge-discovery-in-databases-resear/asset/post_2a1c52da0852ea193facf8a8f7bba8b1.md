
## 2 Related Work

**Graph Representation for Multi-modal Data.** Graph embedding for multi-modal data aims to learn low-dimensional vector representations of graph nodes from diverse data sources. Recent advances in graph neural networks (GNNs) have significantly improved these representations. For instance, HetCAN [31] enhances heterogeneous graph representation by incorporating both type-aware and dimension-aware encoders. These GNN-based approaches have gained substantial attention for their effectiveness in multi-modal data representation learning [10,21]. Early methods employed taxi flow patterns to define graph edges [18,23], whereas more recent studies integrate spatial and socio-environmental attributes into heterogeneous graphs for comprehensive urban modeling [7,32,33]. Additionally, graph contrastive learning has shown great potential in urban representation tasks [29]. These approaches highlight the effectiveness of graph-based multi-modal learning for urban region modeling.

**Urban Region Representation Learning.** Urban region representation learning models can be categorized based on the number of modalities they utilize. Some approaches focus on single-modal data. For instance, [18] leverages taxi data to model urban region embeddings, capturing vehicle movement patterns to reflect the semantic characteristics of urban areas. Similarly, [6] primarily utilizes Points of Interest (POI) features for region representation learning, while [22] employs satellite imagery, leveraging large-scale models to enhance final region representations. Other studies adopt multi-modal data to construct richer and more comprehensive urban region representations [9,24,26,27,30]. For example, [27] introduces a multi-view joint learning framework that integrates taxi data, POI data, and check-in records, effectively capturing cross-modal correlations to model urban regions from multiple perspectives. From a methodological perspective, some studies employ attention mechanisms for modality fusion [8,15,20], while others utilize graph-based approaches for urban region representation learning [7,32]. Our framework utilizes five modalities in a graph-based structure with contrastive learning, effectively capturing effective urban region representations.

## 3 Preliminaries and Problem Statement

### Definition 1 (Urban Regions ($\mathcal{U}$))
An urban area is partitioned into $N$ non-overlapping regions, denoted as $\mathcal{U} = \{U_1, U_2, \dots, U_N\}$. Each $U_i$ has a geographical boundary.

### Definition 2 (Coarse-Grained Modalities ($\mathcal{CM}$))
A modality is considered coarse-grained if it captures region-level urban functional attributes, allowing its data within a region to be aggregated into a single vector representing overall urban functionality.

The coarse-grained modalities $\mathcal{CM}$ used are as follows:

- **Point-of-Interest (POI)** ($\mathcal{P}$): POI data reflects the commercial activity of a region. Each region $U_i$ is associated with a vector $P_i = \{P_{i1}, P_{i2}, \dots, P_{iK}\}$, where $P_{ij}$ denotes the count of POIs in category $j$ within region $U_i$. The $K$ represents the top $K$ POI categories with the highest occurrence frequency across all regions.

![](img/f56761e6196132d5b74909d98468408f_107_0.png)

Fig. 2. The framework: (a) GraphJCL constructs local graphs for individual regions and a global graph for all regions. (b) GraphJCL introduces tailored message-passing mechanisms to capture local and global graph node representations. (c) GraphJCL employs entropy-optimized graph node pruning and modality-aware attention mechanisms to derive effective region representations. (d) Geography-driven, entropy-optimized, and mutual information-based contrastive techniques jointly enhance local region representations to generate the final region representations.

- **Taxi Flow** ($\mathcal{TF}$): Taxi flow captures mobility patterns within a region. Each region $U_i$ is associated with a vector $TF_i = \{TF_{i1}, TF_{i2}, \dots, TF_{iT}\}$, where $TF_{ij}$ represents the taxi flow count in region $U_i$ during the $j$-th time period. The $T$ represents the total number of periods (e.g., hours in a month), depending on the dataset.

- **Remote Sensing Imagery** ($\mathcal{RS}$): Remote sensing imagery provides a macro-level view of land use and urban structure within a region. Each region $U_i$ is associated with a remote sensing image $RS_i$.

### Definition 3 (Fine-Grained Modalities ($\mathcal{FM}$))
A modality is considered fine-grained if it captures spatial topology and local environmental structures within a region, meaning that its data points exhibit significant variability and cannot be effectively aggregated into a single vector representation.

The fine-grained modalities $\mathcal{FM}$ used are as follows:

- **Street View Imagery** ($\mathcal{SV}$): Street view imagery captures local visual characteristics of urban regions through numerous spatially distributed images. Each region $U_i$ contains a collection of street view images, denoted as $\{SV_{i1}, SV_{i2}, \dots, SV_{i|\mathcal{SV}_i|}\}$, where $SV_{ij}$ represents the street view image with index $j$ within region $U_i$.

- **Road Network** ($\mathcal{RN}$): The road network captures the topological structure of urban regions. Each region $U_i$ contains a collection of road network elements, denoted as $\{RN_{i1}, RN_{i2}, \dots, RN_{i|\mathcal{RN}_i|}\}$, where $RN_{ij}$ represents a road segment or junction with index $j$ within region $U_i$. The category index $RNS_{ij}$ specifies the type of road element (e.g., trunk road or motorway).

### Definition 4 (Downstream Tasks ($Y$))
Downstream tasks refer to socio-economic and environmental indicators in urban contexts. For urban area $\mathcal{U}$ with N regions, the L task targets are represented as $Y \in \mathbb{R}^{N \times L}$. This paper focuses on three downstream tasks, check-in counts, crime incidents, and traffic crash counts, where L = 3.

### Definition 5 (Problem Statement: Urban Region Representation)
Given urban regions $\mathcal{U}$ along with their associated coarse-grained modalities CM and fine-grained modalities FM, the objective is to learn a low-dimensional representation $H_i \in \mathbb{R}^{d_{out}}$ for each region $U_i$. These embeddings $\mathcal{H} = \{H_1, H_2, ..., H_N\}$ are used to predict downstream tasks Y.

## 4 Methodology

In this section, we introduce GraphICL, a dual-perspective graph-based framework for urban region representation. Its key components are illustrated in Fig. 2.

### 4.1 Local-Global Graph Construction

In this subsection, to achieve joint region modeling of local and global aspects, we construct a local graph for each individual region and a global graph for all regions.

**Local Graph Construction.** For each region $U_i$, we construct a local heterogeneous graph $\mathcal{G}_i = (\mathcal{V}_i, \mathcal{E}_i)$ to capture its intrinsic features without influence from other regions. Specifically, the node set $\mathcal{V}_i$ consists of six types of nodes:

- **Region**: A node $U_i$ representing the geographic boundary of the region.

- **POI**: A node $P_i$ representing aggregated POI data.

- **Taxi Flow**: A node $TF_i$ representing aggregated taxi mobility patterns.

- **Remote Sensing**: A node $RS_i$ capturing macro-level land use and urban structure.

- **Street View Imagery**: A set of nodes $\{SV_{i1}, SV_{i2}, ..., SV_{i|\mathcal{SV}_i|}\}$ representing localized street-level visual environmental features.

- **Road Network**: A set of nodes $\{RN_{i1}, RN_{i2}, ..., RN_{i|\mathcal{RN}_i|}\}$ representing the topological structure of road segments and junctions.

The edge set $\mathcal{E}_i$ consists of five types of edges, defining relationships between the region node $U_i$ and other modality nodes:

- $\mathcal{U}_{has\_\mathcal{P}}$: An edge $(U_i, P_i)$ that connects the region node to the POI node.

- $\mathcal{U}_{has\_\mathcal{TF}}$: An edge $(U_i, TF_i)$ that connects the region node to the taxi node.

- $\mathcal{U}_{has\_\mathcal{RS}}$: An edge $(U_i, RS_i)$ that connects the region node to the remote sensing imagery node.

- $\mathcal{U}_{has\_\mathcal{SV}}$: A set of edges $(U_i, SV_{ij})$, where $j = 1, 2, ..., |\mathcal{SV}_i|$, that connect the region node to all street view images nodes.

- $\mathcal{U}_{has\_\mathcal{RN}}$: A set of edges $(U_i, RN_{ij})$, where $j = 1, 2, ..., |\mathcal{RN}_i|$, that connect the region node to all road network elements nodes.

Based on the local graph construction method above, N local graphs $\mathcal{G}_i$, where $i = 1, 2, ..., N$, can be constructed for urban regions $U_1, U_2, ..., U_N$, respectively.
