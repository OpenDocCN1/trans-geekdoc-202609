# Transforming Healthcare

# 10.3 PROPOSED WORK

# 10.3.1 Problem statement

One effective solution to alleviate the scarcity of spectrum resources is SS. Commonly used approaches often use model-based variables, including energies and Eigenvalues, as test statistics, omitting the temporal correlation component. Techniques based on deep learning may concentrate on a number of factors such as temporal correlation. Since traditional convolutional neural networks (CNNs) and long short-term memory networks (LSTMs) are employed for feature extraction, the current ones, however, are not very effective at extracting the correlation information from spectrum data. Time series data has global temporal correlations that traditional CNNs were not intended to detect. Standard LSTM is unable to highlight certain significant portions of a time series and only captures temporal correlations based on data gathered from earlier time slots The proposed deep neural network (DNN) model are self-attention (SA), bidirectional long-term memory network (BiLSTM), and 1-dimensional convolutional neural network (1D CNN). Local features and global correlations are extracted from the time series data using the 1D CNN and BiLSTM, with the latter being able to extract enough features in the opposite direction.

The existing learning-based approaches for SS are computationally demanding and have a significant degree of complexity. The existing models need a lot of training data, which is frequently expensive and difficult to get. Therefore, in order to effectively categorize the incoming raw signals while minimizing the computational cost and training data requirements, a more effective and simplified deep learning-based model needs to be developed.

# 10.3.2 Objectives

+   - Develop an efficient and lightweight deep/machine learning (ML)-based model for SS.
- Compare the proposed lightweight deep/ML-based model with existing methods for SS.

# 10.3.3 Proposed work

# 10.3.3.1 DL-based spectrum sensing method

Here, I proposed a SS technique for CR systems on DL. This approach uses unprocessed signal data; no prior understanding of the noise level or signal strength of the PU is required. The suggested SS technique uses artificial neural networks, adaptive fuzzy modeling, and training data. First, the training data gathered during the primary and secondary users sensing