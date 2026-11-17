
tuning jobs. As the security of your assets in AWS is an essential part of your work, you also learned the various ways to secure SageMaker instances.

AWS products are evolving every day to help you solve IT problems. It’s not easy to remember all the product names. The only way to learn is through practice. When you are solving a problem or building a product, focus on different technological areas of your product. Those areas can be scheduling jobs, logging, tracing, monitoring metrics, autoscaling, and more.

Compute time, storage, and networking are the baselines. It is recommended that you practice some examples for each of these services. Referring to the AWS documentation to resolve any doubts is also a useful option. It is always important to design your solutions in a cost-effective way and exploring cost optimizations when using these services is as important as building the solution itself. I wish you all the best!

## Exam Readiness Drill – Chapter Review Questions

Apart from a solid understanding of key concepts, being able to think quickly under time pressure is a skill that will help you ace your certification exam. That is why working on these skills early on in your learning journey is key.

Chapter review questions are designed to improve your test-taking skills progressively with each chapter you learn and review your understanding of key concepts in the chapter at the same time. You’ll find these at the end of each chapter.

## HOW TO ACCESS THESE RESOURCES

To learn how to access these resources, head over to the chapter titled Chapter 11, Accessing the Online Practice Resources.

To open the Chapter Review Questions for this chapter, perform the following steps:

- 1. Click the link – https://packt.link/MLSC01E2_CH09.

Alternatively, you can scan the following QR code (Figure 9.14):

![](img/87c29232224b00f5a8bba6a66a391700_271_0.png)

Figure 9.14 – QR code that opens Chapter Review Questions for logged-in users

- 2. Once you log in, you’ll see a page similar to the one shown in Figure 9.15:

## Amazon SageMaker Modeling

### Summary

In this chapter, you learned about the usage of SageMaker for creating notebook instances and training instances. As you went through, you learned how to use SageMaker for hyperparameter tuning jobs. As the security of our assets in AWS is an essential part of our work, you also learned the various ways to secure SageMaker instances.

AWS products are evolving every day to help us solve our IT problems. It's not easy to remember all the product names. The only way to learn is through practice. When you're solving a problem or building a product, focus on different technological areas of your product. Those areas can be scheduling jobs, logging, tracing, monitoring metrics, autoscaling, and more.

Compute time, storage, and networking are the baselines. It is recommended that you practice some examples for each of these services. Referring to the AWS documentation to resolve any doubts is also a useful option. It is always important to design your solutions in a cost-effective way and exploring cost optimizations when using these services is equally as important as building the solution itself. I wish you all the best!

![](img/87c29232224b00f5a8bba6a66a391700_272_0.png)

Figure 9.15 – Chapter Review Questions for Chapter 9

- 3. Once ready, start the following practice drills, re-attempting the quiz multiple times.

## Exam Readiness Drill

For the first three attempts, don't worry about the time limit.

### ATTEMPT 1

The first time, aim for at least **40%**. Look at the answers you got wrong and read the relevant sections in the chapter again to fix your learning gaps.

### ATTEMPT 2

The second time, aim for at least **60%**. Look at the answers you got wrong and read the relevant sections in the chapter again to fix any remaining learning gaps.

### ATTEMPT 3

The third time, aim for at least **75%**. Once you score 75% or more, you start working on your timing.

### TIP

You may take more than **three** attempts to reach 75%. That's okay. Just review the relevant sections in the chapter till you get there.

## Working On Timing

Target: Your aim is to keep the score the same while trying to answer these questions as quickly as possible. Here’s an example of how your next attempts should look like:

| Attempt | Score | Time Taken |
|---|---|---|
| Attempt 5 | 77% | 21 mins 30 seconds |
| Attempt 6 | 78% | 18 mins 34 seconds |
| Attempt 7 | 76% | 14 mins 44 seconds |

Table 9.3 – Sample timing practice drills on the online platform

### NOTE

The time limits shown in the above table are just examples. Set your own time limits with each attempt based on the time limit of the quiz on the website.

With each new attempt, your score should stay above 75% while your “time taken” to complete should “decrease”. Repeat as many attempts as you want till you feel confident dealing with the time pressure.

## Model Deployment

In the previous chapter, you explored various aspects of Amazon SageMaker, including different instances, data preparation in Jupyter Notebook, model training with built-in algorithms, and crafting custom code for training and inference. Now, your focus shifts to diverse model deployment choices using AWS services.

If you are navigating the landscape of model deployment on AWS, understanding the options is crucial. One standout service is Amazon SageMaker – a fully managed solution that streamlines the entire **machine learning (ML)** life cycle, especially when it comes to deploying models. There are several factors that influence the model deployment options. As you go ahead in this chapter you will learn different options to deploy models using SageMaker.

### Factors influencing model deployment options

Here are the primary factors that play a crucial role in determining a model deployment option:

- **Scalability requirements**

- **High traffic:** Imagine you are developing a recommendation system for a popular e-commerce platform expecting fluctuating traffic throughout the day. If the application anticipates high traffic and varying loads, services such as Amazon SageMaker with autoscaling capabilities or AWS Lambda may be preferable. This is crucial to maintain performance during peak hours.

- **Real-time versus batch inference**

- **Real-time inference:** Consider a fraud detection system for a financial institution where immediate decisions are essential for transaction approval or denial. For such real-time predictions, services such as Amazon SageMaker and AWS Lambda are suitable. For fraud detection, these services provide low-latency responses, enabling quick decisions on the legitimacy of transactions. Real-time transactions trigger immediate predictions through SageMaker's inference endpoints in this case.

- **Batch inference:** In a healthcare setting, you may need to process a large volume of patient data periodically to update predictive models for disease diagnosis. This is a batch processing use case, and a combination of SageMaker and services such as Amazon S3 can be employed. You can efficiently handle large datasets, perform periodic model updates, and ensure that predictions align with the latest information, which is crucial for maintaining accuracy in healthcare predictions.

- **Infrastructure management complexity**

- **Managed deployment versus custom deployment:** Suppose you are developing a computer vision application for analyzing satellite images, requiring specialized configurations and dependencies. In cases where custom configurations are necessary, opting for custom deployments using EC2 instances allows more control over the infrastructure. SageMaker's managed services are ideal for scenarios where you prioritize ease of management and do not want to delve into intricate infrastructure details.

- **Cost considerations**

- **Pay-per-use:** Consider a weather forecasting application where the computational demand varies based on weather events. AWS Lambda's pay-per-use model is advantageous in situations where the workload fluctuates. You pay only for the compute time consumed, making it cost-effective for applications with sporadic, unpredictable usage patterns compared to alternatives with fixed costs.

### SageMaker deployment options

Amazon SageMaker offers diverse deployment options to deploy ML models effectively. In this section, you will explore different ways of deploying models using SageMaker, providing technology solutions with scenarios and examples.

### Real-time endpoint deployment

In this scenario, you have a trained image classification model, and you want to deploy it to provide real-time predictions for incoming images.

#### Solution

Create a SageMaker model and deploy it to a real-time endpoint.

#### Steps

- 1. Train your model using SageMaker training jobs.
- 2. Create a SageMaker model from the trained model artifacts.
- 3. Deploy the model to a real-time endpoint.

#### Example code snippet

```
from sagemaker import get_execution_role
from sagemaker.model import Model
from sagemaker.predictor import RealTimePredictor
role = get_execution_role()
model_artifacts='s3://your-s3-bucket/path/to/model.tar.gz'
model = Model(model_data=model_artifacts, role=role)
predictor = model.deploy(instance_type='ml.m4.xlarge', endpoint_name='image-classification-endpoint')
```
