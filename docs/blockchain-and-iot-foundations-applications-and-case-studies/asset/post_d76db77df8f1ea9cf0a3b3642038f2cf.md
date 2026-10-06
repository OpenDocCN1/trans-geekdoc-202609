
# Blockchain and AI in eHealth

131

![](img/7237166d8c6f79ea99cc6e305e5ec1f5_143_0.png)

FIGURE 8.2 Architecture diagram.

![](img/7237166d8c6f79ea99cc6e305e5ec1f5_143_1.png)

FIGURE 8.3 Flowchart representation.

# Blockchain and IoT

![](img/7237166d8c6f79ea99cc6e305e5ec1f5_144_0.png)

FIGURE 8.4A Blockchain in healthcare.

![](img/7237166d8c6f79ea99cc6e305e5ec1f5_144_1.png)

FIGURE 8.4B Machine learning framework.

the supervised learning approach is used to classify and predict the dataset as it emphasizes the patterns from the data. For distinguishing the feature, the output is predicted. It can validate the dataset using the cross-validation technique. The machine learning framework is depicted with details in Figure 8.4b.

# SUPPORT VECTOR MACHINE

Support vector machine (SVM) is one of the types of supervised machine learning that is used to decide the boundary of multiple classes by performing various analyses of input within the dataset. It points at the position of the greatest possible distance between two data points in each class. It uses binary linear categorization as its main objective. It helps to highlight the model of a higher dimension. In the nonlinear model, it uses a kernel technique to map or plot within the high-dimensional space. The decision boundary between two different classes is using SVM. SVM supports every data point in the course of mapping the data. SVM can predict the distance between two data points the scaling ranges from 0 to 1. For classification purposes, K-SVM is performed.

# Random Forest Classifier

Random forest is one of the significant methods used to integrate multiple models. The extensive ranges of datasets are classified with compatibility by using a random forest algorithm. Bootstrap aggregation and bagging models integrate multiple models of data. Model variants are reduced by using the bagging technique to prevent overfitting. Decision entries are used to specify the data by attaining various outcomes in the decision tree. It was classified in the majority value by attaining the average value. In terms of prediction, a combined decision approach is better in performance than a single decision approach. Random samples are taken from the training dataset. It chooses the attributes from each training dataset and selects the data point from the tree. Features are selected according to their ranking scores.

- Step 1: Select a random set of K features from the total set of m features such as K<m.
- Step 2: From the K features calculate the node p by using the split point in the dataset.
- Step 3: By using the split node, split the node p into daughter nodes.
- Step 4: Repeat the process until the number of nodes is reached.
- Step 5: Build a forest by using the number of ways (n) to create trees by repeating the process.

# KNN Classifier

The KNN classifier is a popular machine learning approach used for classification and regression tasks. In this model, the unlabeled data points and the existing set of training dataset distances are determined in the featured set of stored space. It is highly compatible for predicting classes. The nearest set of data points are validated according to the K value of new observations. This KNN classifier can allocate the predicted classes to class label value. The optimized set of KNN generates a neighbor with a positive relationship to the requester. It can evaluate the weight of the adjacent neighbor. The weight of the adjacent neighbor is determined by using the KNN algorithm by measuring the distance function. Different types of continuous function variables are used to weight the adjacent neighbor. By using the KNN classifier algorithm, the distance functions of the test and training data can be validated. The algorithmic steps to followed by:

- Step 1: Load the dataset of values.
- Step 2: After loading the data, initialize the set of values of k.
- Step 3: For prediction uses, the iterate set of values from 0 to the total range of the training set of data points.
- Step 4: Euclidean distance d(x,y) is used to measure the data metrics by calculating the distance between the training data and the test data.
- Step 5: After calculating the data, sort the data in ascending order.
- Step 6: Gather the k set of rows from the sorted type of array.
- Step 7: Gather the frequent class from each row.
- Step 8: After the prediction, the process is returned to the original state.

# BLOCKCHAIN IN HEALTHCARE

The distributed and safe method to collect and gather transactions is provided by blockchain technology. A blockchain stores information and offers advantages privacy, interoperability, and audits of an immutable nature. It uses a digital ledger of transactions that the networks throughout the computer system to duplicate the complete network. It creates a chain of immutable blocks using a decentralized, digital ledger of transactions. The public key and private key are used in the blockchain technology to verify validity. The storing of a child's health information is controlled by blockchains. By using digital transactions, the application notifies the health records. The decentralized system is used to eliminate the point of failure or delay in order to eliminate traffic flows. It can guarantee the information's scalability and robustness. The signature is used to identify the user's identification and to verify the data. The blockchain can [missing text] 8.4a.

# COMPARATIVE ANALYSIS

The distributed and safe method to collect and gather transactions is provided by blockchain technology. A blockchain stores information and offers advantages privacy, interoperability, and audits of an immutable nature. It uses a digital ledger of transactions that the networks throughout the computer system to duplicate the complete network. It creates a chain of immutable blocks using a decentralized, digital ledger of transactions. The public key and private key are used in the blockchain technology to verify validity. The storing of a child's health information is controlled by blockchains. By using digital transactions, the application notifies the health records. The decentralized system is used to eliminate the point of failure or delay in order to eliminate traffic flows. It can guarantee the information's scalability and robustness. The signature is used to identify the user's identification and to verify the data. The blockchain can [missing text] 8.4a.

The distributed and safe method to collect and gather transactions is provided by blockchain technology... [repetition corrected based on OCR flow]

The results of a comparison on the basis of accuracy and computational burden are the... calculated as follows:
Sensitivity = $\frac{TP}{TP+FN}$
Specificity = $\frac{TN}{TN+FP}$
Precision = $\frac{TP}{TP+FP}$
Recall = $\frac{TP}{TP+FN}$
Accuracy = $\frac{TP+TN}{Total}$

# Blockchain and AI in eHealth

### TABLE 8.2 Attributes from Data

| Attribute | Infant (0–3 years) | Child (6–10 years) | Number of Features | Training Samples | Testing Samples |
|---|---|---|---|---|---|
| Heart rate | 140 bpm | 110 bpm | 7 | 44 | 166 |
| Systolic blood pressure | 98 mm/mmHg | 100 mm/mmHg | 8 | 67 | 46 |
| Diastolic blood pressure | 65 | 70 | 9 | 24 | 67 |
| Pulse rate | 105 beats | 108 beats | 15 | 35 | 77 |
| Temperature sensor | 98.1°F | 99.1°F | 17 | 36 | 98 |
| pH level | 6.55 | 7.01 | 19 | 78 | 78 |
| Lactic acid | 1.7 mmol/L | 17 mmol/L | 21 | 43 | 54 |
| Hemoglobin | 10 g/dL | 13 g/dL | 34 | 68 | 49 |
| Respiration rate | 40 bpm | 20 bpm | 56 | 85 | 98 |

The dataset is from the Pima Indian research center. Nine attributes were taken from the children's vital parameters (Table 8.2). TP is the number of children who have an abnormality in their vital parameters, TN is the number of children who are healthy, FP is the number of children who have an abnormality in their vital condition, and FN is the number of children who are found to be normal.
