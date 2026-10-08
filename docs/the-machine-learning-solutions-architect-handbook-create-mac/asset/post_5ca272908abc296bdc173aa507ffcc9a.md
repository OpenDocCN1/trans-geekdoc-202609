
A very popular example of reinforcement learning is the AlphaGo computer program, which uses mainly reinforcement learning to learn how to play the game of Go. Figure 1.4 shows the flow of reinforcement learning where an agent (for example, the player of a space invader game) takes actions (for example, moving the left/right control) in the environment (for example, the current state of the game) and receives rewards or penalties (score increase/decrease). As a result, the agent will adjust its moves to maximize the rewards in the future states of the environment. This cycle continues for a very large number of rounds, and the agent will improve and become better over time:

![](img/bd21298357d8484151447cff0b2f138b_27_0.png)

Figure 1.4 – Reinforcement learning

There are many practical use cases for reinforcement learning in the real world. The following are some examples for reinforcement learning:

- Robots or self-driving cars learn how to walk or navigate in unknown environments by trying out different moves and responding to the received results.
- A recommendation engine optimizes product recommendations with adjustments based on the feedback of the customers to different product recommendations.
- A truck delivery company optimizes the delivery route of its fleet to determine the delivery sequence required to achieve the best rewards, such as the lowest cost or shortest time.

## ML versus traditional software

Before I started working in the field of AI/ML, I spent many years building software platforms for large financial services institutions. Some of the business problems I worked on had complex rules, such as identifying companies for comparable analysis for investment banking deals, or creating a master database for all the different companies' identifiers from the different data providers. We had to implement hardcoded rules in database stored procedures and application server backends to solve these problems. We often debated if certain rules made sense or not for the business problems we tried to solve. As we changed them, we had to reimplement the rules and make sure the changes did not break anything. To test for new releases or changes, we often relied on human experts to exhaustively test and validate all the business logic implemented before the production release. It was a very time-consuming and error-prone process and required a significant amount of engineering, testing against the documented specification, and rigorous change management for deployment every time new rules were introduced, or existing rules needed to be changed. We often relied on users to report logic issues in production, and when an issue was reported in production, we sometimes had to open up the source code to troubleshoot or explain logic of how it worked. I often asked myself if there were better ways to do this.

After I started working in the field of AI/ML, I started to solve many similar challenges using ML techniques. With ML, I did not need to come up with complex rules that often require deep data and domain expertise to create or maintain the complex rules for decision making. Instead, I focused on collecting high-quality data and used ML algorithms to learn the rules and patterns from the data directly. This new approach eliminated many of the challenging aspects of creating new rules (for example, a deep domain expertise required, or avoiding human bias) and maintaining existing performance metrics. To validate the model before the production release, we could examine model performance metrics as accuracy. While it still required data science expertise to interpret the model metrics against the nature of the business problems and dataset, it did not require exhaustive manual testing of all the scenarios. When a model was deployed into production, we would monitor if the model performed as expected by monitoring any significant changes in production data versus the data we have for model training. We would collect new labels for production data and test the model periodically ensure its predictive power had degraded. To explain why a model made a decision the way it did, we did not need to open up source code to re-examine the hardcoded logic. Instead, we relied on ML techniques to help explain the relative importance of input features to understand what factors were most influential in the decision-making by the ML models.

The following figure (Figure 1.5) shows a graphical view of the process differences between developing a piece of software and training an ML model:

![](img/bd21298357d8484151447cff0b2f138b_29_0.png)

Figure 1.5 – ML and computer software

Now that you know the difference between ML and traditional software, it is time to dive deep into understanding the different stages in an ML life cycle.

## ML life cycle

One of the first ML projects that I worked on was a sport predictive analytics problem for a major sports league brand. I was given a list of predictive analytics outcomes to think about to see if there were ML solutions for the problems. I was a casual viewer of the sports; I didn't know anything about the analytics to be generated, nor the rules of the games in detail. I was given some sample data, but I had no idea what to do with it.

The first thing I started to work on was to learn the sport. I studied things like how the games were played, the different player positions, and how to determine and identify certain events. After acquiring the relevant domain knowledge did the data start make sense to me. I then discussed the impact of the different analytics outcomes with the stakeholders and assessed the modeling feasibility based on the data we had. We came up with a couple of top ML analytics with the most business impact to work on, decided how they would be integrated into the existing business workflow, and how they would be measured on their impacts.

I started to inspect and explore the data in detail to understand what information was available and what was missing. I processed and prepared the dataset based on a couple of ML algorithms I was thinking about and carried out different experiments. I did not have a tool to track the experiments. After some initial rounds, I felt the data was not enough to train a high-performance model, and I needed more datasets. The data owner was able to provide additional datasets I looked for, and after more experiments I built a model that met the business needs. After that, the hard part came - to deploy and operationalize the model in production and integrate it into the existing business workflow. We went through many architecture and engineering discussions and eventually built out a deployment for the model.

As you can see from my personal experience, there are many different steps in taking a business idea or expected outcome from ideation to production. Now, let's formally review a typical life cycle of an ML project. A formal life cycle includes steps as business understanding, data acquisition and understanding, data preparation, model building, model evaluation, and model deployment. Since a big component of the life cycle is experimentation with different datasets, features, and algorithms, a working model can be created at the end of the process. Factors such as the availability and quality of data, feature engineering techniques (the process of using domain knowledge to extract useful features from raw data), and the capability of the learning algorithms, among others, can all prevent a successful outcome.

The following figure shows the key steps in ML projects:

![](img/bd21298357d8484151447cff0b2f138b_31_0.png)

Figure 1.6 – ML life cycle

In the next few sections, we will discuss each of these steps in greater detail.

## Business understanding and ML problem framing

The first step in the life cycle is the business understanding step. In this step, you need to develop a clear understanding of the business goals and define the business performance metrics that can be used to measure the success of the ML project. The following are some examples of business goals:

- Cost reduction for operational processes, such as document processing.
- Mitigation of business or operational risks, such as fraud and compliance.
- Product or service revenue improvements, such as better target marketing, new insight generation for better decision making, and increased customer satisfaction

Specific examples of business metrics for measurement could be the number of hours reduced in a business process, an increased number of true positive instances detected, a conversion rate improvement from target marketing, and the extent of churn rate reductions. This is a very important step to get right to ensure there is sufficient justification for an ML project and that the outcome of the project can be successfully measured.
