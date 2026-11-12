ing. To this end, we elaborately design an edge-aware loss function, which is a combination of supervised loss $\mathcal{L}_{sup}$ and unsupervised loss $\mathcal{L}_{unsup}:$

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

where $\gamma$ is also a balancing factor, $\hat{y}$ represents the segmentation prediction, the subscripts $S$ and $T$ denote student network and teacher network, respectively, and the superscript $U$ means unlabeled data. From Eq. 12, we can see that the edge $e^L$ extracted from the labeled data are utilized as masks for unlabeled