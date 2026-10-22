# Model generation code

This is the code that specifies how your model was created, such as:

+   - What frameworks it used
+   - How it was trained
+   - The details on how the train/valid/test splits were created
+   - The number of experiments run
+   - The range of hyperparameters considered
+   - The actual set of hyperparameters that final model used

Very often, data scientists generate models by writing code in notebooks. Companies with more mature pipelines make their data scientists commit the model generation code into their Git repos on GitHub or GitLab. However, in many companies, this process is ad hoc, and data scientists don’t even check in their notebooks. If the data scientist responsible for the model loses the notebook or quits or goes on vacation, there’s no way to map a model in production to the code that generated it for debugging or maintenance.

# Experiment artifacts

These are the artifacts generated during the model development process, as discussed in the section “Experiment Tracking and Versioning” on page 162. These artifacts can be graphs like the loss curve. These artifacts can be raw numbers like the model’s performance on the test set.

# Tags

This includes tags to help with model discovery and filtering, such as owner (the person or the team who is the owner of this model) or task (the business problem this model solves, like fraud detection).

Most companies store a subset, but not all, of these artifacts. The artifacts a company stores might not be in the same place but scattered. For example, model definitions and model parameters might be in S3. Containers that contain dependencies might be in ECS (Elastic Container Service). Data might be in Snowflake. Experiment artifacts might be in Weights & Biases. Featurize and prediction functions might be in AWS Lambda. Some data scientists might manually keep track of these locations in, say, a README, but this file can be easily lost.