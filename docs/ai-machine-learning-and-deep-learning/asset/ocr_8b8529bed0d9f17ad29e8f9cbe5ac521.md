| MODEL TYPE | ML MODEL | SYMBOL | DESCRIPTION | TYPE |
|---|---|---|---|---|
| ADM | DBSCAN, K-Means |  | Set of nodes in *i*-th Layer | Set |
|  |  |  | Set of all layers | Set |
|  |  |  | *k*-th cluster for the sensor pair for a patient with status, | Sets |
|  |  |  | Set of all cluster for the sensor pair for a patient with status, | Cluster |
|  |  |  | *l*-th line segment of the clusters for the sensor pair and patient’s status, | Set |
|  |  |  | Set of all line segments of the clusters for the sensor pair and patient’s status, | Tuple |
|  |  |  | Sets of all clusters | Sets |
|  |  |  | Set of all line segments | Sets |

# 18.2.2 Machine Learning (ML)–based Patient Status Classification Module (PSCM) in SHS

The CPSs use machine learning (ML) algorithms provided their control decisions are driven through organizational, personal, or societal influence, and SHS is one of its kind. The prevalence of healthcare sensor devices has accelerated the data collection process from various sources in the emerging healthcare sector. Analyzing these data using ML models can extricate complex patterns from the data distribution. The learned pattern can be utilized to classify the patients’ health conditions and discover abnormalities in real-time sensor measurements [12]. This section is concentrated on discussing the ML models for PSCM of SHS. The PSCM mostly uses supervised ML algorithms being trained on the enormous data sample collected from state-of-the-art test beds and data centers. Among them, NN is a mentionable one that can precisely separate the dissimilar data distribution using nonlinear boundaries in high-dimensional feature space and conversely group the same data distribution [13]. Moreover, existing research shows that the DT algorithm exhibits notable performance in the patient status classification [14]. Other popular ML algorithms include LR, SVM, etc., which also can classify data for multiclass settings like NN and DT. A short overview of these ML models is presented here. These ML models are formally modeled based on our ongoing work [15].

# 18.2.2.1 Decision Tree (DT)

The comprehensive, swift, straightforward, and versatile nature of the DT algorithm has made it a popular classification algorithm that draws out inference rules from a complex feature space [14]. The DT algorithm categorizes a sample through its tree-structured decision rules. The ultimate challenges of the decision tree algorithm are to determine the depth of the inference tree, select the best features at a particular level, and choose optimal splitting points for the selected features. In this work, we have adopted a CART (classification and regression trees)–based algorithm leveraging Gini index–based attribute selection metric. *Figure 18.2* shows the tree structure of the DT model with formal notations.