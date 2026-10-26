
## 重大突破的3个特征

- 通常他们不是由已知技术制成的
- 通常他们可能是模糊不清的
- 通常他们需要跨学科协作

be highly demanding and it involves a tremendous task of synchronizing data from multiple sources to fit a certain paradigm, which is an even tougher task when applied on real-time systems.

Another significant challenge is data heterogeneity. Multimodal data sources frequently have different formats, structures, and domains of information, leading to complexities in harmonizing these diverse inputs. For instance, combining textual data with image data involves reconciling differences in how information is represented and processed, which can complicate feature extraction and fusion processes.

Data fusion complexity also plays a ranking role in integration processes with complexity of data fusion. Combination of features from different modalities is necessarily accompanied by lossless merging techniques to avoid inclusion of unnecessary information. Choices as to where to do fusion, at the feature level or at the decision level, affect the functionality of many anomaly detection systems, and have to be made with a view to considering the various advantages and disadvantages of all three options.

Handling missing and incomplete data is another crucial issue. Multimodal datasets often suffer from missing data across one modality. Developing robust methods for dealing with these gaps, such as imputation techniques that can handle partial data, are essential for maintaining the integrity and performance of anomaly detection systems.

Finally, computational complexity is a significant obstacle. Because multimodal data has more dimensionality and a larger volume of data, integrating it usually takes more processing power. Longer processing times and increased resource consumption result from this, making the creation of effective algorithms and systems necessary to meet these needs without sacrificing performance.

## 2.3 Types of multimodal data

Multimodal data, on the other hand, are data that are gathered from different sources. Different modalities offer different and related views of a certain phenomenon. The integration of these varieties of data makes it possible to capture a broader range of analyzing techniques, which in turn helps to improve the notion of sensing anomalies.

### 2.3.1 Image data

The second type of multimodal data is image data, which contains different formats like gray, color and hyper spectral images. When using image data within the context of anomaly detection, the high level of detail within an image is again important in determining deviances from normal behavior. Such data is frequently applied in such areas as diagnostic imaging, in which magnetic resonance images can provide infor-

![](img/18722240e44c225d7ff2f58a10eecb4a_233_0.png)

Figure 2: Data fusion techniques.

weighted voting, and ensemble techniques, which combine the outputs of several classifiers, are methods for decision-level fusion. With these methods, every model functions independently on its own sort of data, and the fusion process combines their predictions to provide a more comprehensive judgment. When modalities need specialized processing and are extremely diverse, decision-level fusion comes in handy.

### 2.4.3 Model-level fusion

Model-level fusion refers to the use of joint models that process multiple modalities simultaneously. This approach involves designing and training models that can directly handle and integrate data from various sources, allowing for simultaneous processing and interaction between modalities. Techniques include multi-input neural networks, where each input represents a different modality, and the network learns to exploit correlations between them and multimodal deep learning models that share parameters modalities. Model-level fusion can enhance the ability of the system to capture complex relationships and dependencies between different types of data, leading to improved anomaly detection performance.

### 2.4.4 Graph-based fusion methods

Graph-based fusion methods model the relationships between different modalities using graph structures. In these methods, nodes represent different data modalities, and edges represent the relationships between them. By using concepts like GCNs and multi-graphs, to name a few, such representations that can capture between-modality dependencies can be developed. This approach helps to structure information and enhance the detection of outliers due to the integration of context and interdependency of distinct types of information.

### 2.4.5 Hybrid fusion approaches

Hybrid fusion approaches combine multiple fusion techniques to leverage the strengths of each method. For example, a system first performs feature-level fusion to create a unified feature representation and then applies decision-level fusion to aggregate predictions from separate models trained on different modalities. This layered approach allows for flexible and adaptive integration of multimodal data, addressing various challenges such as data heterogeneity and varying data quality. Hybrid fusion strategies can offer a balanced solution, maximizing the benefits of each fusion technique while mitigating their individual limitations.

## 2.5 Evaluation metrics for multimodal integration

A suitable set of measurements that can be used for the purpose of evaluating multimodal integration in detection of anomalous events for vulnerable segments of the population is needed to provide a clear picture of the performance of different aspects of the integrated system. As demonstrated in later chapters, unlike unimodal locomotion monitoring systems where evaluation can be performed with single indexed values, multimodal systems require a global assessment to guarantee that the fusion of multiple data sources improves the anomaly detection procedure.

### 2.5.1 Accuracy and precision

Precision is, to date, considered a key measure for evaluating the performance of multimodal anomaly detection systems. It calculates the ratio between accurate classification between anomalies and non anomalies in relation to the total sample size. Accuracy of predictive value is especially important in cases where the focus is on the correctness of the anomaly's identification using the ratio of true anomalies to the total number of true and false anomalies. In the context of multimodal approach, accuracy and precision cannot be assessed at modality level but rather in terms of how combining the modalities is enhancing the detection performance.

### 2.5.2 Recall and F1-score

Sensitivity is a measure of the proportion of real abnormalities in the total of false negatives and true positives. It is this statistic that is used to determine the effectiveness of the system’s anomaly detection across all modalities. F1-score is one of the better measuring scores because the score considers both false positives and false negatives. It is computed as the arithmetic mean of the ratio of the number of correct values to the total number of actual values and the ratio of the number of correct values to the number of values retrieved. When assessing the efficiency of the anomaly detection in general for multimodal integration, it is imperative to consider both true positive results and false positives. This is done based on what is shown in the *F1-score*.

### 2.5.3 Receiving operating characteristic curve (ROC-AUC)

The ROC-AUC measure considers the specificity/sensitivity relationship at different thresholds and results in a single, combined performance measure for quite a number of thresholds. For multimodal systems, ROC-AUC can provide some information about how well the fused modalities work compared to each other and how far they enhance the detection of anomalies. The ROC-AUC of rigorous units increases, indicating improved accuracy toward discriminating anomalies from non anomalies and demonstrating the efficiency of the proposed data fusion approach.

### 2.5.4 Multimodal fusion metrics

Specific metrics for evaluating multimodal fusion include measures of how effectively different data modalities are integrated. Metrics such as the fusion performance index (FPI) and cross-validation score for fusion (CVSF) assess the impact of data integration on overall model performance. The FPI evaluates the improvement in detection accuracy achieved through multimodal integration, compared to unimodal approaches, while CVSF involves cross-validating the performance of fused models to ensure generalizability and robustness.

We also demonstrated the computational efficiency and scalability of the method based on simulations.

Comparing the performance and factorability of multimodal systems tended to be significantly related to the large datasets with many users. Performance and versatility
