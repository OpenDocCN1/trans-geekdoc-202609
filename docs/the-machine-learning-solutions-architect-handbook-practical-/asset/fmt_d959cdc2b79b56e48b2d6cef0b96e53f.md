
With these functional requirements in mind, the following architecture diagram illustrates an e-commerce architecture that uses Amazon Personalize as the recommendation engine:

![](OEBPS/Images/B20836_11_03.png)

Figure 11.3: E-commerce site and recommendation architecture

In this architecture, we use Personalize as the recommendation engine to power both the online user experience as well as the target user marketing experience.

The RDS database, DynamoDB, and Elasticsearch are the main data sources for item, user, and interaction data. Glue ETL jobs are used to transform the source data into the datasets required for Personalize solution building.

Once a Personalize solution has been evaluated to meet the desired criteria, it is deployed as a Personalize campaign to serve recommendation requests from customers visiting the e-commerce website.

Amazon Pinpoint is a managed target marketing service. You can use Pinpoint to manage user segmentation and send email and SMS marketing campaigns. In this architecture, the Pinpoint service gets a list of recommended products for a group of target customers and sends out email or SMS campaigns to those users with personalized recommendations.

## Customer self-service automation with intelligent search

Good customer service boosts customer satisfaction and builds long-term customer loyalty. However, customer support is very labor-intensive and can result in poor customer satisfaction due to long waiting times and unknowledgeable support agents. The customer self-service capability has been widely adopted by organizations in different industries to deflect customer support call volumes and improve customer satisfaction.

In a customer self-service scenario, we can identify the following ML problems:

*   `Automatic speech recognition` (`ASR`): This ML task recognizes human speech and converts it into text, and then uses NLU to understand the meaning of the text.

*   `Natural language understanding` (`NLU`): NLU is a subfield of NLP, and it deals with intent understanding and reading comprehension. NLU focuses on the meaning and intent of the text. For example, if the text is `Can I get the cash balance in my savings account?`, then the intent here is `get account balance`. Another example of NLU is understanding the text and extracting specific information from it based on the semantic meaning of the question and the text.

*   `Text to speech`: This ML task converts text into natural human voices.

The following diagram shows a sample architecture for implementing a self-service chat functionality for customers to look up customer-related details, as well as general information and FAQs:

![](OEBPS/Images/B20836_11_04.png)

Figure 11.4: Self-service chat portal with an intelligent virtual assistant

In this architecture, an Amazon Lex bot is used to provide the text-based conversational interface for customer engagement. The customer uses the self-service chat portal to initiate the conversation and the chat portal integrates with the Lex bots via the Lex API.

Lex bots support several different intents, such as `look up account info`, `update customer profile`, and `How do I return a purchase?`.

Depending on the intent, the Lex bot will route the fulfillment requests to a different backend. For customer account-related inquiries, it will use a Lambda function for fulfillment. For information search-related questions, the Lex bot will send the query to a Kendra index for fulfillment.

Having explored the various AI services and their practical business applications, the subsequent sections will focus on operational considerations related to the adoption of these services. This includes delving into MLOps, code promotion, and monitoring processes to enhance the operational efficiency of AI implementations.

# Designing an MLOps architecture for AI services

Implementing custom AI service models requires a data engineering, model training, and model deployment pipeline. This process is similar to the process of building, training, and deploying models using an ML platform. As such, we can also adopt MLOps practice for AI services when running them at scale.

Fundamentally, MLOps for AI services intends to deliver similar benefits as MLOps for the ML platform, including process consistency, tooling reusability, reproducibility, delivery scalability, and auditability. Architecturally, we can implement a similar MLOps pattern for AI services.

## AWS account setup strategy for AI services and MLOps

To isolate the different environments, we can adopt a multi-account strategy for configuring the MLOps environment for AI services. The following diagram illustrates a design pattern for a multi-account AWS environment. Depending on your organizational requirements for separation of duties and control, you may also consider consolidating these into fewer environments:

![](OEBPS/Images/B20836_11_05.png)

Figure 11.5: MLOps architecture for AI services on AWS

In this multi-account AWS environment, developers use the custom model development environment to build and test the pipelines for data engineering, model training, and model deployment. When ready, the pipelines are promoted for formal model building and testing using production training data in the model development environment. Since trained AI services models cannot normally be exported, we will need to replicate the model training workflow in the production environment for model deployment.

The shared services environment hosts CI/CD tools such as AWS CodePipeline and AWS CodeBuild. You use the CI/CD tools to build different pipelines for data engineering, model building, and model deployment running in different environments. For example, a pipeline for the UAT environment could have the following components and steps:

*   `CodePipeline definition`: This definition would have a CodeBuild step, a CloudFormation execution step, and a Step Functions workflow execution step.

*   `CodeBuild step`: The CodeBuild step enriches the CloudFormation template with additional inputs needed to create a Step Functions workflow that orchestrates data engineering, dataset creation, data ingestion, model training, and model deployment.

*   `CloudFormation execution step`: This step executes the CloudFormation template to create the Step Functions workflow.

*   `Step Functions workflow execution step`: This step kicks off the Step Functions workflow to run the various steps, such as data engineering and model training, in the workflow. For example, if we build a Step Functions workflow for Personalize model training and deployment, the workflow will consist of six steps: create dataset group, create dataset, import dataset, create solution, create solution version, and create campaign.

In a multi-account environment, there could also be other purpose-built accounts for data management, monitoring, and security.

## Code promotion across environments

Similar to the pattern we use for the ML platform, we can use a code repository as the mechanism to promote code to different environments. For example, during code development, a developer creates code artifacts such as data engineering scripts for Glue ETL jobs and CloudFormation template skeletons and builds specification files for CodeBuild to run different commands. Once the code is deemed ready to promote them for formal model building and testing, the developer checks the code into a release branch in the code repository. The code check-in event can trigger a CodePipeline job to run the CodeBuild step in the shared services and then run a Step Functions workflow step in the model development environment. When it is ready for production release, a deployment CodePipeline job can be triggered in the shared services environment to execute a CloudFormation template to deploy the model in the production environment.

## Monitoring operational metrics for AI services
