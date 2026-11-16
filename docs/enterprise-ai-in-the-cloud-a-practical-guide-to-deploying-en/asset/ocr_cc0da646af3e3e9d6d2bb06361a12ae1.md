operations (Ops). It focuses on automating the end-to-end machine learning lifecycle, from data preparation to model training to deployment and monitoring. It enables faster, more reliable, and scalable ML implementations, which is the focus of this chapter. MLOps is similar to DevOps in software development, but it is specifically geared towards automating ML workflows.

![](bbox=[0.116, 0.213, 0.505, 0.502])

Setup Infrastructure and Manage Operations

* Setup Enterprise AI Cloud Platform Infrastructure
* Automate AI platform operations for scale and speed

Objective

Efficiently manage and scale your AI platform by integrating MLOps best practices for automation, model deployment, and tracking throughout the AI lifecycle

# FIGURE 14.1: SETUP INFRASTRUCTURE AND MANAGE OPERATIONS: Automate AI platform operations for scale and speed

MLOps is about continuous integration and continuous delivery (CI/CD) of not just models, but also of data. The goal of MLOps is to automate and scale the tasks of processing and engineering data. Your goal must be to ensure that you employ the best practices in this chapter so that when processing data in Chapter 15, as new data comes in, it’s processed and made available automatically for model training seamlessly.

In Chapters 16 and 17, you may try different algorithms and train and tune multiple models. Your goal must be to deploy the best practices in this chapter to ensure that each model version is tracked, stored, and can be rolled back or forward as needed. This also ties in with the concept of tagging and container image management, which will facilitate this process.

Once you have trained your models, they need to be evaluated. The practices outlined in this chapter and Chapter 19 can help automate this step. It ensures that as soon as the model is trained using the practices in Chapter 17, it’s automatically evaluated and metrics are logged.

Finally, I want to emphasize the importance of having feedback loops. By that I mean the evaluations and insights obtained from the training, tuning,