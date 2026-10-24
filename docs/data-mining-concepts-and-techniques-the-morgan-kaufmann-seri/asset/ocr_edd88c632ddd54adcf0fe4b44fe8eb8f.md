more learnable parameters); however, higher model complexity might cause the overfitting issue of the model (i.e., high variance), which results in a tension in terms of simultaneously minimizing both bias and variance. We leverage bias-variance decomposition to mathematically analyze the generalization error of a learning algorithm as follows.

Given a set of i.i.d. samples, \(D = \{(\mathbf{x}_1, y_1), \dots, (\mathbf{x}_n, y_n)\}\) that are drawn from \(P(X, Y)\), we denote the learned model from \(D\) as \(f_D(\cdot)\). The generalization error (i.e., expected test error) in the squared loss is computed as

\(\mathbb{E}_{(\mathbf{x}, y) \sim P}[(f_D(\mathbf{x}) - y)^2] = \int_{\mathbf{x}, y} (f_D(\mathbf{x}) - y)^2 P r(\mathbf{x}, y) d\mathbf{x} dy.\)

We can think of \(f_D(\cdot)\) as a random variable of learning model from data set \(D\). Then, we can represent the expected learning model as \(\bar{f}(\cdot)\). The expected test error can be further decomposed as

\(\mathbb{E}_{\mathbf{x}, y, D}[(f_D(\mathbf{x}) - y)^2] = \mathbb{E}_{\mathbf{x}, y, D}[(f_D(\mathbf{x}) - \bar{f}(\mathbf{x}) + \bar{f}(\mathbf{x}) - y)^2] = \mathbb{E}_{\mathbf{x}, D}[(f_D(\mathbf{x}) - \bar{f}(\mathbf{x}))^2] + \mathbb{E}_{\mathbf{x}, y}[(\bar{f}(\mathbf{x}) - y)^2].\)

Eq. (A.13) holds because \(\mathbb{E}_{\mathbf{x}, y, D}[(f_D(\mathbf{x}) - \bar{f}(\mathbf{x}))(\bar{f}(\mathbf{x}) - y)] = 0\). We find that the first term \(\mathbb{E}_{\mathbf{x}, D}[(f_D(\mathbf{x}) - \bar{f}(\mathbf{x}))^2]\) on the right-hand side is the variance, and similarly, we decompose the second term \(\mathbb{E}_{\mathbf{x}, y}[(\bar{f}(\mathbf{x}) - y)^2]\) as

\(\mathbb{E}_{\mathbf{x}, y}[(\bar{f}(\mathbf{x}) - y)^2] = \mathbb{E}_{\mathbf{x}, y}[(\bar{f}(\mathbf{x}) - \bar{y} + \bar{y} - y)^2] = \mathbb{E}_{\mathbf{x}, y}[(\bar{f}(\mathbf{x}) - \bar{y})^2] + \mathbb{E}_{\mathbf{x}, y}[(\bar{y} - y)^2].\)

where the second step is due to the fact that \(\mathbb{E}_{\mathbf{x}, y}[(\bar{f}(\mathbf{x}) - \bar{y})(\bar{y} - y)] = 0\). The first term \(\mathbb{E}_{\mathbf{x}, y}[(\bar{f}(\mathbf{x}) - \bar{y})^2]\) represents squared bias, and the second term \(\mathbb{E}_{\mathbf{x}, y}[(\bar{y} - y)^2]\) is the data noise that cannot be removed.

From the above decomposition, we observe that the expected test error (i.e., generalization error) is composed of the bias, variance, and data noise.

# A.1.6 Cross-validation and Jackknife

# Cross-validation

Data used for training data mining models are usually split into a training set, a validation set, and a test set. The model with the best performance on the validation set is finally evaluated on the test set. However, this split method is not suitable for applications with scarce data, because we want to train the model with as much data as possible. Cross-validation can be used to address this challenge. For \(k\)-fold cross validation, the original data set is split into \(k\) chunks. In each time, the model is trained with \(k - 1\) chunks (i.e., folds) and validated on the remaining chunk. This procedure is repeated \(k\) times and the final performance score (e.g., the classification accuracy) is the average of the performance scores from \(k\) runs. If we let \(k = n\), where \(n\) is the total number of samples in the data set, this technique is called leave-one-out cross-validation.