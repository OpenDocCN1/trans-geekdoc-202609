# Table 15.3 Ictal (Seizure), Inter-ictal (Normal), and Pre-ictal (Partial Seizure) subdivision.

| S. no. | Class | Time | Patients | Seizure records | Total segments |
|---|---|---|---|---|---|
| 1 | Seizure | 8 s | 23 | 198 | 1,200 |
| 2 | Normal | 8 s | 23 | 240 | 1,200 |
| 3 | Partial Seizure | 8 s | 23 | 248 | 1,200 |

input to the classifier which is chosen as Softmax to perform classification between a Non-seizure and Seizure signals.

# 15.3.3 Normalization

In this proposed technique, our dataset is having a few variables of big variance and some small variance. So essentially, standardization is utilized when information are considered as an random variable; normalization implies changing to normal distribution. We apply z-score standardization as pre-processing the dataset. Normalization is applied for information preprocessing for learning mechanism. The principle objective of normalization is to enhance the values of numeric sections in the dataset without misjudging differences in the ranges of values [27]. Usually utilized or required just when features have various ranges. Standardization is a more extreme change. The equation which we have utilized for normalizing our dataset is represented as:

```
Z = (x − µ)/σ
(15.1)
```

where Z z-score, x is the random variable, μ is referred as mean, and σ represents standard deviation.

# 15.3.4 Preprocessing Using PCA

The benefit of utilizing Principal Component Analysis (PCA) is that it can extract the valuable data which is required from the EEG dataset and to de-correlate the factors dependent on the extracted data. Perhaps the main properties of PCA is that the Principal Components (PCs) acquired are essentially the linear combinations of the original variables and the weight vector, which is additionally the eigenvector that fulfills the property of