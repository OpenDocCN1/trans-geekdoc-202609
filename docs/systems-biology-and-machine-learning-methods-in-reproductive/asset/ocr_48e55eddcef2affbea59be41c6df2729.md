# **6.3.3.3 Isomap**

+   - Isomap restores the intrinsic geometrical structure for high-dimensional data in lower-dimensional spaces via Multi-dimensional Scaling (MDS)
+   - Graphically, it represents data points as nodes and similarities as edges.
+   - Then, computes the shortest distance between them using specific algorithms or spectral techniques.

# **6.3.3.4 Auto-encoder**

+   - System that uses ANNs.
+   - Consists of an encoder network that maps input data to a lower-dimensional latent space and a network of decoders that reassembles the input data from the latent space representation.
+   - Reduces dimensionality and compresses data.

# ## 6.4 SEMI-SUPERVISED LEARNING

+   - Aims to enhance the accuracy of the learning algorithm by utilizing the extra information present in unlabeled data.
+   - Useful in situations where acquiring labeled data is costly or time-consuming.
+   - Encompasses many approaches that may be used to address data-driven challenges, including SVM, Self-training, Graph-based techniques, Co-training, and Generative models.

# **6.4.1 Self-training**

+   - Generates predictions on labeled data is first trained using the labeled data.
+   - Predicted labels that have a high level of confidence are then included in the labeled dataset.
+   - Undergoes retraining using the enhanced labeled dataset, and this process continues until convergence is achieved.

# **6.4.2 Co-training**

+   - Entails training several models or perspectives on distinct subsets of characteristics or depictions of the data.
+   - At first, every model is trained using the labeled data.
+   - Share reliably predicted labels on the unlabeled data with one another.
+   - The models undergo retraining using the supplemented labeled data, and this procedure is repeated frequently.