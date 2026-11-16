# Feature Consistency

+   - Use the same feature engineering code in training and inference environments.
+   - Use only trusted data sources for training.
+   - Before training, check the quality of the data for outliers or incorrect labels.

# CI/CD/CT Automation

+   - Use the CI/CD/CT pipeline to automate the process of model building, testing, and deploying the models.
+   - Use version control system to track the changes in the model and data.

# Relevant Data

+   - Use a validation dataset representative of the data the model will use in production.
+   - Check for underlying shifts in the patterns and distributions in the training data.
+   - Be on the lookout for drift in data and the model.

Building Robust and Trustworthy Models

# FIGURE 17.13: Reliability best practices

# Ensure Feature Consistency Across Training and Inference

Here are some best practices to ensure feature consistency:

+   - **Unified feature engineering:** Use the same feature engineering code in training and inference environments.
+   - **Trusted data sources:** Use only trusted data sources for training.
+   - **Audit trails:** Implement a robust audit process to replay the activity based on who did it and at what time.
+   - **Data quality assurance:** Before training, check the quality of the data for outliers or incorrect labels.

# Ensure Model Validation with Relevant Data

Here are some best practices for validating data:

+   - **Representative validation data:** Use a validation dataset representative of the data the model that will be used in production.