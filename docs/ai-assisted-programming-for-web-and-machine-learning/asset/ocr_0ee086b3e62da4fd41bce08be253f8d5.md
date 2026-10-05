imbalance, etc.).

Example:
I have a CSV file with columns: 'age', 'gender',
'income', and 'purchased' (0 or 1). It is an
imbalanced classification problem. Can you help
me create a preprocessing pipeline using scikit-learn?

+   Be specific with the task:
Specify what you need:
* Full pipeline or partial (e.g., just preprocessing)?
* Which libraries to use (e.g., scikit-learn, pandas)?
* Whether to include validation or performance metrics.

Example:
Using scikit-learn, write code to one-hot encode categorical variables, imput missing values with median, and scale numeric features. Add cross-validation using StratifiedKFold.

+   Use prompt framing techniques:
Use structured prompts like:
* Write a function to...
* Generate Python code for...
* What’s the best way to
This helps ChatGPT generate cleaner, reusable code.

# Prompt examples for best practice

To illustrate how well-structured prompts can guide ChatGPT effectively, the following table presents example scenarios along with corresponding prompts that demonstrate best practices in prompt crafting:

| Scenario | Well-crafted prompt |
| Binary classification with missing values | Create a pipeline using scikit-learn for logistic regression with missing values in numerical |