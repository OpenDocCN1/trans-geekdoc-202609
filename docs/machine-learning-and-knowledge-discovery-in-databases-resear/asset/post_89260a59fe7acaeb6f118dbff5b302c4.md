
![](img/f56761e6196132d5b74909d98468408f_472_0.png)

Fig. 4. A novel definition of edge. In figure (a), each element in the cube represents a pixel. The value of this central orange pixel in the edge map is determined by all 27 pixels within a larger cube. The left side of figure (b) shows the general edge extracted by conventional method, the outermost edge contains only 240 pixels over 10000 pixels, while the right side of figure (b) depicts the edge extracted by our method, which contains 719 pixels (more than 5%). (Color figure online)

where $p$ and $p'$ represent a pixel, \(x_i^L(\cdot)\) denotes the value of the pixel in the image, \(e_i^L(\cdot)\) denotes the value of the pixel in the edge, \(b_i\) signifies the general edge, and \(b_i(\cdot)\) indicates the value of the pixel, \(\mathcal{N}(\cdot)\) refers to the 26 neighbouring pixels of a given pixel. By considering more neighbouring pixels along the boundary, the newly defined edge can encompass more pixels along the boundary, improving the robustness of edge. The difference between general edge and edge extracted by our method is shown in Fig. 4(b).

### Edge Attention

Inspired by the success of attention mechanism, we propose to displace the standard residual connections between the first two layers of encoder and last two layers of decoder with an edge attention module that comprises two channel attention (CA) blocks, which consists of three layers: an average pooling layer, a linear layer with ReLU, and a linear layer with Sigmoid. The average pooling layer ensures that every pixel of a channel contributes to the weight of this channel, and then two linear layers are used to calculate the weights of channels, which are also viewed as attention scores. The calculation of channel attention block is formulated as:

```
\(\mathbf{Y} = \mathbf{X} \times \sigma(\text{Linear}_2(\text{ReLU}(\text{Linear}_1(\text{AvgPool}(\mathbf{X}))))),\)
```

where \(\mathbf{X}\) is the input of channel attention block, \(\mathbf{Y}\) is the output of channel attention block, \(\sigma(\cdot)\) represents the sigmoid function, \(\text{Linear}(\cdot)\) denotes a linear transformation, and \(\text{AvgPool}(\cdot)\) means average pooling.

### 3.3 Edge-Aware Loss Function

The edge extraction module can extract robust edge information. Subsequently, another core issue is how to leverage the edge information to promote the learning. To this end, we elaborately design an edge-aware loss function, which is a combination of supervised loss $\mathcal{L}_{sup}$ and unsupervised loss $\mathcal{L}_{unsup}:$

$\mathcal{L}_{overall} = \mathcal{L}_{sup} + \alpha \mathcal{L}_{unsup}, \quad (7)$

where $\alpha$ is a balancing factor that controls the weight of inherent consistency.

For labeled data, we use the combination of Dice loss [14] and cross entropy loss to supervise the model training, as done in many medical image segmentation researches [1,24,33]. Beyond that, we utilize edge information extracted from the labeled data as additional supervision. Thus, the loss function on labeled data is formulated as follows:

$\mathcal{L}_{sup}(\hat{y}_S^L, y^L, \hat{e}_S^L, e^L) = 0.5 \left( \mathcal{L}_{dice}(\hat{y}_S^L, y^L) + \mathcal{L}_{ce}(\hat{y}_S^L, y^L) \right) + \beta \mathcal{L}_{edge}, \quad (8)$

$\mathcal{L}_{edge} = \frac{\text{SUM} \left( \left( (\hat{e}_S^L - y^L) \cdot e^L \right)^2 \right)}{\sum_{p=1}^P e^L(p)}, \quad (9)$

where $\hat{y}_S^L$ is the predicted segmentation, $y^L$ is the ground-truth, $\hat{e}_S^L$ is the edge prediction, $e^L$ is the edge, $\mathcal{L}_{dice}(\hat{y}_S^L, y^L)$ denotes the Dice loss, $\mathcal{L}_{ce}(\hat{y}_S^L, y^L)$ represents the cross entropy loss, $\beta$ is a balancing factor, $\mathcal{L}_{edge}$ is edge loss, function $\text{SUM}(\cdot)$ is the sum of the pixel-level values in a feature map, $P$ represents the total number of pixels in the image, and $p$ signifies an individual pixel within that image, the calculation of $e^L(p)$ is shown in Eq. 5. From Fig. 3, we can see that the edge output is extracted from the penultimate decoder, which obtains edge information from the edge attention module. Therefore, the loss $\mathcal{L}_{edge}$ helps to update the parameters of edge attention module. Additionally, to avoid redundant computations, the loss $\mathcal{L}_{edge}$ only takes into account the edge regions that are crucial for medical image segmentation.

For unlabeled data, we calculate the consistency loss between student network and teacher network. Specifically, the consistency loss consists of segmentation consistency loss $\mathcal{L}_{con}$ and edge consistency loss $\mathcal{L}_{edge\_c}$. The loss function $\mathcal{L}_{unsup}$ on unlabeled data is formulated as:

$\mathcal{L}_{unsup}(\hat{y}_S^U, \hat{y}_T^U, \hat{e}_S^U, \hat{e}_T^U, e^L) = \mathcal{L}_{con}(\hat{y}_S^U, \hat{y}_T^U) + \gamma \mathcal{L}_{edge\_c}(\hat{e}_S^U, \hat{e}_T^U, e^L), \quad (10)$

$\mathcal{L}_{con}(\hat{y}_S^U, \hat{y}_T^U) = (\hat{y}_S^U - \hat{y}_T^U)^2, \quad (11)$

$\mathcal{L}_{edge\_c}(\hat{e}_S^U, \hat{e}_T^U, e^L) = \frac{\text{SUM} \left( \left( (\hat{e}_S^U - \hat{e}_T^U) \cdot e^L \right)^2 \right)}{\sum_{p=1}^P e^L(p)}, \quad (12)$

where $\gamma$ is also a balancing factor, $\hat{y}$ represents the segmentation prediction, the subscripts $S$ and $T$ denote student network and teacher network, respectively, and the superscript $U$ means unlabeled data. From Eq. 12, we can see that the edge $e^L$ extracted from the labeled data are utilized as masks for unlabeled data. By imposing edge consistency between student and teacher networks, the learning from unlabeled data can leverage the edge information from labeled data to achieve better segmentation. By utilizing the edge extracted from labeled data as masks, a synergistic learning framework between labeled and unlabeled data is created, where edge information from labeled data can promote learning from unlabeled data and unlabeled data can provide more details about edge regions to help robust edge extraction on labeled data.

## 4 Experiments

### 4.1 Datasets

Two public datasets are used in our experiments, including the LA dataset [30], which contains 100 3D MRI images, and the Pancreas-CT dataset [15], which comprises 82 CT scans. For fair comparison, we preprocess the two datasets following the previous works [1, 16]. We also compare the segmentation performance of our proposed EAMT method with that of several state-of-the-art methods for semi-supervised medical image segmentation.

### 4.2 Implementation and Experimental Setting

**Implementation Configurations.** Our proposed EAMT is implemented using PyTorch and trained on an NVIDIA 4070 GPU. We employ the 3D V-Net architecture as the backbone, which is a de facto choice for many medical image segmentation tasks. We utilize the SGD optimizer with a weight decay of 0.0001 and a momentum factor of 0.9. The initial learning rate is set to 0.01, and we adopt a polynomial decay strategy to adjust the learning rate at each iteration.

For the LA dataset, we set the maximum number of iterations to 15k. We set the batch size to 8, comprising 4 labeled and 4 unlabeled samples. For the Pancreas-CT dataset, we set the maximum iteration to 10k, and a batch size of 4, with 2 labeled and 2 unlabeled samples. The parameter \(\alpha\) in Eq. 7 is set following the work in [18]. The parameter \(\beta\) in Eq. 8 is set to 0.1 for Pancreas-CT and 0.5 for LA dataset, besides, every 1.5k iterations, we will multiply this parameter for the LA dataset by 0.5. And \(\gamma\) in Eq. 10 is set to 1.0 for both two datasets.

Following previous works in semi-supervised medical image segmentation [1, 5, 10, 33], our experiments were conducted with two typical semi-supervised settings, i.e. training with 10% labeled data and training with 20% labeled data. Four metrics were adopted to evaluate the segmentation performance: Dice similarity coefficient (Dice), Jaccard similarity coefficient (Jaccard), 95% Hausdorff Distance (95HD), and Average Surface Distance (ASD).
