
![](img/7ae4bd70c4b8a91a2f0a81163d918a5f_6_0.png)

## Data acquisition & preparation

To build high quality models, data scientists and machine learning engineers must have access to large quantities of high-quality labeled training data. This data very rarely exists in a single place or in a form directly usable by data scientists. Rather, in the vast majority of cases, the training dataset must be built by data scientists, data engineers, machine learning engineers, and business domain experts working together.

In the real world, as opposed to in academia or Kaggle competitions, the creation of training datasets usually involves combining data from multiple sources. For example, a data scientist building a product recommendation model might build the training dataset by joining data from web activity logs, search history, mobile interactions, product catalogs, and transactional systems.

> While the specific use of labeled training datasets is characteristic of supervised learning, as opposed to unsupervised, self-supervised or reinforcement learning, the former remains the most popular type of machine learning in use today. While this book occasionally refers to labels and other supervised learning concepts, its key messages apply broadly.

Once compiled, training data must then be prepared for model development. To do this, data scientists will apply a series of transformations to the raw data to cleanse and normalize it. Examples include removing corrupt records, filling in missing values, and correcting inconsistencies like differing representations for states or countries.

Transformations may also be required to extract labels. For example, developing a model that predicts the likelihood of churn among customers will require a label indicating which of the customers in our transactional database are examples of churn. This can, in turn, require a complex query against the data warehouse that considers factors such as the products or services that we are basing the prediction on, the number of days without a transaction, the window in which we want to make predictions, and more.³

As a result of the organizational and technical complexity involved, the process of acquiring and preparing enterprise data can consume the vast majority of a data scientist's effort on a given project—50 to 80 percent, according to some reports.4

If not accounted for during planning or supported by appropriate processes and tools, data acquisition can consume all of the time and resources allocated for a project, leaving little available for the remaining steps in the machine learning process.

## Experiment management and model development

Experimentation is central to the machine learning process. During modeling, data scientists and machine learning engineers (MLEs) run a series of experiments to identify a robust predictive model. Typically, many models—possibly hundreds or even thousands—will be trained and evaluated in order to identify the techniques, architectures, learning algorithms, and parameters that work best for a particular problem.

Feature engineering is the iterative process of creating the features and labels needed to train the model through a series of data transformations. Feature engineering is often performed in lockstep with model training, because the ability to identify helpful features can have a significant impact on the overall success of the modeling effort. That said, a fine line separates the preliminary data cleansing and normalization steps associated with data preparation from feature engineering.

Simple examples of feature engineering include generating derived features (such as calculating an age from a birthdate) or converting categorical variables (such as transaction types) into one-hot encoded, or binary, vectors.

With deep learning, features are usually straightforward because deep neural networks (DNNs) generate their own internal transformations. With traditional machine learning, feature engineering can be quite challenging and relies heavily on the creativity and experience of the data scientist and their understanding of the business domain or ability to effectively collaborate with domain experts.

In addition, a variety of tools under the broad banner of “AutoML” are finding popular use to automate aspects of experimentation and model development. Offerings exist to automate feature engineering by creating and testing a wide variety of candidate features, identify the best machine learning or deep learning models (the latter referred to as neural architecture search), automatically tune or optimize model hyperparameters, and automate the compression of large DNNs so that they’re more amenable to mobile or edge deployment.

Whether manually performed or automated, the various aspects of experimentation and model training can be quite computationally intensive, especially in the case of deep learning. Having ready access to the right infrastructure for each experiment, such as CPUs, GPUs, memory, etc.—whether locally or in the cloud—can significantly impact the speed and agility of the data science team during the model development phase of the process.

## Model deployment

Once a model has been developed, it must be deployed in order to be used. While deployed models can take many forms, typically the model is embedded directly into application code or put behind an API of some sort. HTTP-based (i.e. REST or gRPC) APIs are increasingly used so that developers can access model predictions as microservices.

While model training might require large bursts of computing hardware over the course of several hours, days or weeks, model inference—making queries against models—can be even more computationally expensive than training over time. Each inference against a deployed model requires a small but significant amount of computing power. Unlike the demands of training, the computational burden of inference scales with the number of inferences made and continues for as long as the model is in production.

> Or not so small in the case of some deep learning models. Google's efforts to build its Tensor Processing Unit (TPU), a specialized chip for inference, began in 2013 when engineer Jeff Dean projected that if people were to use voice search for 3 minutes a day, meeting the inference demands of speech recognition would require Google data centers to double in capacity.

Meeting the requirements of inference at scale is a classic systems engineering problem. Addressing issues like scalability, availability, latency, and cost are typically primary concerns. When mobile or edge deployment is required, additional considerations like processing cycles, memory, size, weight, and power consumption come into play.

At a certain point, we often end up needing to turn to distributed systems to meet our scalability or performance goals. This of course brings along its own set of challenges and operational considerations. How do we get our model onto multiple machines and ensure consistency over time. How do we update to new models without taking our applications out of service? What happens when problems arise during an upgrade? How can we test new models on live traffic?

Fortunately for those deploying models, much progress has been made addressing these questions for microservices and other software systems.

## Model monitoring

Once a model is put into production, it is important to monitor its ongoing performance. Machine learning models are perishable, meaning that the statistical distribution of the data a model sees in production will inevitably start to drift away from that seen during training. This will cause model performance to degrade, which can result in negative business outcomes such as lost sales or undetected fraudulent activity if not detected and addressed.

Production models should be instrumented so that the inputs to and results of each inference are logged, allowing usage to be reviewed and performance to be monitored on an ongoing basis. Owners of models experiencing degraded performance can use this information to take corrective action, such as retraining or re-tuning the model.

Business or regulatory requirements may impose additional requirements dictating the form or function of model monitoring for audit or compliance purposes, including in some cases the ability to explain model decisions.

Model monitoring is generally a concern shared by all of an organization’s production models, and thus ideally supported by a common framework or platform. This has the advantage of making monitoring “free” for data scientists, that is, something they get the benefit of but don’t need to worry about building. While some models or applications may have unique monitoring or reporting requirements requiring the involvement of data scientists or ML engineering staff, they should ideally be able to take advantage of low level “plumbing” that is already in place.

## Machine Learning at Scale

When an enterprise is just getting started with machine learning, it has few established ML practices or processes. During this period, its data scientists are typically working in an ad hoc manner to meet the immediate needs of their projects. Data acquisition and preparation, as well as model training, deployment, and evaluation, are all done hand crafted with little automation or integration between steps.

Once a team has operated this way for more than a handful of projects, it becomes clear that a great deal of effort is spent on repetitive tasks, or worse, on reinventing the wheel. For example, they may find themselves repeatedly copying the same data, performing the same data transformations, engineering the same features, or following the same deployment steps.

Left to their own devices, individual data scientists or MLEs will build scripts or tools to help automate some of the more tedious aspects of the ML process. This can be an effective stopgap, but left unplanned and uncoordinated, these efforts can be a source of distraction and lead to technical debt.

For organizations at a certain level of scale—typically when multiple machine learning teams and their projects must be supported simultaneously—“data science platform” or “ML infrastructure” teams are established to drive efficiency and ensure that data scientists and MLEs have access to the tools and resources they need to work efficiently.
