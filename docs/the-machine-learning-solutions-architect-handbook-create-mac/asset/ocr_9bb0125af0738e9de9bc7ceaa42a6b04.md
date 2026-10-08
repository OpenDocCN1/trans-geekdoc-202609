4. **Evaluate the model:** In this step, you evaluate the model metrics and determine if they meet the performance target. If they do not, consider retraining the model using higher-quality and/or more data. Personalize outputs several evaluation metrics for the trained models, such as coverage, mean reciprocal recall, precision, and normalized discounted cumulative gain. You can find more details about these metrics at https://docs.aws.amazon.com/personalize/latest/dg/working-with-training-metrics.html. The performance metrics are available in the Personalize management console. You can also get the metrics programmatically using the GetSolutionMetrics API.

5. **Create a campaign:** In this final step, you deploy a solution (trained model) to the prediction endpoint so you can use it in your applications. To do this, you can use the CreateCampaign API. You can also provide additional configurations such as the **minimum provisioned transaction per second (minProvisionedTPS)** throughput, as well as item exploration configuration. Item exploration configuration allows Personalize to show a percentage of random items to users not on user personalization. The idea is to let users explore items they have not interacted with to gauge interest. The item exploration configuration is only applicable for user personalization.

You can use the Personalize management console to build Personalize solutions and campaigns. Alternatively, you can use boto3 to access the Personalize API. The following code sample shows the Python syntax for creating a campaign. You can find the full list of boto3 APIs for Personalize at https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/personalize.html:

```
import boto3
client = boto3.client('personalize')
response = client.create_campaign(
name='name of the campaign',
solutionArn='AWS Arn to the solution',
minProvisionedTPS=<provisioned TPS>,
campaignConfig={
'itemExplorationConfig': {
'<name of configuration>': '<value of configuration>'
}}))
```