The cardinality checks, Chi-squared test, and entropy can be used for categorical variables.

Control charts and histogram intersections can be used to detect a drift in data.

Finally, there are several platforms for model monitoring, such as WhyLabs, and libraries, such as deepchecks, and alibi-detect. They come with easy integrations and a ready framework for drift detection. The best part about this is that most of them provide a drift detection framework, storage for logs and historical data, intuitive monitoring dashboards, and alert mechanisms for critical events.

# Addressing the drift in ML

Once you detect the drift in the ML model, it can be addressed in the following ways:

# Data quality issues

If there is an issue with input data, then it can be easily fixed. For instance, high-resolution images were provided for training face recognition models; however, low-resolution images were passed to the deployed model.

# Retraining the model

After detecting the data or concept shift, retraining the model with recent data can improve its performance. Sometimes production data is not sufficient to train the model. In that case, you can combine historical data with recent production data and give more weight to recent data.

Here are four strategies for retraining the model:

+   - **Periodically retraining**: Scheduling it at a fixed time, for instance, every Monday at 10 PM
+   - **Data or event-driven**: When new data is available
+   - **Model or metric driven**: When accuracy is lower than a threshold or SLA
+   - **Online learning**: Where the model continuously learns in real-time or near real-time on the latest data

# Rebuilding or tuning the model

If retraining the model doesn’t work, then you may need to consider rebuilding it or tuning it on recent data. You can automate this using a pipeline.