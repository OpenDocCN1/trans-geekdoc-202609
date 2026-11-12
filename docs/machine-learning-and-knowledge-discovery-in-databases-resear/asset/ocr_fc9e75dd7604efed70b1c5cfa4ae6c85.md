![](bbox=[0.135, 0.085, 0.895, 0.365])

Fig. 2. The framework: (a) GraphJCL constructs local graphs for individual regions and a global graph for all regions. (b) GraphJCL introduces tailored message-passing mechanisms to capture local and global graph node representations. (c) GraphJCL employs entropy-optimized graph node pruning and modality-aware attention mechanisms to derive effective region representations. (d) Geography-driven, entropy-optimized, and mutual information-based contrastive techniques jointly enhance local region representations to generate the final region representations.

+   - **Taxi Flow** ($\mathcal{TF}$): Taxi flow captures mobility patterns within a region. Each region $U_i$ is associated with a vector $TF_i = \{TF_{i1}, TF_{i2}, \dots, TF_{iT}\}$, where $TF_{ij}$ represents the taxi flow count in region $U_i$ during the $j$-th time period. The $T$ represents the total number of periods (e.g., hours in a month), depending on the dataset.

+   - **Remote Sensing Imagery** ($\mathcal{RS}$): Remote sensing imagery provides a macro-level view of land use and urban structure within a region. Each region $U_i$ is associated with a remote sensing image $RS_i$.

# **Definition 3 (Fine-Grained Modalities (FM)).** A modality is considered fine-grained if it captures spatial topology and local environmental structures within a region, meaning that its data points exhibit significant variability and cannot be effectively aggregated into a single vector representation.

**The fine-grained modalities** $\mathcal{FM}$ **used are as follows:**

+   - **Street View Imagery** ($\mathcal{SV}$): Street view imagery captures local visual characteristics of urban regions through numerous spatially distributed images. Each region $U_i$ contains a collection of street view images, denoted as $\{SV_{i1}, SV_{i2}, \dots, SV_{i|\mathcal{SV}_i|}\}$, where $SV_{ij}$ represents the street view image with index $j$ within region $U_i$.

+   - **Road Network** ($\mathcal{RN}$): The road network captures the topological structure of urban regions. Each region $U_i$ contains a collection of road network elements, denoted as $\{RN_{i1}, RN_{i2}, \dots, RN_{i|\mathcal{RN}_i|}\}$, where $RN_{ij}$ represents a road segment