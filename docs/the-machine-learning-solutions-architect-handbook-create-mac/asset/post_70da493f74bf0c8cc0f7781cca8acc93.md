
The model explainability report is also directly accessible via Studio UI. You can navigate to the report by going to SageMaker Components and Registries | Experiments and trials | Unassigned trials. Then, right-click the latest clarify-explainability-XXXX job and select Open in trial details. Finally, on the Model explanation fact. In this example, you will see that this is the most important feature that influences predictions.

## Training privacy-preserving models

In this last part of the hands-on lab, you will learn how to use differential privacy for privacy-preserving training model:

- Create a new folder "differential-privacy" under the chapter 11 folder. Download the notebook at https://github.com/PackPublishing/The-Machine-Learning-Solutions-Architect-Handbook/blob/main/Chapter11/churn_privacy.ipynb and upload it to the newly created differential-privacy folder.

- Run all the cells in the notebook and take note of the training losses at the end. We are not going to explain all the details in this notebook; it simply trains the simple neural network using the same churn dataset we have been using.

- Now, we must modify this notebook to implement differential privacy model training using the PyTorch opacus package. You can also download the modified notebook from https://github.com/PackPublishing/The-Machine-Learning-Solutions-Architect-Handbook/blob/main/Chapter11/churn_privacy-modified.ipynb.

- Specify the parameters for the opacus package's PrivacyEngine object. Here, noise_multiplier is the ratio of the standard deviation of Gaussian noise to the sensitivity of the function to add to noise, while max_per_sample_grad_norm is the maximum value greater than this norm will be clipped. The sample_rate value is used for figuring out how to build batches for training:

```
max_per_sample_grad_norm = 1.5
sample_rate = batch_size/len(train_ds)
noise_multiplier = 0.8
```

5. Next, we must wrap the privacy engine around the model and optimizer and kick off the training process:

```
from opacus import PrivacyEngine
net = get_CHURN_model()
optimizer = optim.Adam(net.parameters(),
weight_decay=0.0001, lr=0.003)
privacy_engine = PrivacyEngine(
net,
max_grad_norm=max_per_sample_grad_norm,
noise_multiplier = noise_multiplier,
sample_rate = sample_rate,
)
privacy_engine.attach(optimizer)
model = train(trainloader, net, optimizer, batch_size)
```

If you compare the training loss with the losses you observed earlier without the privacy engine, you will notice some small degradations in the losses across all epochs.

6. Now, let's measure the potential privacy loss with this model:

```
epsilon
```

You will see values for ε and δ. As we discussed earlier, ε is the privacy loss budget, the probability that output can change by adding or removing one record from the training data. δ is the probability of failure that information is accidentally leaked.

Congratulations! You have successfully used SageMaker to detect data and model bias, explain feature importance for a model, and trained a model using differential privacy. All these capabilities are highly relevant to ML governance.

## Summary

In this chapter, we covered the ML governance framework and some of its core components. Now, you should have a fundamental understanding of the model risk management framework and its processes and be able to describe the core requirements for implementing ML governance. You should also be able to identify some of the technology capabilities in AWS that support model risk management processes, such as bias detection and model drift detection. The lab section should have provided you with hands-on experience of using SageMaker to implement bias detection, model explainability, and privacy-preserving model training. In the next chapter, we are going to change gear a bit and talk about AI services, including how AI services should be used in combination with ML platforms to support different ML solutions.

# 12
## Building ML Solutions with AWS AI Services

You have come a long way and we are getting close to the finishing line. Up to this point, we have mainly focused on the skills and technologies required to build and deploy ML models using open source technologies and managed ML platforms. To solve business problems with machine learning, however, you don't have to build, train, and deploy your ML models from scratch. An alternative option is to fully managed AI services. AI services are also fully managed APIs or applications with pre-trained models that perform specific ML tasks, such as object detection or sentiment analysis. Some AI services also allow you to train custom models with your data for a defined ML task, such as document classification. AI services promise to enable organizations to build ML-enabled solutions without requiring strong ML competencies.

In this final chapter, we are going to switch gears and talk about several AWS AI services and where they can be used in business applications. Please note that the focus of this chapter will not be to dive deep into individual AI services, as warrants dedicated books. Instead, we will focus on ML use cases that can be powered by AI services, and the architecture patterns that you can use to deploy these AI services. After reading this chapter, you should be able to identify some use cases where AI services can be a good fit and where to find the additional resources to get a deeper understanding of these services. Specifically, we are going to cover the following topics:

- What are AI services?
- Overview of the AWS AI Services
- Building intelligent solutions using AI services
- Designing an MLOps architecture for AI services
- Hands-on lab – running ML tasks for AI services

## Technical requirements

You will continue to use our AWS environment for the hands-on portion of this book. The associated code samples can be found at https://github.com/PacktPublishing/The-Machine-Learning-Solutions-Architect-Handbook/tree/main/Chapter12.

## What are AI services?

AI services are pre-built fully managed services that perform a particular set of ML tasks out of the box, such as facial analysis or text analysis. The primary target users for AI services are application developers who want to build AI applications without the need to build ML models from scratch. In contrast, the target audiences for ML platforms are data scientists and ML engineers, who need to go through the full ML life cycle to build and deploy ML models. For an organization, AI services mainly solve the following challenges:

- Lack of high-quality training data for ML model development: To train high-quality models, you need a large amount of high-quality curated data. For many organizations, data poses many challenges in data sourcing, data engineering, and data labeling.

- Lack of data science skills for building and deploying custom models: Data science and ML engineering skills are scarce in the market and expensive to acquire.

- Slow product time-to-market: Building and deploying custom models and engineering infrastructure is time-consuming. This can be a hurdle for a quick time-to-market product delivery goal.

- Undifferentiated capabilities: Many ML problems can be solved using commodity ML capabilities that do not provide unique competitive advantages. Spending resources on building undifferentiated capabilities can be a waste of scarce resources.

- System scalability challenge: Managing scalable infrastructure to meet the dynamic market demands and growth is an engineering challenge.

While AI services can provide a cost-effective way for building ML-enabled products quickly, they come with limitations. The main limitations are the lack of customization flexibility for specific functional and technical requirements. AI services usually focus on specific ML tasks with a predefined set of algorithms, so usually you don't have the flexibility to alter the functionality of the AI services. With AI services, you normally do not access to the underlying models, thus limiting your ability to deploy the model elsewhere.

The number of offerings in AI services has grown extensively in recent years, and we expect this trend to continue at an accelerated pace. Next, we will talk about several AWS AI services.

## Overview of AI services

AWS provides AI services in multiple machine learning domains such as text and vision, as well as AI services for industrial use cases such as manufacturing anomaly detection and predictive maintenance. In this section, we will cover a subset of AWS AI services. The objective of this section will not be to deep dive into individual services, but rather make you aware of the fundamental capabilities offered by these AI services. This will let you know where and how these services can be integrated into your applications.
