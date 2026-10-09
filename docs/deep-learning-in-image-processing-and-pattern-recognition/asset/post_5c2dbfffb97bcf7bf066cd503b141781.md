
using $v_m \in \mathbb{R}^C (m = 1, \cdots M)$. We calculate the cosine similarity between each query $q_t^k$ and all items $v_m$ in the memory to obtain a two-dimensional correlation graph of size $M \times K$. By forming a global softmax function, the probability $w_t^k$ of $q_t^k$ matching the $v_m$ is obtained. Figure 3 shows the flowchart of the confidence-guided difference enhancement module.

$$ w_t^{k,m} = \mathrm{softmax} \left[ \frac{\exp((v_m)^T q_t^k)}{\sum_{m'=1}^{M} \exp \left( (v_{m'})^T q_t^k \right)} \right] \tag{7} $$

![](img/e4200cc4308edaf8913e513b0f96dbb6_337_0.png)

**Figure 3.** Illustration of a confidence-guided difference enhancement module. To read items in the normal memory, we compute matching probabilities $w_t^{k,m}$ in between the query $q_t^k$ and items $v_m$, and applied a weighted average of the items with the possibilities to obtain the feature. With the confidence of the query $q_t^k$, a fully connected layer is used to change the weight of items. Finally, we multiply items by their weight, and add the items together to obtain the reconstructed query.

We add a fully connected layer to $\hat{q}_t$ as a confidence branch of the network, measuring the confidence level of the network evaluation. When the network confidence level is low, we reverse the original weight $w_t^{k,m}$ in succession to obtain features that are more different from the original image. By guiding the decoder to direct the anomalous features in the direction in which they are least similar, the difference can be increased. The transformed feature map and query features are assembled into the decoder. The formula is as follows.

$$ \hat{q}_t^k = \begin{cases} \sum_{m'=1}^{M} w_t^{k,m'} v_{m'} & \text{if } FC(q_t^k) < \delta \\ \sum_{m'=1}^{M} \left( 1 - w_t^{k,m'} \right) v_{m'} & \text{if } FC(q_t^k) \geq \delta \end{cases} \tag{8} $$

To train a fully connected layer of confidence, we only feed normal items into the fully connected layer. We denote the similarity of normal feature $q_t^k$ to memory item $v_m$ using $w_t^{k,m}$. We define $y$ as the target probability distribution of the input normal features. The target probability distribution can give the network "hints". The confidence $c$ denotes the probability that a query belongs to the memory items. Through training, normal features attain higher confidence in fully connected networks. The formula is as follows:

$$ w_t^{k',m} = (1-c) \cdot w_t^{k,m} + c \cdot y_t^{k,m} \tag{9} $$

We calculate the task loss using the prediction of negative log likelihood. To prevent the network from always choosing to receive the entire ground truth for minimizing the loss function, we add a binary cross-entropy loss function and balance the two losses using a hyperparameter $\lambda$; the loss function is as follows:

$$ \mathcal{L}_{c}=\lambda\left(\sum_{m=1}^{M} y_{i}^{k,m}\log\frac{1}{w_{i}^{v,m}}\right)+(1-\lambda)\log\frac{1}{c} \tag{10} $$

### 3.2.2. Comparison of Shallow Features

In the process of calculating the characteristic value of commodity damage, not all abnormal feature values have an equal impact on the judgment results. If only the single feature value of each pixel is compared in the process of comparing the image, the calculation result will produce a large error, which is not conducive to the overall understanding of the damaged area. This is because the production of abnormal features of commodities and the destruction of commodity packaging have a strong causal relationship. Therefore, we synthesized the changes in hand nodes in the $n$ frames before and after the selected video frame, and performed pixel-level feature vector stitching. We let the horizontal and ordinate changes of the nodes of the two adjacent frames be expressed as $\mathbf{k}_{xm}^{p}$, $\mathbf{k}_{yn}^{p}$, specifying that the left and down movements are negative values, where $p$ represents the hand, and $m$ is the $m$-frame in $n$ frames.

$$ \hat{\theta}=\arctan\left(\sum_{m=2}^{n}\mathbf{K}_{xm}^{p},\sum_{m=2}^{n}\mathbf{k}_{yn}^{p}\right) \tag{11} $$

We stitched the pixels in position according to the size of the frame of the selected video frame $\mathrm{w}\times\mathrm{h}$, where $\boldsymbol{f}_{M}^{i}$ is the feature vector of the RGB channel at the $i^{\mathrm{th}}$ pixel position of the last layer output of the segmentation model M. By stitching the feature values in the $\hat{\theta}$ direction, we filled the rest of the video frame $\hat{\theta}$ with black according to $\mathrm{w}\times\mathrm{h}$, and the feature vector of the stitching $\boldsymbol{f}_{\hat{\theta}}^{i}$, where $\lfloor\cdot\rfloor$ represents the splicing of pixels. When the sum value of the motion coordinates is small, we skipped the area aggregation module and directly compared the pixel-level features of each point.

$$ f_{\hat{\theta}}^{i}=\left[f_{\hat{\theta}}^{i,1}, f_{\hat{\theta}}^{i,2}, \ldots, f_{\hat{\theta}}^{i,n+m}\right] \tag{12} $$

Subsequently, for regions with large outliers, we compared the cosine distance defined on the intermediate feature of each element in the region:

$$ S_{n}^{(i)}=F(x,r)=1-\left\langle\frac{f_{M}^{i}(x)}{\left\|f_{M}^{i}(x)\right\|_{2}},\frac{f_{M}^{i}(r)}{\left\|f_{M}^{i}(r)\right\|_{2}}\right\rangle \tag{13} $$

where $\langle\cdot,\cdot\rangle$ is the inner product of two vectors.

### 3.2.3. Comparison of Deep Features and Fusion

Although shallow features can make good use of pixel-level information, the expression of higher features is missing, and the global features of the broken area are not expressed. We expressed the semantic differences between the segmentation map and the composite map by calculating the perceived loss of each patch. Furthermore, by using the semantic differences between abnormal objects in the composite image, we can compare the deep features of each pixel.

The pixels of the original video frame are defined as $f_{M}^{(i)}(x)$, and the pixels of the composite video frame are defined as $f_{\hat{M}}^{(i)}(x)$, where $F^{(i)}$ represents the elements of layer $i$ in the $N$ layer of the VGG network, which are normalized between $[0, 1]$. The perceived difference expression is as follows:

$$ D(x,r) = \sum_{i=1}^{N} \frac{1}{M_{i}} \left\| E^{(i)}\left(f_{x}^{i}(x) - F^{(i)}\left(f_{r}^{i}(r)\right) \right\|_{1} \tag{14} $$

Subsequently, we synthesized the differences of the deep and shallow layers of the same position, and assigned different weights to the deep features and shallow feature differences of each node, wherein we define the weight parameter as $\lambda_{S}$, $\lambda_{D}$. Finally, depending on the presence or absence of abnormal areas in the commodity, a fine judgment of the damage to the commodity can be made. The final synthetic difference is $SD$, which can be determined using the following formula:

$$ SD = \lambda_{S} \cdot S_{H} + \lambda_{D} \cdot D \tag{15} $$

## 4. Experimental Results and Analysis

### 4.1. Experimental Platform and Dataset

The following platforms were used in this experiment: Windows 11; Graphics: NVIDIA GeForce GTX1650; Server: Nine days of ascension, Baidu PaddlePaddle. We used the Pytorch deep learning framework, PaddlePaddle 2.3 networking framework, and Python 3.8 to build the network model.

Because the commodity destruction video dataset is still blank in the public dataset of anomaly detection, the actual situation of the popular public dataset of anomaly detection and the abnormal behavior of consumption are quite different. To ensure the validity and accuracy of the experiment, it was conducted using homemade datasets. For each video, only a single customer consumes, excluding multiple people consuming at the same time. The consumer is in a bright environment. Additionally, all the customer's behavior is in the area that can be monitored by the camera, and there is no malicious occlusion and other problems in the customer's consumption behavior. Since the container door is transparent, the camera is placed above the inside of the container, and the shooting area is directly facing the retail container door. The inside of the smart retail container is equipped with light strips. This ensures that customers are also under a good light source when consuming at night. The video starts recording when the customer opens the door, and stops recording when the customer closes the door.

We divided consumer behavior into four behavioral categories (buying, not buying, drinking water, and tearing up packaging) and included three types of commodities (potato chips, biscuits, and drinks). The commodities used did not include those with transparent outer packaging. We also tested our algorithm on the MVtec AD dataset shown in Figure 4. Figure 5 shows the four behavioral data points, and Table 1 lists the details of our dataset. This is a dataset that mimics industrial production scenarios and is mainly used for unsupervised anomaly detection. The dataset contains five textures and ten objects from different domains.

**Table 1.** Details of video datasets used in our experiments.

| Actions | Train | Resolution | Commodity | Test |
| :--- | :--- | :--- | :--- | :--- |
| Destroy | 397 | 1280 × 720 | 4 | 44 |
| Purchase | 891 | 1280 × 720 | 7 | 98 |
| No purchase | 412 | 1280 × 720 | 7 | 45 |
| Drink | 372 | 1280 × 720 | 3 | 41 |
