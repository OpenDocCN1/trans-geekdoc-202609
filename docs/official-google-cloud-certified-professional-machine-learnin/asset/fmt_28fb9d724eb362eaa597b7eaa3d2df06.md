
# 8. Data Integration Service Selection

You are a data engineer for a finance company. You are responsible for building a unified analytics environment across a variety of on‐premises data marts. Your company is experiencing data quality and security challenges when integrating data across the servers, caused by the use of a wide range of disconnected tools and temporary solutions. You need a fully managed, cloud‐native data integration service that will lower the total cost of work and reduce repetitive work. Some members on your team prefer a codeless interface for building an extract, transform, load (ETL) process. Which service should you use?

1.  **Cloud Data Fusion**
2.  Dataprep
3.  Cloud Dataflow
4.  Apache Flink

# 9. Model Validation Strategy

You work for a global footwear retailer and need to predict when an item will be out of stock based on historical inventory data. Customer behavior is highly dynamic since footwear demand is influenced by many different factors. You want to serve models that are trained on all available data but track your performance on specific subsets of data before pushing to production. What is the most streamlined, scalable, and reliable way to perform this validation?

1.  Use the `tf.Transform` to specify performance metrics for production readiness of the data.
2.  Use the entire dataset and treat the area under the receiver operating characteristic curve (AUC ROC) as the main metric.
3.  Use the last relevant week of data as a validation set to ensure that your model is performing accurately on current data.
4.  Use k‐fold cross‐validation as a validation strategy to ensure that your model is ready for production.

# 10. Improving Production Model Accuracy

You are transforming a complete dataset before model training. Your model accuracy is 99 percent in training, but in production its accuracy is 66 percent. What is a possible way to improve the model in production?

1.  Apply transformation during model training.
2.  Perform data normalization.
3.  Remove missing values.
4.  **Use `tf.Transform` for creating production pipelines for both training and serving.**

# Chapter 4: Choosing the Right ML Infrastructure

In this chapter, we will discuss the hardware requirements for training on different types of data and for the various different scenarios of deployment. The hardware requirements depend on the type of machine learning (ML) algorithm you choose, the training method (custom, AutoML, or pretrained), and the data type as well.

Generally, ML models for video and images require a large number of computations for each loop of training, including matrix multiplications, additions, subtractions, and differentials. These operations are performed on very large matrices, which sometimes could be several megabytes for each data point. When you have millions of data points, it becomes a problem for traditional general‐purpose CPUs. So, GPUs (which were originally used in rendering videos or in gaming consoles) were repurposed to train ML models. Later Google created custom ASICs called Tensor Processing Units (TPUs), which perform even better. These techniques were originally applied to video and images and then were applied to natural language processing tasks. They greatly improved the performance of translations, text classifications, and in‐general text‐to‐text problems (where both the input and output of a model is text).

Let's explore the available hardware options for training and deploying models.

## Pretrained vs. AutoML vs. Custom Models

When you have an ML problem to solve, say image classification, you have three ways to deal with approaching it:

*   Pretrained
*   AutoML
*   Custom

[Figure 4.1](#c04.xhtml#c04-fig-0001) shows the differences between the models, and we'll elaborate on each in this chapter.

The first method is to use any pretrained models that might be available and ready to use. These are models that have already been trained on large datasets by Google. These pretrained models are already deployed and can be readily used via APIs. Google manages the deployment of these models; therefore, as a user, you only think about the number of times you call the APIs.

![FIGURE 4.1 Pretrained, AutoML, and custom models](images/c04f001.png)

**FIGURE 4.1** Pretrained, AutoML, and custom models

The biggest advantage of using pretrained models is the ease of use and the speed with which you can incorporate ML into your application. In this case, you do not have to think about the algorithm, the training method, the training hardware, the deployment hardware, scalability, and so on.

A pretrained model should be your first choice. Carefully consider a pretrained model and evaluate if it fits your use case. You can start by using a pretrained model in your application, and then if you think you need a better model, you can move to an AutoML or custom model.

Pretrained models are used by thousands of users, and with millions of requests coming in, they are maintained by a team of engineers. Of all the users looking to use ML in their application, a majority will choose pretrained models. [Figure 4.1](#c04.xhtml#c04-fig-0001) shows these models as a pyramid. You will notice that the bottom layer, which is wide, represents the number of users who use pretrained models.

You do not even have to be an ML engineer to use pretrained models. Any developer can make use of pretrained models using APIs. They can be used with ease using the Python, Java, and Node.js SDKs. We provide a detailed list of pretrained models that are available later in this chapter.

When using the pretrained models, you are not provisioning any cloud resources, and you are consuming only through an API. This is called a *serverless* method, and you will be charged based on the number of times you make a request to the API. Some of the APIs have a free tier. This is one of the reasons the pretrained models using APIs are so popular.

Now, while the pretrained models work well for a majority of users, sometimes they may not work for you. It is the most convenient option, but it is also the least customizable. Say you used the Vision API to classify plants but now you want to identify the exact subspecies of a plant. While the Vision API can provide thousands of labels, it might not have names for subspecies of plants. In this case, you may consider the next option: AutoML.

Vertex AI AutoML is a method by which you can build your own model using your own data. There are some popular machine learning problems that have been researched for decades and understood very well. These problems—such as image classification and text translation, for example—have been used many times in the past and all the nuances and variations have been identified. AutoML chooses the best ML algorithm, and the only thing that it needs is the data. Like a "just add water" cake mix, AutoML can be considered "just add data." You then have to format the data and work on quality control.

Unlike with pretrained models, you have to provision cloud resources for training and deploying the model on instances. At the time of training, you have to decide on the number of hours of instance time that you have to provision, and during deployment, you will decide on whether the model is deployed in the cloud, on field devices like Android phones, or in other IoT devices. We will look at the hardware provisioning options later in this chapter.

AutoML is the second level in the pyramid shown in [Figure 4.1](#c04.xhtml#c04-fig-0001), where users who want to train models with their own data usually go. AutoML provides you with the ability to build your own models and at the same time does not require a team of ML experts to build them.
