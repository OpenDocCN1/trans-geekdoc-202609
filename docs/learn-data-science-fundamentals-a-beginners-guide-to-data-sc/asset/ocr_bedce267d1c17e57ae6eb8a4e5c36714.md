into a numerical format. Common encoding techniques include:

+   - One-Hot Encoding: This method creates a binary column for each category, indicating the presence (1) or absence (0) of that category for each observation. example, if a feature has three categories (red, blue, green), one-hot encoding will create three binary features. This technique is effective for nominal data but can lead to a high number of features, especially with high cardinality categorical variables, which may introduce the curse of dimensionality

**Label Encoding:** This technique assigns a unique integer to each category. While simple, it can introduce unintended ordinal relationships between categories, which may mislead certain algorithms that rely on distance calculations

For example, assigning 0 to "red," 1 to "blue," and 2 to "green" implies a ranking that does not exist.

+   - **Target Encoding:** This method replaces each category with the mean of the target variable for that category. It can be particularly effective for high-cardinality categorical features but requires careful handling to avoid data leakage during model training
- **Ordinal Encoding:** Used for ordinal data, this technique assigns integers based on the rank order of the categories. For example, customer satisfaction levels could be encoded as 1 (poor), 2 (fair), 3 (good), and 4 (excellent).
- **Handling High Cardinality:** When dealing with categorical variables with many unique categories, techniques such as target encoding or feature hashing may be employed to reduce dimensionality while retaining meaningful information.
- **Feature Engineering:** Creating new features from existing categorical data can help improve model performance. Techniques include:

+   - Interaction Variables: Combining two or more categorical features to capture their joint effect on the target variable.