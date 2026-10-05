+   - Feature extraction from text (**Comments**) and dates (**JoinDate**).

+   - Categorical encoding for **Department**.

+   - Numeric transformations or binning for **Experience** and **Salary.**

+   - Feature selection to identify which variables most influence downstream predictions.

In the following subsections, we will apply traditional and AI-assisted approaches to automate the feature engineering process on this dataset.

# Feature extraction from categorical and text data

Categorical and text features often hold rich, meaningful information, but must be transformed into numerical formats before machine learning models can use them effectively. This transformation is a core part of feature extraction, and the proper technique depends on the data's nature and the complexity of the model used.

# Traditional approach

One of the most common techniques for categorical variables like **Department** is one-hot encoding, which creates a separate binary column for each category.

The following line applies one-hot encoding to the **'Department'** column:

```
# One-hot encoding for Department
df = pd.get_dummies(df, columns=['Department'], drop_first=True)
```

When working with free-text fields like **Comments, term frequency-inverse document frequency (TF-IDF)** is often used to extract key terms that can be fed into models.