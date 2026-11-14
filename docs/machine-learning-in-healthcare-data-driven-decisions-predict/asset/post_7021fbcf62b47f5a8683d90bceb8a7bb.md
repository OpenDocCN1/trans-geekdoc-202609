

![](img/106ef0dba620d314f9842503e8ef40c8_406_0.png)

**Figure 4:** Proposed Algorithm 3.

\( L_{focal} = - \sum_{i=1}^N w_{y_i} (1 - p_{y_i})^\gamma \log(p_{y_i}) \) (23)

- Step 7: Combine with regularization term:
  \( L_{final} = \lambda || \Theta ||_2^2 \) (24)

- Step 8: Final loss function:
  \( L_{final} = \lambda_1 L_{CE} + \lambda_2 L_{focal} + \lambda_3 L_{reg} \) (25)

- Step 9: Backpropagation using gradient descent:
  \( \Theta \leftarrow \Theta - \eta \nabla_\Theta L_{final} \) (26)

- Step 10: Continue until convergence criteria:
  \( |L_{final}^t - L_{final}^{t-1}| < \delta \) (27)

**Table 4: Algorithm description.**

| Algorithm | Purpose | Key techniques |
|---|---|---|
| DB-MSFE | Multi-scale feature extraction | Dual-branch CNN, dilated convolutions, normalization |
| HCFB | Hierarchical feature fusion | Attention (channel and spatial), self-attention, cross-level aggregation |
| CA-FRLO | Imbalance-aware optimization | Class-aware reweighting, focal loss, L2 regularization |

Three sophisticated algorithms as shown in Table 4, dual-branch multi-scale convolutional feature extraction (DB-MSFE), hierarchical cross-fusion block (HCFB), and class-aware feature reweighting and loss optimization (CA-FRLO) are employed in the modular structure of the proposed feature extraction approach for cervical cytology image analysis. The initial module, referred to as DB-MSFE, employs a dual-branch CNN to extract rich contextual and morphological information from cytology images. While the other branch utilizes dilated convolutions in order to retain more general contextual information, the initial branch utilizes regular convolutions in order to extract local features.

In order to pursue a robust multi-scale representation, these branches also leverage spatial dropout, depthwise separable convolutions, and 1 × 1 convolutions to adjust dimensions. The second module, HCFB, takes in the generated feature maps and applies a hierarchical cross-fusion method to enhance the discriminability of the features. HCFB employs channel and spatial attention mechanisms, representing spatial dependencies via self-attention and channel descriptors via GAP. Adaptive weighting and residual connections are used to combine these attention-refined features at different encoder levels, producing semantically rich representations that are sensitive to high-resolution cellular differences and inter-class similarities.

Finally, through the computation of dynamic class-aware weights using label frequency and their inclusion in a composite loss function, the CA-FRLO module addresses the problem of class imbalance, an important one when dealing with cervical cancer datasets. Class-weighted cross-entropy, L2 regularization to prevent overfitting, and concentrated loss for hard sample mining are all integrated within this function. These three modules cooperate to provide the proposed HCFEN framework with improved feature representation, enhanced sensitivity to minority classes, and enhanced generalization, all of which assist in the detection of cervical cancer that is more accurate and interpretable.

## 4 Experimental Results

With a robust and reproducible experimental platform, the proposed HCFEN was implemented and evaluated over benchmark cervical cytology dataset Herlev. Python 3.8 was utilized for the whole implementation, and PyTorch framework version 1.12 was utilized to perform deep learning operations. To ensure computational efficiency, CUDA-supported GPUs (NVIDIA RTX 3090 with 24 GB VRAM) were utilized for both training and inference phases. In order to enhance generalizability and solidity, the image preprocessing pipeline resized all cytology images to 224 × 224 pixels, zero-mean unit variance normalized them, and applied data augmentation methods such as flipping, random rotation, and contrast adjustment.

A batch size of 32 was utilized, and the model was trained on the Adam optimizer with an initial learning rate of 1e-4. The learning rate would be dropping by a factor of 0.1 every 10 epochs according to validation performance. We employed shared measures including accuracy, sensitivity (recall), specificity, precision, and F1-score to exhaustively evaluate HCFEN's performance on classification. In medical image classification, where diagnostic risk associated with false negatives and class imbalance need to be precisely controlled, these metrics are particularly important. To provide further insight into class-wise performance and discriminative power of the model over thresholds, confusion matrices and receiver operating characteristic (ROC) curves were generated.

To ensure statistical stability and prevent overfitting on the limited training samples of cytological data sets, a 5-fold cross-validation method was employed. We compared HCFEN's performance with a set of state-of-the-art models, including ResNet50, DenseNet121, InceptionV3, EfficientNet-B0, and a novel attention-based hybrid CNN transformer model. To ensure fairness, the baseline models were all pre-trained on ImageNet and fine-tuned on respective cytology datasets using the identical training setup and loss functions by HCFEN. With 98.7% accuracy, 98.2% sensitivity, 99.0% specificity, and F1-score of 98.5% on the Herlev dataset, HCFEN surpassed all baseline models by a significant margin. EfficientNet-B0 achieved an overall accuracy of 95.1%, while ResNet50 and DenseNet121 achieved F1-scores of 95.4% and 96.2%, respectively. Figure 5 shows the ROC comparison, Figure 6 depicts training and testing validation comparison, and Figure 7 depicts the performance metrics analysis. Furthermore, minority class detection, especially for abnormal epithelial types, showed a marked improvement due to the class-aware loss mechanism integrated into HCFEN, which addressed class imbalance by dynamically adjusting penalty weights during backpropagation.

Comprehensive training performance and feature extraction iteration judgments were conducted in an effort to evaluate the learning behavior and architectural efficiency of the proposed HCFEN model. The improvement of the model progressively along with epochs of training is evident in the training performance iteration table. As shown in Table 5, the model achieves 96.8% accuracy after 20 epochs and continues to improve, reaching a peak of 98.7% accuracy and 98.5% F1-score at epoch 100. This demonstrates effective optimization, smooth convergence, and good generalization without overfitting of the model. Furthermore, ablation-based contribution for each architectural module is shown in Table 6. At 91.3% accuracy, performance is initially limited when beginning with a baseline CNN.

By contrast, the hierarchical fusion blocks enhance multi-scale feature representation, and introducing a dual-branch CNN enhances contextual understanding. The highest results of 98.7% accuracy and 98.5% F1-score are achieved when cross-attention mechanisms are eventually added to the entire HCFEN setting, proving the effectiveness of hierarchical cross-fusion. All these results prove that the progressive architectural enhancement significantly enhances the proposed system's robustness and discriminative ability.

## 5 Conclusion

To alleviate common problems in automated cervical cytology classification, including poor feature representation, limited interpretability, and class-imbalance impact, this study presents the HCFEN, an advanced deep learning network. A dual-branch CNN backbone, cross-attention blocks, and hierarchical fusion blocks are all incorporated into HCFEN to effectively gather contextual and fine-grained morphological information that are crucial for accurate cell classification. The ability of the model to identify minority classes is also enhanced by the inclusion of a class-aware loss function,

![](img/106ef0dba620d314f9842503e8ef40c8_410_0.png)

![](img/106ef0dba620d314f9842503e8ef40c8_410_1.png)

**Figure 6:** Training versus validation.

