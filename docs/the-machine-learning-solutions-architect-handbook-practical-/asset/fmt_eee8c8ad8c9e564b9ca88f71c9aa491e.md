
The primary SageMaker user interface for data scientists is SageMaker Studio, a data science `integrated development environment` (`IDE`). It provides core features such as hosted notebooks for running experiments, as well as access to different backend services such as data wrangling, model training, and model hosting services from a single user interface. It is the main interface for data scientists to interact with most of SageMaker’s functionality. It also provides a Python SDK for interacting with its backend services programmatically from Python notebooks or scripts. The following diagram shows the key components of SageMaker Studio:

![](OEBPS/Images/B20836_08_03.png)

Figure 8.3: SageMaker Studio architecture

SageMaker Studio implements the concept of domains to segregate user environments. A domain represents a collection of user profiles, each equipped with specific configurations, such as the AWS IAM role used when running Jupyter notebook, tags, and access permission to SageMaker Canvas. Within each domain, a Studio user can access different Studio applications such as JupyterLab, Code Editor, or Canvas through a user profile. 

To run certain Studio applications such as JupyterLab and Code Editor, you need to create SageMaker Studio spaces. SageMaker Studio spaces are used to manage the storage and resource needs of these applications. Each space has a 1:1 relationship with an instance of an application, and is composed of resources such as a storage volume, application type, and image the application is based on. A space can be either private or shared.

To begin using SageMaker, the initial step is to onboard users into SageMaker Studio. The onboarding process starts by creating a SageMaker domain, if one doesn’t already exist. For the single-user scenario, SageMaker provides a quick domain setup option. With the quick setup option, SageMaker automatically configures the new domain with default settings for fast setup. For advanced multi-user scenarios, SageMaker provides an advanced domain setup option. With the advanced setting, you can configure various aspects of the domain for enterprise adoption, such as the authentication method, access to different services, networking configuration, and data encryption keys. Following that, user profiles are created within the domain, and users are granted access to these profiles. Once the user profiles are set up, users can launch a Studio environment by selecting their respective user profile in a domain. This allows them to start working within SageMaker Studio.

## Launching Studio applications

There are multiple applications available inside Studio, including JupyterLab, RStudio, Canvas, and Code Editor. You also have the option to launch the previous Studio Classic experience.

In the SageMaker Studio environment, initiating a Jupyter notebook is a straightforward process. Begin by selecting the JupyterLab application, followed by the creation of a JupyterLab space. A space, serving as a named, self-contained, and durable storage container, can be attached to the JupyterLab application. During the space creation, you have the flexibility to choose the server instance type and the Docker image for your JupyterLab. Once the space is successfully created, you can proceed to launch the JupyterLab application and initiate a notebook within it. The JupyterLab notebook now has an AI-powered programming assistant (Jupyternaut) feature that you can use to ask programming questions. For example, you can ask questions such as “How do I import a Python library?” or “How do I train a model using SageMaker?”.

Similarly, launching the Canvas application involves selecting it within the SageMaker Studio environment. As a no-code ML tool, Canvas provides features for data preparation, model training, inference, and workflow automation. While primarily designed for data analysts with a limited background in data science and ML, it also proves to be valuable for experienced data scientists aiming to quickly establish baseline models for diverse datasets. Users can leverage Canvas’s ready-to-use models for predictions without model building or choose to create custom models tailored to specific business problems. Ready-to-use models cover various use cases like language detection and document analysis. For custom models, Canvas supports building diverse model types using tabular and image data for personalized predictions. 

Importing data, whether from local or external sources such as S3, Amazon Redshift, or Databricks, is supported. Additionally, Canvas facilitates data preparation through Data Wrangler and offers generative AI foundation models for initiating conversational chats.

The Code Editor, built on Code-OSS and Visual Studio Code Open Source, facilitates writing, testing, debugging, and running analytics and ML code. To launch the Code Editor, simply select the application within Studio and create a dedicated private space. This space operates on a single `Amazon Elastic Compute Cloud` (`Amazon EC2`) instance for computing and a corresponding `Amazon Elastic Block Store` (`Amazon EBS`) volume for storage. All elements within the space, including code, Git profiles, and environment variables, are stored on this unified Amazon EBS volume.

## Preparing data

Preparing and processing data for model training is an essential step in the ML lifecycle to optimize model performance. To do this in the Studio environment, you can install and use your preferred library packages directly inside your Studio notebook. SageMaker also provides several data wrangling and processing services to assist with data preparation, including SageMaker Data Wrangler, and integrated data preparation with Amazon EMR and Glue for large-scale data preparation and processing.

## Preparing data interactively with SageMaker Data Wrangler

SageMaker Data Wrangler is a fully managed service that helps data scientists and engineers prepare and analyze their data for ML. With a graphical user interface, it facilitates data preparation tasks, such as data cleaning, feature engineering, feature selection, and visualization.

To use Data Wrangler, you construct a data flow, a pipeline that connects the dataset, transformation, and analysis. When you create and run a data flow, Data Wrangler spins up an EC2 instance to run the transformation and analysis. Each data flow is associated with an EC2 instance. A data flow normally starts with a data import step. Data Wrangler allows you to import data from multiple data sources, including Amazon S3, Athena, Amazon Redshift, Amazon EMR, Databricks, Snowflake, as well as `Software-as-a-Service` (`SaaS`) platforms such as Datadog, GitHub, and Stripe.

After the data is imported, you can use Data Wrangler to clean and explore the data and perform feature engineering with a built-in transform. You can also use the preconfigured visualization templates to understand data and detect outliers. 

You can assess the data quality with built-in reports. The following diagram shows the flow and architecture of Data Wrangler:

![](OEBPS/Images/B20836_08_04.png)

Figure 8.4: SageMaker Data Wrangler architecture

When utilizing Data Wrangler, the first step involves importing sample data from various data sources to perform data processing and transformations. After completing the necessary transformation steps, you have the option to export a recipe. This recipe can then be executed by SageMaker Processing, which processes the entire dataset based on the defined transformations.

Additionally, you have the option to export the transformation steps into a notebook file. This notebook file can be used to initiate a SageMaker Processing job, allowing for the data to be processed and transformed. The resulting output can be either directed to SageMaker Feature Store or stored in Amazon S3 for further usage and analysis.

## Preparing data at scale interactively
