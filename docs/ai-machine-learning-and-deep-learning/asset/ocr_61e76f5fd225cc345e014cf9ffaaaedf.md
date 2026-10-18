# 18.4.1.3 One-class SVM (OCSVM)

The OCSVM model is a bit different from the state-of-the-art support vector machine (SVM) model for novel pattern detection [30]. The SVM is a supervised ML for drawing hyperplanes between different classes. But the SVM model is dependent on the labels for the training samples. For zero-day/novel attack detection, the OCSVM model can be leveraged, which separates the trained patterns from the origin using a decision boundary. The OCSVM model’s decision boundary can be modified by tuning two hyperparameters: gamma and nu.

# 18.4.1.4 Autoencoder (AE)

The AE model is mainly an NN model that intends to regenerate the features. Section 18.2.2 shows the modeling notations of NN models [31]. The primary difference between the regular NN model and AE model is that the AE model contains some strict constraints. For instance, the number of nodes in the encoded hidden layer of the AE model needs to be less than the number of features of the model. Although the AE model mainly gets used for data compression applications, recently, the model has been used for abnormality detection as well.

# 18.4.2 Ensemble-based ADMs in SHS

The efficacy of the DBSCAN and K-means algorithm as ADM in SHS has been analyzed in our ongoing work [7]. Moreover, we propose an unsupervised ensembling of the AE and OCSVM models, which has shown significant performance in the smart building domain. The proposed ensembled model can be used as SHS ADM as well. The workflow of the algorithm is explained as follows.

# 18.4.2.1 Data Collection and Preprocessing

The primary stage of ensembled-based ADM is to create/collect benign sensor measurements from trusted devices. The dataset stores the SHS sensor measurements and corresponding actuation. The duplicate entries are removed from the dataset as the first step of preprocessing. Then the features are normalized, followed by the dimensionality of the feature space being reduced by the principal component analysis technique. The preprocessing steps allow faster model training. The dimensionality reduction of features is performed only for OCSVM model training. However, for AE model training, all features (sensor measurements) are used. The benign dataset is split into 75% training and 25% testing samples. Additionally, a dataset comprised of attack samples (generated based on the attack model as discussed in section 18.3) is also prepared for assessing the model’s performance.

# 18.4.2.2 Model Training

The model training uses preprocessed data to train both AE and OCSVM models. The AE model is directly trained with on historical benign samples, while the PCA components of training samples are used to train . The models are trained separately, and after the training’s completion, the prediction models are then used to calculate benign and anomalous sample separation thresholds.