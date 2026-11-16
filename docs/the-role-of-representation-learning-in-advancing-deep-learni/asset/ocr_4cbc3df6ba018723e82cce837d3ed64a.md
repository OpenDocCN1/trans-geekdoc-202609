where:

+   - $I \in \mathbb{R}^{H \times W \times C}$ is the input image tensor, with $H, W,$ and $C$ representing its height, width, and number of channels, respectively.
+   - $\mathcal{Y}$ is the output space, consisting of sets of detected objects (bounding boxes and class labels).
+   - $n_O$ is the number of detected objects in image $I$.
+   - $n_C$ is the number of object classes.
+   - $\mathbf{b}_i = (b_{ix}, b_{iy}, b_{ih}, b_{iw}) \in [0, 1]^4$ represents the normalized bounding box coordinates for the $i$-th object: the center $(b_{ix}, b_{iy})$, height $b_{ih}$, and width $b_{iw}$, following [35].
+   - $c_i \in \{1; ..., n_C\}$ is the class label for the $i$-th object.

# D.1.2 Architecture

The model consists of the following main components:

**Backbone.** The backbone processes the input image and generates embeddings that serve as leaf nodes of the tree. These embeddings can be thought of as latent vector representations of image patches. Following DETR [35], we use a ResNet50 backbone pre-trained on ImageNet.

**Tree Encoder.** The encoder takes the leaf node embeddings as input and constructs the remaining levels of the tree in a bottom-up fashion.

**Tree Decoder.** The decoder parses the tree, selecting a subset of nodes relevant to the given task. It takes both the tree and a set of learned decoder embeddings as input. These decoder embeddings are analogous to the object queries in DETR [35], each representing a potential object. The decoder refines these embeddings through cross-attention with the selected tree nodes.

**Output Head.** The output head uses the refined decoder embeddings to predict bounding box coordinates and class labels. Specifically, for each decoder embedding, the output head predicts a vector of dimension $n_C + 4$, where $n_C$ is the number of objects classes and 4 corresponds to the normalized bounding box coordinates.