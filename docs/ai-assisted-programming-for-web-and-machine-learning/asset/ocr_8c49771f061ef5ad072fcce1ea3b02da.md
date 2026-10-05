| mobile and embedded deployments | like logistic regression or shallow neural nets. |

**Table 8.3:** Key criteria for algorithm selection and AI tool guidance

Understanding these criteria empowers practitioners to use AI-assisted tools more effectively, transforming vague prompts into precise, context-aware instructions that lead to better modeling outcomes.

# Prompt driven algorithm recommendation

AI-powered coding assistants like ChatGPT and GitHub Copilot deliver their most valuable insights when guided by precise, well-structured prompts. By clearly stating the machine learning task, dataset characteristics, and evaluation goals, developers can obtain highly relevant model recommendations, reasoning, preprocessing suggestions, and even ready-to-execute code.

The following is an example illustrating how prompt engineering directly influences the quality of algorithmic recommendations:

+   **Example prompt:** "Suggest a model for binary classification with a small, imbalanced dataset."

+   **AI response (ChatGPT):** The following AI-generated recommendations demonstrate effective strategies for handling class imbalance in classification tasks:
- Logistic regression with **class_weight='balanced**
- Random forest with controlled depth **(max_depth)** to avoid overfitting
- SMOTE + Gradient boosting to address class imbalance with resampling
- **Evaluation guidance:** Use F1 score or ROC-AUC to measure performance on imbalanced classes

+   **Copilot insight:** When you begin a line with **model =