
Overfitting, on the other hand, occurs when a model is too complex and captures noise along with the underlying patterns, leading to poor generalization on new data. Put differently, when a model overlearns a dataset, to the extent of learning all the noise and errors in the dataset, the model has overfitted its training data.

This is illustrated by the dotted black line in the regression plot (degree 15 polynomial in [Figure 5.7](#c005.xhtml#c05-fig-7)) and the classification plot (degree 25 polynomial in [Figure 5.8](#c005.xhtml#c05-fig-8)). To address overfitting, techniques such as regularization (L1 or L2), pruning (in decision trees), and dropout (in neural networks) can be employed. Additionally, reducing the model’s complexity by selecting a lower-degree polynomial or using fewer features can help prevent overfitting. For instance, the optimal fitting models in both regression and classification plots strike a balance between capturing the data’s patterns without being overly complex.

Overfitting is similar to a student who prepares for an exam by studying with only a single source of information. Even though the student may feel fully prepared because they learned really well from the (only) study material, if the exam questions differ in content and scenarios from the study material, they may struggle to pass the exam. This is because they learned too well from the training material (e.g., they memorized the answers from the practice exams without truly understanding the concepts) and are unable to generalize to real-world scenarios that may happen while taking the actual exam or trying to solve an unseen problem at work.

For the exam, it is important you understand how regularization is an effective technique to address overfitting, which is covered in the next section.

### Regularization

Regularization helps prevent your model from overfitting by adding a penalty term to the loss function, which the model aims to minimize during training. This penalty “discourages” the model from becoming too complex and fitting the training data too closely. There are different types of regularization techniques, including L1 regularization (LASSO), L2 regularization (Ridge), and Elastic Net:

*   **L1 regularization (LASSO)** L1 regularization, also known as LASSO (least absolute shrinkage and selection operator), is commonly used in regression problems. It adds a penalty term `λ` to the loss function that is proportional to the sum of the absolute values of the model’s coefficients. The formula for the loss function with L1 regularization in the context of linear regression can be written as follows:

```
L(w) = L_original(w) + λ Σ|w_i| (i=1 to n)
```

*   In the formula, `L(w)` is the regularized loss function, `L_original(w)` is the original loss function (e.g., MSE for regression), `w_i` are the model’s coefficients, `λ` is the regularization parameter, and `n` is the number of coefficients.

*   The regularization parameter `λ` controls the strength of the regularization by scaling the penalty applied to the model’s coefficients. When `λ` is small, the penalty is small, and the regularization effect is minimal, allowing the model to fit the training data more closely. When `λ` is large, the penalty is significant, forcing more coefficients to zero and resulting in a simpler, sparser model.

*   L1 regularization encourages sparsity in the model’s parameters, making it particularly useful for feature selection in regression problems. By driving some coefficients to zero, it effectively removes less relevant features, resulting in a simpler and more interpretable model.

*   Moreover, due to the nature of its penalty term, L1 regression is particularly robust (less sensitive) to outliers. This is because L1 regularization penalizes the absolute values of the coefficients, which don’t amplify the effect of outliers as much as the squared term in L2 regularization—outliers typically result in large coefficients.

*   These characteristics of L1 regularization (driving sparsity and robustness to outliers) make it an ideal regularization technique to prevent your model from overfitting its training data. L1 regularization excels in scenarios when you have a high-dimensional dataset with many features and you want to focus on the most relevant ones while mitigating the influence of outliers that could skew the model’s performance.

*   **L2 regularization (Ridge)** L2 regularization, known as Ridge regression, is also used in regression problems. It adds a penalty term to the loss function that is proportional to the sum of the squared values of the model’s coefficients. The formula for the loss function with L2 regularization in the context of linear regression can be written as follows:

```
L(w) = L_original(w) + λ Σ w_i^2 (i=1 to n)
```
