The role of the ML platform in ML governance documentation is usually to provide data points that feed into the formal risk management documentations or generate some of the ready-to-use reports. Specifically, an ML platform must be able to track, store, and report the following data points:

+   - Data quality metrics such as data descriptions, statistics, bias, and errors

+   - Model metrics and validation results in development and testing

+   - Model bias and explainability reports

+   - Model performance monitoring results in production

Amazon SageMaker can produce data and documentation to be included in model risk documentations. Specifically, SageMaker tracks and produces the following information that is relevant for ML governance documentation:

+   - **Model metrics:** SageMaker Training Service Clarify tracks model metrics as training errors and validation errors.

+   - **Data and model bias reports:** SageMaker Clarify is the bias detection component in SageMaker. If you enable SageMaker Clarify, you can get data and model bias reports for training data and trained model. The data and model bias reports provide details such as imbalances in training data and prediction behavior across different ages and genders.

+   - **Model explainability reports:** SageMaker Clarify also provides a model explainability feature. It uses SHAP to explain the contribution of each input to the final decision. You can find out more about SHAP at `https://shap.readthe.io/en/latest/index.html`.

There are various tools for generating data quality reports. For example, AWS DataBrew can be used to profile input data and generate data quality reports. It reports data statistics such as data distribution, correlation, and missing values.

These data points are available via SageMaker and the DataBrew UI and API can be manually extracted to meet your needs. However, to operationalize the process, you should implement automated extraction jobs to extract data points from SageMaker and DataBrew and store them in a purpose-built data store for model risk management. Depending on the business requirements, data from the data science environment, testing environment, or production hosting environment can be extracted for documentation purposes.