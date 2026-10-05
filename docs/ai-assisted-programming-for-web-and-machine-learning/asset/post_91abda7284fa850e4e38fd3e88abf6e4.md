
In many real-world ML scenarios, datasets contain a mix of numerical and categorical features. Handling these diverse data types efficiently and consistently is critical for building robust models. Scikit-learn’s ColumnTransformer provides a clean and modular approach to applying different preprocessing steps to each type of feature.

Let us consider a practical example. Suppose we are working with a dataset that includes:

- **Numerical features**: account_age, monthly_spending
- **Categorical features**: region, plan_type

We can construct a preprocessing pipeline that applies StandardScaler to numerical columns and OneHotEncoder to categorical ones. This composite preprocessor is then integrated into a full ML pipeline using RandomForestClassifier.

Here is how it looks in the code:

```python
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import StandardScaler, OneHotEncoder
from sklearn.pipeline import Pipeline
from sklearn.ensemble import RandomForestClassifier
numeric_features = ['account_age', 'monthly_spending']
categorical_features = ['region', 'plan_type']
preprocessor = ColumnTransformer(
    ('num', StandardScaler(), numeric_features),
    ('cat', OneHotEncoder(handle_unknown='ignore'), categorical_features)
)
pipeline = Pipeline([
    ('preprocessor', preprocessor),
    ('classifier', RandomForestClassifier())
])
```

This pipeline ensures that the numerical and categorical data are processed appropriately before reaching the classifier. The parameter handle_unknown='ignore' in OneHotEncoder is especially important because it prevents the model from crashing during inference when it encounters unseen categories not present during training.

**Copilot insight**: AI assistants like GitHub Copilot often include helpful safeguards—as handle_unknown='ignore' in scikit-learn's OneHotEncoder—by default or through suggestions. These features anticipate common runtime errors and enhance production readiness without requiring explicit user intervention.

AI tools like ChatGPT and GitHub Copilot simplify the creation of robust, real-world-ready pipelines by intelligently automating complex steps such as encoding, imputation, cross-validation, and metric evaluation. It is essential to fully leverage these tools, especially when using ChatGPT for code generation.

# Guidelines for effective prompt usage in ChatGPT

To maximize the benefits of ChatGPT in code generation and data pipeline automation, it is important to structure prompts thoughtfully. The following guidelines will help you craft prompts that yield more accurate, relevant, and context-aware responses:

1. Provide sufficient context about your data:
Clearly describe:
- The structure of your dataset (columns, data types),
- The problem type (classification, regression, etc.),
- Any special constraints (missing values, class imbalance, etc.).

Example:
I have a CSV file with columns: 'age', 'gender', 'income', and 'purchased' (0 or 1). It is an imbalanced classification problem. Can you help me create a preprocessing pipeline using scikit-learn?

2. Be specific with the task:
Specify what you need:
- Full pipeline or partial (e.g., just preprocessing)?
- Which libraries to use (e.g., scikit-learn, pandas)?
- Whether to include validation or performance metrics.

Example:
Using scikit-learn, write code to one-hot encode categorical variables, imput missing values with median, and scale numeric features. Add cross-validation using StratifiedKFold.

3. Use prompt framing techniques:
Use structured prompts like:
- Write a function to...
- Generate Python code for...
- What’s the best way to...
This helps ChatGPT generate cleaner, reusable code.

# Prompt examples for best practice

To illustrate how well-structured prompts can guide ChatGPT effectively, the following table presents example scenarios along with corresponding prompts that demonstrate best practices in prompt crafting:

| Scenario | Well-crafted prompt |
| :--- | :--- |
| Binary classification with missing values | Create a pipeline using scikit-learn for logistic regression with missing values in numerical columns. Use median imputation and StandardScaler. |
| Encoding unknown categories | How to one-hot encode a categorical column in scikit-learn while ignoring unseen categories during prediction? |
| Model evaluation with class imbalance | Use StratifiedKFold with 5 splits to evaluate an imbalanced classification model using ROC-AUC as the scoring metric. |

**Table 8.2:** Example scenarios with well-crafted ChatGPT prompts for common ML tasks

By following these prompt engineering techniques, users can extract highly accurate, context-aware, and reusable code from ChatGPT relying on GitHub Copilot for real-time code suggestions and corrections in the IDE.
