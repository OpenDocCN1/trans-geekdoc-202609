# 1.3 Approaches

Large amounts of data can diminish the efficiency of data mining and may not provide significant inputs to the model. Non-essential attributes add noise to the data, expanding the size of the model. Moreover, model building and scoring leads to consumption of time and system resources, influencing model precision.

Likewise, huge data sets may contain groups of attributes that are associated and may quantify a similar hidden component which can skew the logic of the algorithm. The computation cost associated with algorithmic processing increases with higher dimensionality of processing space, posing challenges for data mining algorithms. Impacts of noise, correlation, and high dimensionality can be minimized by dimension reduction using feature selection and feature extraction [10].

# 1.3.1 Feature Selection

Feature Selection selects the most relevant attributes by identifying the most pertinent characteristics and eliminating redundant information. A small size feature vector is used to reduce computational complexity, basic for online individual acknowledgment. Determination of effective features also helps increase precision [11]. Traditionally, large dimensions of feature vectors can be reduced using Principal Component Analysis (PCA) and Linear Discriminant Analysis (LDA).

The importance of a feature set S, for class c, is characterized by the normal estimation of all common data values between the individual feature f_i and class c as follows:

```
D(S,c) = \frac{1}{|S|} \sum_{f_i \in S} I(f_i;c) .
```

The repetition of all features in set S is the normal estimation of all common data values between feature f_i and feature f_j:

```
R(S) = \frac{1}{|S|^2} \sum_{f_i f_j \in S} I(f_i;f_j)
```

# 1.3.2 Feature Extraction

Feature extraction extracts distinct features from samples represented in a feature vector. Thus, alteration of attributes takes place in this method, whereas