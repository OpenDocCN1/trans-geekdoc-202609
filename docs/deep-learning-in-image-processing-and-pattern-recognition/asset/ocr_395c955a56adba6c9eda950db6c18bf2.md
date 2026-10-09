where $h$ and $w$ are the height and width of the input, and $f_{i}$ is the index representing the $i$-th element of the feature map from the SRBlock and the most relevant position of the feature map from the RecBlock. Then, the feature $T$ transferred from the feature map of the RecBlock is obtained using $f_{i}$ as the index and applying the index selection operation to $V$. Here, the Feature Transfer Attention map $T$ contains the structural features of the text image and is denoised.

![](bbox=[0.15, 0.25, 0.85, 0.47])

Figure 4. The architecture of the FST module. Feature maps extracted from the reconstruction branch are fused with the feature maps from the SR branch to utilize complementary characteristics, such as noise removal capability and text structure information.

Finally, Soft Attention is calculated to synthesize the features from $Q$ and Feature Transfer Attention map $T$. In order to transfer relevant features, a soft attention map $\mathrm{S}$ is calculated from $r_{i,j}$ to estimate the confidence of the transferred texture features for each position of $T$ as shown in Equation (3):

$$s_{i} = \max_{j} (r_{i,j}),\tag{3}$$

where $s_{i}$ is the $i$-th position of the Soft Attention map S. Then, the feature map concatenating $T$ and $Q$ and the Soft Attention map S are multiplied element by element and output as the final feature map $F_{out}$. The definition is shown in the following Equation (4):

$$F_{out} = Q \oplus Conv (Concat (Q, T)) \otimes S.\tag{4}$$

Here, $\otimes$ is the element-wise multiplication, and $\oplus$ is the element-wise summation.

# 3.3. Feature Enhancement Transformer (FET)

FET is a transformer designed to capture sequential information for arbitrary directions in text images tilted or curved using 2D positional encoding. BLSTM [16], which has been used to capture sequential information in our previous work [31] and TSRN [12], is effective for horizontal and vertical sequential information but is insufficient for text images of real scenes with various shapes and orientations. Therefore, inspired by the results of studies [15,27,28] on the text image using 2D attention and recent achievements of the transformer in computer vision [32–34], we attempt to use a transformer for a feature enhancement to capture sequential information in arbitrary orientations.

The attention mechanism in typical transformers used for natural language processing and time series data processing cannot recognize spatial location information or context because the input is processed in parallel in one dimension. Thus, positional encoding for 2D orientation considers spatial positional information to enable the transformer for text