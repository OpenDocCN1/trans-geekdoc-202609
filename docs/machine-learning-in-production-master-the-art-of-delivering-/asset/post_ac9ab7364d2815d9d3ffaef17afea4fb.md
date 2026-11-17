
User behavior can be unpredictable. For instance, suppose a model requires a string value, but the user provides an alphanumeric value. In such scenarios, the model output might not be reliable.

## Security

ML systems are prone to security breaches. They may be forced to deliver false predictions by deliberately providing poisonous data or adding noise to the data. The models perform better when trained on new data. However, a person or a group of people can deliberately pass the poisonous data to the model, intending to change the model predictions.

Data security is at risk as the model keeps training on new data. While training the model, attackers can steal sensitive information.

## MLOps

MLOps combines machine learning processes and best practices of DevOps to deliver consistent output with automated pipelines and management. MLOps has been an emerging space in the industry for the last few years.

The following figure shows the increasing popularity of MLOps over time.

![](img/cc4299656808e62a294f1843a1e18e72_63_0.png)

Figure 3.2: The rise of MLOps. Source: Google trends

MLOps bridges the gap between machine learning experiments and model deployment in the production environment. Nowadays, many data scientists are forced to execute the MLOps processes manually.

The MLOps process involves multiple professionals, and data scientists play a critical role. Subject matter experts understand and collect the requirements from the client. Then, data engineers collect the data from multiple sources and execute the ETL jobs. Once this is done, data scientists build the models and the DevOps team builds the CI/CD pipeline and monitors it. Finally, feedback is sent to the data scientist or the concerned team for validation.

MLOps streamline and automate this process to speed up delivery and build efficient products / services.

MLOps is a combination of three disciplines as shown in the following figure

![](img/cc4299656808e62a294f1843a1e18e72_64_0.png)

*Figure 3.3: Machine learning operations*

MLOps is different from DevOps because the code is usually static in the latter, but that’s not the case in MLOps.

In MLOps, the model keeps training on new data, so a new model version gets generated recurrently. If it meets the requirements, it can be pushed into the production environment. This is why MLOps requires **Continuous Training** (CT) along with **Continuous Integration** (CI) and **Continuous Delivery/Deployment** (CD).

In DevOps, developers write the code as per the requirements and then release it to the production environment, but in the case of machine learning, developers first need to collect the data and clean it. They write code for model building and then build the ML model. Finally, they release it into the production environment.

## Benefits of MLOps

MLOps processes not only speed up the ML journey from experiments to production, but also reduce the number of errors. MLOps automates Machine Learning and Deep Learning model deployment in a production environment. Moreover, it reduces dependency on other teams by streamlining the processes.

## Efficient management of ML life cycle

MLOps takes care of the ML life cycle by following the fundamental principles of machine learning projects. It is based on agile methodology. An automated CI/CD pipeline helps speed up the process of retraining models on new data, testing before the deployment, monitoring, and feedback loops. The current stage depends on the output of the preceding stages, so there are fewer chances of issues in the deployment process.

If the amount of traffic or number of requests increase for a deployed model, it increases the required resources; similarly, the required resources decrease when the amount of traffic or number of requests reduces.

There are many platforms (like GitHub Actions) available in the market that help you set up MLOps workflow.

## Reproducibility

> Developer: It works on my machine.

> Manager: Then, we are going to ship your machine to the client.

- Reproducibility plays a crucial role in the ML life cycle. While transferring the code files to another machine or server, reproducibility reduces debugging time. MLOps works on **DRY (Don’t Repeat Yourself)** principles and allows you to get consistent output.

- Given the same input, the replicated workflow should produce an identical output. For this, developers use container orchestration tools like Docker so that it will create and set up the same environment with dependencies in another machine or server for consistent output.

## Automation

Mostly, developers deploy models several times before the final deployment to ensure that everything is in place and the output is as expected. Without automation, this would be a time-consuming and tedious process. Automation increases productivity, as you are less likely to test, deploy, scale, and monitor ML models manually.

At every stage, certain rules and conditions are implemented, and the model moves to the next stage only when these conditions are met. This reduces the active involvement of other teams every time you are planning to deploy it in production.

There is a low or no delayed deployment with testing since one inter-team dependency is reduced.

After making the required changes in the code, speedy deployment is done in an automated fashion (if it passes the test cases and satisfies the conditions). This increases the overall productivity of the team.

## Tracking and feedback loop

Tracking model performance, metrics, test results, and output becomes easy if you set up MLOps workflow properly. The model’s performance may degrade over time, hence one may need to retrain the model on new data.

Thanks to tracking and feedback loops, it sends alerts about the model’s performance, metrics, and so on.

For instance, if the feedback loop sends the information that model accuracy has dropped below 68%, then the model needs to be retrained. Again, it will check the model’s performance. If it is above the threshold level, it will pass on to the next stage; else, the model needs to be recalibrated using the latest data.

## Conclusion

In this chapter, you studied the key challenges faced while deploying ML models in production. At the beginning of this chapter, you learned how the ML life cycle works, and you understood its different stages and their challenges. Next, you got exposure to different types of model serving techniques and looked at their pros and cons. Then, you analyzed the challenges you may face while deploying ML models in production. Finally, you learned the benefits of MLOps.

In the next chapter, you will learn to develop, build and install custom python packages for ML models using a use case.

## Points to remember

- MLOps bridges the gap between the Machine Learning experiments stage and its model deployment in the production environment.
- Model deployment strategy depends on business requirements, users, and applications.
- MLOps combines machine learning processes and best practices of DevOps to deliver consistent output with automated pipelines and management.

## Multiple choice questions

- 1. What are the different ways of collecting data for an ML problem?
- a) E-surveys
- b) Web scraping
- c) Click data
- d) All the above

- 2. If you provide a similar input as the original workflow to the replicated workflow, it should produce an identical output known as:
- a) Portability
- b) Reproducibility
- c) Scalability
- d) Label encoding

## Answers

- 1. d
- 2. b

## Questions

- 1. What are the different ways of deploying ML models?
- 2. How do MLOps differ from DevOps?
- 3. What are the challenges faced while deploying ML models?
- 4. What are the benefits of MLOps?

## Key terms

- **Container**: A container is a standard unit of software that packages up the code and all its dependencies so that the application runs quickly and reliably despite the computing environment.
- **Continuous Integration (CI)**: It is an automated process to build, test, and execute different pieces of code.
- **Continuous Delivery/Deployment (CD)**: It is an automated process of frequently building tested code and deploying it to production.
