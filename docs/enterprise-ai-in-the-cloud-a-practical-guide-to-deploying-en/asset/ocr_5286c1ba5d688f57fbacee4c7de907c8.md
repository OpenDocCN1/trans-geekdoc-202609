How frequently you review the features will depend upon how frequently your business environment changes.

# Implementing a Model Update Pipeline

You need to have a model update pipeline in place, which gets triggered in the case of any violations in the performance of the model. This pipeline should activate the data prepared pipeline, the feature pipeline, and the CI/CD/CT pipeline.

This retraining process will ensure that the new data is cleansed before feeding into the model and new features are engineered, if required, in the CI/CD/CT pipeline, ensuring that the model is trained and tested before deploying into production. This way, the model is continuously retrained with new data and can continue to make accurate predictions.

# Keeping Models Fresh with a Scheduler Pipeline

The scheduler pipeline plays a vital role in keeping the AI models fresh. When new data comes into the model, the data distribution and patterns can change, impacting the accuracy of the model predictions. When that happens, it is essential to retrain the model so that its predictions reflect the input data.

For example, the patient's health may depend on several factors. However, these factors can change with time, a phenomenon known as **concept drift**. There may have been a disease outbreak that caused a change in these factors. Under such situations, you need to retrain your model; this is where a scheduler pipeline can greatly help. The scheduler pipeline retrains the model at predefined business intervals, which helps keep the model always reflective of the latest data patterns.

The data preparation pipeline gets activated when the scheduler pipeline activates the retraining process. The data preparation pipeline collects and cleans the new data for use in a model.

At the same time, the feature pipeline gets activated, which extracts the important or relevant features from the prepared data to feed into the model.