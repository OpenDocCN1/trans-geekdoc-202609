
Our method is evaluated on two public video anomaly detection datasets, namely, ShanghaiTech Campus [[17](#chap6.xhtml#fsr17)] and CUHK Avenue [[16](#chap6.xhtml#fsr16)]. We compare our proposed Normal Graph with MPED-RNN [[24](#chap6.xhtml#fsr24)] which leverages RNN to predict future joints and reconstruct current joints. All experiments are evaluated on the metric of frame-level AUC.

### 4.1 Dataset

The **ShanghaiTech Campus dataset** [[17](#chap6.xhtml#fsr17)] is a new large-scale anomaly detection dataset, recorded on several spots in campus. The anomalies defined in this dataset can be caused by humans and vehicles. The previous work [[24](#chap6.xhtml#fsr24)] splits a subset from ShanghaiTech Campus that contains only those human-related anomalies, named HR-ShanghaiTech, which will be used in this chapter. We also evaluate our method on this subset.

The **CUHK Avenue dataset** [[16](#chap6.xhtml#fsr16)] is also a popular anomaly detection dataset, recorded at a single view of the metro. We also extract those human-related anomalies and name it HR-Avenue.

### 4.2 Implementation details

We utilized Alpha-Pose [[19](#chap6.xhtml#fsr19)] to extract skeletons for each frame in a video. We follow the tracking algorithm used in Ref. [[24](#chap6.xhtml#fsr24)], which combines sparse optical flow with skeletons. For the configuration of ST-GCN, we follow the setting in Ref. [[8](#chap6.xhtml#fsr8)] which is composed of 9 ST-GCN layers. The first three layers, the following three layers and the last three layers have 64, 128 and 256 channels, respectively. The Resnet mechanism is applied on each ST-GCN.

### 4.3 Comparison with state-of-the-art methods

In this section, we compare Normal Graph with appearance-based [[1](#chap6.xhtml#fsr1), [2](#chap6.xhtml#fsr2), [17](#chap6.xhtml#fsr17), [32](#chap6.xhtml#fsr32)] as well as skeleton-based methods [[24](#chap6.xhtml#fsr24)]. The results illustrated in [Table 1](#chap6.xhtml#tab1) demonstrate that skeleton-based methods achieve better AUC than those with appearance-based ones, especially on the HR-ShanghaiTech dataset where anomalies are associated only with humans. We believe appearance-based methods will introduce noise from background during reconstruction [[1](#chap6.xhtml#fsr1), [17](#chap6.xhtml#fsr17)] or prediction [[2](#chap6.xhtml#fsr2)]. In addition, our method performs better than MPED-RNN which models the relationship of skeletons with RNN, while our method utilizes spatial temporal graph convolutional networks to model the relationship in a graph. In conclusion, our proposed method achieves the state-of-the-art AUC and EER on the ShanghaiTech (ST), the HR–ShanghaiTech (HR–ST) and the CUHK Avenue, which demonstrates the effectiveness of our method.

**Table 1:** The performance of different baselines on ShanghaiTech (ST), Human-Related ShanghaiTech (HR-ST) and CUHK HR-Avenue.

![figure](images/p148-1.jpg)

### 4.4 The number of ST-GCNs

We further conduct an ablation study on the number of ST-GCNs to explore the mechanism of ST-GCNs. The output channels of 9 ST-GCN are set to 64, 64, 64, 64, 128, 128, 128, 256, 256, respectively. The number of ST-GCNs is gradually increased and a fully connected layer is always utilized for prediction. Demonstrated in [Fig. 3](#chap6.xhtml#fig3), the performance on the CUHK Avenue dataset gradually increases when the number of ST-GCNs increases. Especially, it arrives at the best performance on the CUHK Avenue dataset when the number of ST-GCNs is 9. We assume that deeper ST-GCN models will cause difficulty in optimization, where some works [[33](#chap6.xhtml#fsr33)] propose a residual mechanism to increase the layers of GCN, which is out of scope in this work.

### 4.5 The effectiveness of ST-GCNs

To further investigate the effectiveness of our proposed method, we introduce a baseline which contains only 9 fully connected layers and another baseline which includes only spatial GCNs. For fair comparison, the dimensions of the 9 fully connected layers are the same with the 9 ST-GCN-based Normal Graph. Illustrated in [Table 2](#chap6.xhtml#tab2), stacking only several fully connected layers results in a dramatical performance decline. It proves that fully connected layers cannot explicitly characterize the spatial and temporal relationship of human joints, while GCNs are able to model such a complex relationship with a specific adjacent matrix. Further, the GCNs with only spatial connection and without temporal connection cannot well characterize the relationship across time, resulting in a slight performance decline.

![figure](images/p149-1.jpg)

**Figure 3:**The performance of Normal Graph on the CUHK Avenue dataset when changing the number of ST-GCNs.

**Table 2:** The demonstration of the effectiveness of our proposed normal graph.

|  || **CUHK Avenue** |
| --- | --- |
| 9 Fully connected layers || 0.802 |
| --- | --- |
| Normal Graph without temporal connection || 0.857 |
| Normal Graph || 0.873 |

![figure](images/p150-1.jpg)

**Figure 4:**The visualization on the HR–ST dataset.

### 4.6 The demo of normal graph

To further analyze our method, we visualize scores normalized from the scores in a video clip on the HR–ST dataset. As demonstrated in [Fig. 4](#chap6.xhtml#fig4), our proposed Normal Graph can well detect HR anomalies. Besides, we found that failure cases always happen in some subtle actions and occlusion scenes which cannot be well captured by joints.

### 4.7 The visualization of anomaly detection

We also visualize some successful detected results in both HR–ST dataset and HR-Avenue dataset, as shown in [Figs. 5](#chap6.xhtml#fig5) and [6](#chap6.xhtml#fig6), respectively. The visualizations show that the pedestrian acting abnormally cannot be well predicted in terms of joint positions, while the normal cases are predicted well.

![figure](images/p151-1.jpg)

**Figure 5:**The detection results on the HR–ST dataset. The red boxes denote the abnormal regions. Best viewed in color.

![figure](images/p152-1.jpg)

**Figure 6:**The detection results on the HR Avenue dataset. The red boxes denote the abnormal regions. Best viewed in color.

### 4.8 The analysis of true positive rate and false negative rate

Besides the measurement on AUC, we also provide the analysis of true positive rate (TPR) and false positive rate (FPR) when a certain threshold (0.5) is set to determine whether a frame is normal or abnormal. We conduct such experiments on HR–ST dataset and find that TPR is 0.76 and the FPR is 0.37.

We also find that humans who are on bikes are easily missed by our proposed skeleton-based method since they appear quite similar to those walking pedestrians. Thus, one can handle such an issue by combining the image-based solution and the skeleton-based solution. We leave it for the future.

## 5. Conclusion

The image-level reconstruction or prediction-based methods for video anomaly detection may introduce noise from background. To minimize the affect from background, we tackle this problem by a skeleton-based prediction network which combines several spatial temporal graph convolutional networks and a prediction module. With the model trained on only normal data in the training set, abnormal events represented by skeletons will be automatically discovered. To our knowledge, this is the first work to apply graph convolutional networks on skeleton-based video anomaly detection. Experiments show that our proposed normal graph achieves state-of-the-art performance, compared with those image-level reconstruction-based methods, image-level prediction-based methods, and skeleton-level RNN-based methods.

## References

[1](#chap6.xhtml#fs1).M. Hasan, J. Choi, *et al*., “Learning temporal regularity in video sequences,” in *CVPR*, 2016.
