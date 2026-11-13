Imagine this; if there is no need for coding and specialized equipment, then ML becomes a bit more accessible to various users and industries.5 From this end, the user is expected to become familiar with the platform of their choice and general ideas behind ML as opposed to learning ML via learning how to code. The latter is indeed one of the biggest hurdles to embracing ML in a variety of engineering industries.

In the coding-free approach, a civil or environmental engineer can access an online portal with an intuitive graphical interface.6 It is through this interface that the engineer can upload their data, select the type of analysis they envision to carry out, select one or a series of ML algorithms, run the ML analysis, and examine the outcome of this analysis.7 In some instances, the engineer could deploy their final model to use it outside of the platform. The engineer could seamlessly share and collaborate with others on projects.

I will be covering five platforms in this chapter. My reasoning for selecting these five stems from the positive experiences I gained while using such platforms, as well as the fact that these platforms offer free access and academic support to students and faculty. These platforms are BigML, DataRobot, Dataiku, Exploratory, and Clarifai.8

# 6.1.1 BigML

According to BigML,9

> BigML is a consumable, programmable, and scalable Machine Learning platform that makes it easy to solve and automate Classification, Regression, Time Series Forecasting, Cluster Analysis, Anomaly Detection, Association Discovery, and Topic Modeling tasks.

BigML was founded in 201110 with the mission of making ML easy and beautiful for everyone [1]. Of all the presented platforms in this textbook, BigML could arguably be the most general in applications. BigML also has a strong academic program that supports ML education and research and allows students to freely access and practice its platform. A unique feature of BigML is that it allows its users to download the completed ML models in scripts11 (i.e., once a user completes building a model, the same user can download their model’s code in a programming language of their choice to share with other users, etc.). BigML also supports explainable ML.12 A screenshot of BigML’s homepage is shown in Figure 6.1. We will use this platform to cover four examples,13 as you will see below. Please feel free to follow my steps.

# Example no. 1 [BigML, Classification]: Categorizing failure mode in FRP-strengthened RC beams.

In this example, we have a dataset14 that homes the outcome of over 100 experimental tests on RC beams strengthened with FRP15 composites. This dataset includes compressive strength of concrete fc, yield strength of steel reinforcement fy, the ratio of steel reinforcement rs, FRP ratio rf, modulus of FRP Efr, moment arm a, and strengthening type t.16 The target in this dataset is the failure mode17 (FM) observed in each test (i.e., steel yielding/concrete crushing or failure through the FRP system). Let us use the BigML platform to carry out this example.