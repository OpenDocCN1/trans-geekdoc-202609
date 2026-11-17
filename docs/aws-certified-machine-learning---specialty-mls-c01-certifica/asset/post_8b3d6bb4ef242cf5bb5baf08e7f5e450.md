
likely that it won’t be able to create random batches of data with a good representation of both classes. Once the algorithm builds strong assumptions about the training data, it might be difficult for it to change them.

## IMPORTANT NOTE

Some algorithms are able to execute the training process by fitting the data in chunks, also known as batches. This approach lets the model learn more frequently since it will make partial assumptions after processing each batch of data (instead of making decisions only after processing the entire dataset).

On the other hand, there is no need to shuffle the testing set, since it will be used only by the inference process to check model performance.

## Modeling expectations

So far, you have learned about model building, validation, and management. You can now complete the foundations of ML by learning about a couple of other expectations while modeling.

The first one is parsimony. Parsimony describes models that offer the simplest explanation and fit the best results when compared with other models. Here’s an example: while creating a linear regression model, you realize that adding 10 more features will improve your model’s performance by 0.001%. In this scenario, you should consider whether this performance improvement is worth the cost of parsimony (since your model will become more complex). Sometimes it is worth it, but most of the time it is not. You need to be skeptical and think according to your business case.

Parsimony directly supports interpretability. The simpler your model is, the easier it is to explain it. However, there is a battle between interpretability and predictivity: if you focus on predictive power, you are likely to lose some interpretability. Again, you must select what is the best situation for your use case.

## Introducing ML frameworks

Being aware of some ML frameworks will put you in a much better position to pass the AWS Machine Learning Specialty exam. There is no need to master these frameworks since this is not a framework-specific certification; however, knowing some common terms and solutions will help you to understand the context of the problems/questions.

scikit-learn is probably the most popular ML framework that you should be aware of. It is an open source Python package that provides implementations of ML algorithms such as decision trees, support vector machines, linear regression, and many others. It also implements classes for data preprocessing, for example, one-hot encoding, label encoders, principal component analysis, and so on. All these preprocessing methods (and many others) will be covered in later sections of this book.

The downside of scikit-learn is the fact that it needs customization to scale up through multiple machines. There is another ML library that is very popular because of the fact that it can handle multiprocessing straight away: **Spark's ML library**.

As the name suggests, it is an ML library that runs on top of **Apache Spark**, which is a unified analytical multi-processing framework used to process data on multiple machines. AWS offers a specific service that allows developers to create Spark clusters with a few clicks, known as **EMR**. Additionally, SageMaker (a fully managed ML service provided by AWS, which you will cover in a separate chapter) is well integrated with Apache Spark.

The Spark ML library is in constant development. As of the time of writing, it offers support to many ML classes of algorithms, such as classification and regression, clustering, and collaborative filtering. It also offers support for basic statistics computation, such as correlations and some hypothesis tests, as well as many data transformations, such as one-hot encoding, principal component analysis, min-max scaling, and others.

Another very popular ML framework is known as **TensorFlow**. This ML framework was created by the Google team and it is used for numerical computation and large-scale ML model development. TensorFlow implements not only traditional ML algorithms but also DL models.

TensorFlow is considered a low-level API for model development, which means that it can be very complex to develop more sophisticated models, such as **transformers** (for text mining). As an attempt to facilitate model development, other ML frameworks were built on top of TensorFlow to make it easier. One of these high-level frameworks is **Keras**. With Keras, developers can create complex DL models with just a few lines of code. More recently, Keras was incorporated into TensorFlow and it can be now called inside the TensorFlow library.

**MXNet** is another open source DL library. Using MXNet, you can scale up neural network-based models using multiple GPUs running on multiple machines. It also supports different programming languages, such as Python, R, Scala, and Java.

**Graphics processing unit (GPU)** support is particularly important in DL libraries such as TensorFlow and MXNet. These libraries allow developers to create and deploy neural network-based models with multiple layers. The training process of neural networks relies a lot on matrix operations, which perform much better on GPUs rather than on CPUs. That's why these DL libraries commonly offer GPU support. AWS also offers EC2 instances with GPU enabled.

These ML frameworks need a special channel to communicate with GPU units. NVIDIA, the most common supplier of GPUs nowadays, has created an API called the Compute Unified Device Architecture (CUDA). CUDA is used to configure GPU units on NVIDIA devices; for example, setting up caching memory and the number of threads needed to train a neural network model. There is no need to master CUDA or GPU architecture for the AWS Machine Learning Specialty exam, but you definitely need to know what they are and how DL models take advantage of them.

Last, but not least, you should also be aware of some development frameworks widely used by the data science community, but not necessarily to create ML models. These frameworks interoperate with ML libraries to facilitate data manipulation and calculations. For example: pandas is a Python library that provides data processing capabilities and NumPy is an open source Python library that provides numerical computing.

These terms and libraries are so incorporated into data scientists’ daily routines that they might come up during the exam to explain some problem domain for you. Being aware of what they are will help you to quickly understand the context of the question.

## ML in the cloud

ML has gone to the cloud and developers can now use it as a service. AWS has implemented ML services at different levels of abstraction. ML application services, for example, aim to offer out-of-the-box solutions for specific problem domains. AWS Lex is a very clear example of an ML application as a service, where people can implement chatbots with minimum development.

AWS Rekognition is another example, which aims to identify objects, people, text, scenes, and activities in images and videos. AWS provides many other ML application services, which will be covered in the next chapter of this book.

Apart from application services, AWS also provides ML development platforms, such as SageMaker. Unlike out-of-the-box services such as AWS Lex and Rekognition, SageMaker is a development platform that will let you build, train, and deploy your own models with much more flexibility.

SageMaker speeds up the development and deployment process by automatically handling the necessary infrastructure for the training and inference pipelines of your models. Behind the scenes, SageMaker orchestrates other AWS services (such as EC2 instances, load balancers, auto-scaling, and so on) to create a scalable environment for ML projects. SageMaker is probably the most important service that you should master for the AWS Machine Learning Specialty exam, and it will be covered in detail in a separate section. For now, you should focus on understanding the different approaches that AWS uses to offer ML-related services.

The third option that AWS offers for deploying ML models is the most generic and flexible one: you can deploy ML models by combining different AWS services and managing them individually. This essentially does what SageMaker does for you, building your applications from scratch. For example, you could use EC2 instances, load balancers, auto-scaling, and an API gateway to create an inference pipeline for a particular model. If you prefer, you can also use AWS serverless architecture to deploy your solution, for example, using **AWS Lambda functions**.

## Summary

You are now heading toward the end of this chapter, in which you have learned about several important topics regarding the foundations of ML. You started the chapter with a theoretical discussion about AI, ML, and DL, and how this entire field has grown over the past few years due to the advent of big data platforms, cloud providers, and AI applications.

You then moved on to the differences between supervised, unsupervised, and reinforcement learning, highlighting some use cases related to each of them. This is likely to be a topic in the AWS Machine Learning Specialty exam.

You learned that an ML model is built in many different stages and the algorithm itself is just one part of the modeling process. You also learned about the expected behaviors of a good model.

You did a deep dive into data splitting, where you learned about different approaches to train and validate models, and you became aware of the mythic battle between variance and bias. You completed the chapter by getting a sense of ML frameworks and services.

Coming up next, you will learn about AWS application services for ML, such as Amazon Polly, Amazon Rekognition, Amazon Transcribe, and many other AI-related AWS services. But first, look at some sample questions to give you an idea of what you can expect in the exam.
