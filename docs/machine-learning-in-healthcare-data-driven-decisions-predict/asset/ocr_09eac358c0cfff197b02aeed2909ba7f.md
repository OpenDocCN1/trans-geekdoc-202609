# **Output:**

+   - Final ensemble classifier \( H(x) = sign\left( \sum_{t=1}^T \beta_t h_t(x) \right) \)

# **Step 1: Initialize sample weights**

Assign uniform weights to each training instance: \( w_i^{(1)} = \frac{1}{N}, \forall i = 1, 2, ..., N \)

# **Step 2: For each boosting round** \( t = 1 \) **to** \( T \), **perform the following:**

# **Step 2.1: Train base learner**

+   - Train a base classifier \( h_t(x) \) using the current weighted dataset \( \left\{ \left( x_i, y_i, w_i^{(t)} \right) \right\} \)

# **Step 2.2: Compute weighted classification error**

\( Error_t = \sum_{i=1}^N w_i^{(t)} \cdot I\left( h_t(x_i) \neq y_i \right) \)

# **Step 2.3: Calculate learner complexity**

+   - Compute a complexity score based on model structure:

+   - For decision trees: depth or number of leaf nodes

+   - For logistic regression: number of nonzero weights

+   - For naive Bayes: variance in class-conditional probabilities

Complexity\( (h_t) \)

# **Step 2.4: Compute regularized loss**

\( Loss_{HRAB}(t) = a_t \cdot Error_t + \lambda \cdot Complexity(h_t) \)

# **Step 2.5: Compute ensemble weight**

\( \beta_t = \frac{1}{Loss_{HRAB}(t) + \delta} \)

where \( \delta \) is a small constant to prevent division by zero (e.g., \( \delta = 10^{-6} \)).

# **Step 2.6: Update sample weights**

+   - Update instance weights to emphasize incorrectly classified samples and reduce focus on overly complex models:

\( w_i^{(t+1)} = w_i^{(t)} \cdot exp\left( \beta_t \cdot I\left( h_t(x_i) \neq y_i \right) \right) \)

+   - Normalize weights:

\( w_i^{(t+1)} = \frac{w_i^{(t+1)}}{\sum_{j=1}^N w_j^{(t+1)}} \)