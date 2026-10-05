helps ensure reliability and detect issues.
Let us look at an example of a CloudWatch logging setup in
Lambda:

```
import logging
logger = logging.getLogger()
logger.setLevel(logging.INFO)
def lambda_handler(event, context):
    logger.info(f"Received input: {event}")
```

# ChatGPT bonus tip: Ask: How do I set up CloudWatch alarms for Lambda function latency and error rates? ChatGPT will generate both configuration scripts and recommendations for threshold tuning.

# Al-assisted and cloud-based ML development workflow at a glance

The following table outlines the key stages of a typical machine learning workflow, highlighting how tools like ChatGPT and GitHub Copilot enhance each step through automation, optimization, and intelligent code generation, particularly in a cloud-integrated environment:

| Stage | Technology | AI tool contributions |
|---|---|---|
| Data preparation | Pandas, TensorFlow | Generate scripts, resolve missing values, and autocomplete encodings |
| Model training | TensorFlow | Suggest architecture, guide compilation, and optimize hyperparameters |
| Model export | TensorFlow, boto3 | Automate save and S3 upload, ensure format compatibility |
| Deployment | AWS Lambda, SageMaker, S3 | Scaffold API handlers, handle IAM roles and optimize runtime setup |
| Monitoring | AWS CloudWatch | Generate logs, alerts, retention policies, |