
## Azure Cognitive Services

Azure Cognitive Services is a suite of cloud-based APIs and services that helps developers integrate AI and ML capabilities into their applications, websites, and devices.

- Extract entities from audio and videos
- Natural language processing, computer vision, speech recognition
- Extract entities such as key value pairs, tables, and text from forms
- Develop conversational chatbots
- Use AI and NLP to search for data such as images and text
- Draw insights in real time from various sources such as IoT devices, social media clickstreams

![](img/1490b3cf638678afadc8c48abc1698d5_221_0.png)

FIGURE 9.14: Azure-applied AI services

| FEATURE | DESCRIPTION |
|---|---|
| Purpose | Helps developers integrate AI and ML capabilities into their applications, websites, and devices |
| Capabilities | Includes natural language processing, computer vision, speech recognition, and more |
| Use cases | Can improve customer service, fraud detection, product recommendations, image classification, and natural language processing |
| Method | Just make an API call to embed the ability to speak, hear, see, search, understand, and thus include decision-making into the apps |
| Specific services | Can be used for speech-to-text, text-to-speech, speech translation, and speaker recognition |

## Cognitive Services for Language

Cognitive Services for Language offers capabilities such as entity recognition, language translation, sentiment analysis, question answering, conversational language understanding, and translation.

## Cognitive Services for Vision

Cognitive Services for Vision analyzes content within images and videos and provides custom image recognition. It has the following features:

| FEATURE | DESCRIPTION |
|---|---|
| Cognitive service for decisions | Provides content moderation and personalization of experiences for the users, and addresses device problems earlier, all contributing to better decision-making |
| Open API service | Provides an open API service for advanced language models and coding |

## Azure Bot Service

Azure Bot Service is a cloud-based platform for developing conversational chatbots that interact with users across websites, messaging apps, and voice assistants.

TIP Use Azure Applied AI services to integrate AI capabilities into your applications and unlock the power of natural language processing, computer vision, real-time analytics, and intelligent search.

## Azure Stream Analytics

Azure Stream Analytics is a cloud-based analytics platform that draws insights in real-time from various sources, including IoT devices, social media clickstreams, and more. It can integrate with Azure events hubs, Azure IoT hub, and Azure functions to create complex streaming data pipelines.

TIP Azure Stream Analytics can be used to monitor and analyze streaming data in real time, which can help you make better decisions and take action more quickly.

## Azure Cognitive Search

Azure Cognitive Search allows developers to integrate enterprise-grade search into their applications. Some of its features include the following:

| FEATURE | DESCRIPTION |
| --- | --- |
| AI and NLP | Uses AI and Natural Language Processing to search for data such as images and text |
| Search features | Provides semantic search, faceted navigation, fuzzy matching, and geospatial search features |
| Unstructured data | Can extract insights from unstructured data such as sentiment analysis, key phrase extraction, and entity recognition |

## Azure Form Recognizer

Azure Form Recognizer helps to extract entities such as key-value pairs, tables, and text from forms. It enables data entry to be faster and error-free as compared to manual data entry. It can be used on documents such as invoices, receipts, and custom documents.

## Azure Video Indexer

Azure Video Indexer is a cloud-based platform that extracts entities from audio and videos. Once you upload the content to a portal, it extracts information using speech-to-text, facial recognition, sentiment analysis, scene detection, and so on. Users can then search through this information, either through a portal or through an API.

Using Azure Video Indexer is easy; just go to [videoindexer.ai](videoindexer.ai) and upload a video after signing up. [Figure 9.15](Figure 9.15) shows the results for a video that I uploaded. It came up with a list of relevant topics, transcripts, keywords, named entities, and emotions.

![](img/1490b3cf638678afadc8c48abc1698d5_223_0.png)

### FIGURE 9.15: Using Azure Video Indexer tool

## Azure Machine Learning

Azure Machine Learning is a cloud-based machine learning platform. Developers can use it to build, train, and deploy machine learning models into production. It allows developers to prepare data, build and train models, validate, deploy, manage, and monitor the results.

| PHASE | FEATURE |
|---|---|
| Data preparation | During data preparation, developers can label training data, manage label projects, use analytics to explore data, and access and share datasets. |
| Build and train models | Provides notebooks, automated machine learning capability, the ability to run experiments, accelerate training using a scalable compute engine, access to a secure compute instance, and access to open-source libraries such as Scikit-learn, PyTorch, TensorFlow, Keras, and more. |
| Validate and deploy models | Provides the ability to deploy model endpoints for real-time and batch inference, pipelines and CI/CD workflows, prebuilt instances for inference, model repository, and hybrid and multi-cloud deployment options. |
| Manage and monitor models | Provides the ability to track logs, analyze data and models, detect drift, maintain model accuracy, debug models, trace machine learning artifacts for compliance, and ensure continuous monitoring of security and cost control features, including quota management and automatic shutdown. |

## EXERCISE: BUILDING, DEPLOYING, AND MONITORING AN AI MODEL WITH AZURE SERVICES

This exercise is to give your team practical experience with building, training, and deploying a machine learning model using Azure Machine Learning. It includes important aspects such as data preparation, model training, validation, deployment, and monitoring.

Remember to clean up resources at the end of the exercise to avoid unnecessary charges. Also note that the roles in the exercise can vary in your organization.

| STEP NAME | TASK OWNER | OBJECTIVE INSTRUCTION | DELIVERABLE | |
|---|---|---|---|---|
| Data preparation | Data engineer | Prepare data for model training | Import a dataset and use Azure's data preparation tools to preprocess the data. | A cleaned and preprocessed dataset ready for model training |
| Model building and training | Data scientist/ML engineer | Build and train a machine learning model | Choose a suitable ML algorithm and use it to train a model on the prepared dataset. Monitor the training process using Azure's tracking tools. | A trained machine learning model |
| Model validation | Data scientist/ML engineer | Evaluate the model's performance | Evaluate the model's performance using a holdout validation set and appropriate evaluation metrics. | Evaluation metrics and analysis |
| Model deployment | MLOps engineer/ML Engineer | Deploy the model for use | Deploy the model using Azure's deployment options for real-time or batch inference. | A deployed machine learning model |
| Monitoring | MLOps engineer | Monitor the model's performance over time | Use Azure's monitoring tools to track model usage, data drift, and retrain the model as necessary. | Regular performance reports and updated models as necessary |

## OTHER ENTERPRISE CLOUD AI PLATFORMS

This section covers several other enterprise cloud AI platforms that are worth knowing about and considering.

### Dataiku

Dataiku is an enterprise-class data science platform that allows data preparation, machine learning, and collaboration all in one place. It enables use cases such as customer segmentation, fraud detection, product recommendation, inventory management, and supply chain optimization.

Dataiku has key capabilities for explainable AI. It includes interactive reports for feature importance, partial dependence plots, subpopulation analysis, and individual prediction explanations.

### DataRobot

DataRobot's specific capabilities include AutoML, which automates the machine learning development and deployment lifecycle, and explainability, which explains how the models work and helps businesses build trust around their models. It facilitates collaboration by allowing users to share their work, including code, models, and workflows, in a collaboration platform. Its governance
