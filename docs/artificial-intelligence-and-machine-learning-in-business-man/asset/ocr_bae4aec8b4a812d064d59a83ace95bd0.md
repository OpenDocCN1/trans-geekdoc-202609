# Artificial Intelligence and Machine Learning in Business Management

represents the statistics of different parameters used for the evaluation of model using 2 hidden layers.

In addition to the Generic data set and the Taiwanese data set implementation is also carried out in the European data set. Table 5.3 shows the results from the European data set.

From Table 5.3 it can be seen here, in each of the architectures it has observed that the best results are obtained when the architecture is implemented with sigmoid activation function with two hidden layers. From Table 5.3 it can be illustrated that the MLP architecture with sigmoid activation and two hidden layers are providing precision of 0.87, recall of 0.79, F1 score of 0.83 and MCC score of 0.829. In CNN architecture sigmoid activation and

# TABLE 5.3

# Results from the European Data Set

| Model | NN | Activation | Precision | Recall | F1 | MCC | Tra | Tea | ROC |
|---|---|---|---|---|---|---|---|---||
| MLP | 1 | Relu | 10 | 0.85 | 0.81 | 0.83 | 0.825 | 0.9991 | 0.905 |
| | 2 | Relu | 10 | 0.84 | 0.81 | 0.83 | 0.824 | 0.9985 | 0.9986 | 0.953 |
| | 2 | tanh | 10 | 0.84 | 0.81 | 0.83 | 0.824 | 0.9867 | 0.9966 | 0.938 |
| | 2 | tanh | 10 | 0.84 | 0.81 | 0.83 | 0.824 | 0.9966 | 0.946 | 0.94 |
|  1 | sigmoid | 10 | 0.85 | 0.81 | 0.823 | 0.8983 | 0.9981 | 0.981 |\ |9 2 |
| 12 | 0 10 | 0.87 | 0.79 | 0.829 | 0.9994 | 0.9984 | 0.966 |
| | 1 | swish | 10 | 0.87 | 0.79 | 0.83 | 0.825 | 0.9985 | 0.9985 | 0.967 |
| | 2 | swish | 10 | 0.87 | 0.79 | 0.83 | 0.829 | 0.9984 | 0.9986 | 0.970 |
| CNN | 1 | Relu | 10 | 0.84 | 0.42 | 0.56 | 0.9598 | 0.9989 | 0.973 |
| | 2 | Relu | 10 | 0.83 | 0.78 | 0.80 | 0.8039 | 0.9992 | 0.9993 | 0.889 |
| | 1 | tanh | 10 | 0.85 | 0.80 | 0.8168 | 0.8196 | 0.9993 | 0.954 |
| | 2 | tanh | 10 | 0.85 | 0.80 | 0.8151 | 0.9992 | 0.9996 | 0.967 |
| | 1 | sigmoid | 10 | 0.88 | 0.75 | 0.81 | 0.8137 | 0.9989 | 0.958 |
| 12 2 | sigmoid | 10 | 0.88 | 0.82 | 0.8151 | 0.9991 | 0.9994 | 0.966 |
| | 1 | swish | 10 | 0.84 | 0.73 | 0.78 | 0.7111 | 0.9993 | 0.871 |
| 12 2 | swish | 10 | 0.83 | 0.80 | 0.81 | 0.8136 | 0.9993 | 0.9994 | 0.912 |
| LSTM | 1 | Relu | 10 | 0.87 | 0.65 | 0.694 | 0.9985 | 0.9984 | 0.500 |
| | 2 | Relu | 10 | 0.84 | 0.69 | 0.760 | 0.9984 | 0.9982 | 0.902 |
| | 1 | tanh | 10 | 0.86 | 0.66 | 0.74 | 0.929 | 1.105 | 0.0012 | 0.929 |
| | 2 | tanh | 10 | 0.84 | 0.79 | 0.81 | 0.8165 | 0.4469 | 0.392 | 0.923 |
| | 1 | sigmoid | 10 | 0.84 | 0.81 | 0.8153 | 0.9990 | 0.9986 | 0.946 |
| | 2 | swish | 10 | 0.84 | 0.79 | 0.82 | 0.8153 | 0.9998 | 0.946 |
| | 1 | swish | 10 | 0.86 | 0.72 | 0.78 | 0.709 | 0.9982 | 0.9981 | 0.922 |
| | 2 | swish | 10 | 0.84 | 0.78 | 0.78 | 0.8007 | 0.9994 | 0.9994 | 0.922 |
| GRU | 1 | Relu | 10 | 0.83 | 0.36 | 0.542 | 0.9984 | 0.9985 | 0.910 |
| | 2 | Relu | 10 | 0.82 | 0.39 | 0.53 | 0.5666 | 0.9985 | 0.908 |
| | 1 | tanh | 10 | 0.89 | 0.73 | 0.80 | 0.81 | 0.8007 | 0.0017 | 0.925 |
| | 2 | tanh | 10 | 0.84 | 0.78 | 0.81 | 0.809 | 0.8116 | 0.0659 | 0.931 |
| | 1 | sigmoid | 10 | 0.95 | 0.80 | 0.87 | 0.874 | 0.9995 | 0.9995 | 0.947 |
| | 2 | sigmoid | 10 | 0.96 | 0.82 | 0.89 | 0.868 | 0.9996 | 0.9996 | 0.950 |
| | 1 | swish | 10 | 0.87 | 0.72 | 0.792 | 0.9981 | 0.9981 | 0.9981 | 0.909 |
| | 2 | swish | 10 | 0.86 | 0.78 | 0.82 | 0.817 | 0.9981 | 0.9981 | 0.909 |n