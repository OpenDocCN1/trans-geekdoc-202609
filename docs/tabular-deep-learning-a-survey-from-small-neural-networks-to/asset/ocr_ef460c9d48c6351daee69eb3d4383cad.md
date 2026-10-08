# Library

# Description

| scikit-learn | A library dedicated to learning in Python, containing dozens of ML models for different types of tasks, and tools for data analysis. |

| Categorical Encoding | Scikit-learn compatible set of methods for encoding categorical variables |

| imbalanced-learn | Scikit-learn compatible set of models and evaluation metrics for re-sampling unbalanced data |

| Qolmat | Provides a number of methods for imputation of missing values |

| PyTorch tabular | High-level library based on PyTorch and PyTorch Lightning for deep learning, implements NODE, TabNet, TabTransformer, FT Transformer, DANETs, and others. |

| PyTorch Frame | A modular deep learning framework for building neural networks on heterogeneous data |

| DeepTables | An open-source toolkit that builds deep learning models as Wide & Deep, DeepFM, DCN (Deep Cross Network), and PNN (Product Neural Network) |

| pytorch-widdee | A deep learning library that specializes in Wide & Deep models and multi-modal inputs. It allows tabular data (both dense and categorical features) with images in a single model

| Fastai tabular | A library for tabular deep learning that includes Mamba, TabTransformer, FTTransformer, TabM and tabular ResNets, and others

| Mambular | |

| TINT01b | PyTorch library for transforming tabular data into images with 2-Dimensional-Convolutional Neural Networks |

| PyTorch frame | A modular framework for building neural networks on heterogeneous data |

| TabularS3DA | A PyTorch-based library to facilitate semi- and semi-supervised learning with tabular neural network interpretability |

| Captum | |

Table 11: Tabular learning libraries in PyTorch

![](bbox=[0.167, 0.503, 0.832, 0.613])

Figure 16: Suggestions for tabular model choice

ance and small sample size. SMOTE, or derivatives, are one of the most widely used algorithms to handle the minority class. Over time, however, there have several reports on whether this algorithm can bring improved performance. SMOTE seems to work well with categorical variables but less with continuous distributions. Also considered a simple method to capture the complexity of real tabular data. Methods based on GAN, autoencoder, and diffusion models have been developed in recent years to obtain better modeled synthetic tabular examples. As example, different types of models achieve better results than SMOTE. They have a much higher computational cost and more complexity for training, complicating their adaption by the community. To date, despite its limitations, SMOTE remains one of the most widely used

algorithms. Another interest is the use of synthetic data for training (or in other cases, mentioning the) of tabular deep learning models. The use of synthetic data for overcoming data scarcity, potentially generating a virtually unbiased sample while significantly reducing the data collection effort. It also reduces the preprocessing effort. Another advantage is that synthetic data respects privacy, avoiding compliance issues and rules of legal privacy. At the same time, data can be generated with bias reduction to reduce bias in real datasets. Or datasets can be created to study phenomena in particular, especially when the data needed are difficult to collect. However, synthetic data does not capture the complexity of real data, nor of the causal relationships between variables. In addition, the real data has anomalies that are smoothed in