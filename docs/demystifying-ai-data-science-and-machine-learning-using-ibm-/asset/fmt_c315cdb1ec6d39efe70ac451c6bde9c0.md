
# 7. Differentiate between supervised learning and unsupervised learning? Provide examples of each type.

# 8. What are common machine learning methods for supervised learning and unsupervised learning?

# 9. What is ensemble modeling? In what situations should we use ensemble modeling?

# 10. How do you select the appropriate machine learning method for a data mining project?

# 11. Compare data mining software programs. Search the Internet to find the most current usage statistics for data mining software.

# Chapter Exercises

## Exercise 1: Add the Data File in SPSS Modeler and Identify the Target Variable

Follow the steps given below:

1.  Open `SPSS Modeler`.
2.  In the `File` menu, select `New Stream`.
3.  Go to `File/Save Stream As`.
4.  Select a location for your stream and name it `Airline_Explore`.
5.  From the `Sources` group in the `Node Pallet`, double-click the `Statistics File` node to add it to the stream.
6.  Double-click the `Statistics File` node to open the setting window for this node.
7.  Click the ellipsis button (three-dot button) and select the `AirlineRecommendation.sav` file from your computer.

    ![](images/ufig2_25.jpg)

8.  Click `Preview` to review the first ten rows of the data.

    ![](images/ufig2_26.jpg)

9.  Click `Apply` and `OK`.
10.  From the `Field Ops` group, add the `Type` node to the stream and connect it to the data node. We use this node to view and change the scales and roles of fields.
11.  Double-click the `Type` node to open the setting window.
12.  Check the measurement scales of all fields as below.
13.  For the field `recommendation`, change the role to `Target`.

     ![](images/ufig2_27.jpg)

14.  Click `Apply` and `OK`.

# 3 Data Sampling and Partitioning

DOI: [10.1201/9781003468196-4](https://doi.org/10.1201/9781003468196-4)

## Learning Outcomes

Upon the completion of this chapter, you will be able to:

1.  Define data sampling.
2.  Explain the importance of data sampling in data mining.
3.  Differentiate between population, sampling frame, and sample.
4.  Compare probability sampling and non-probability sampling.
5.  Identify sampling bias and understand its implications.
6.  Evaluate and select the appropriate sampling method for various data mining projects.
7.  Sample a subset of the full dataset using `SPSS Modeler`.
8.  Determine the appropriate sample size for a data mining project.
9.  Describe the challenges of an imbalanced dataset and overfitting.
10.  Evaluate various strategies to address the imbalanced dataset.
11.  Define oversampling and undersampling and understand their applications.
12.  Describe `SMOTE` technique and its strengths and weaknesses.
13.  Explain the importance of data partitioning in model validation.
14.  Determine the proper split ratio in data partitioning.
15.  Implement data partitioning using `SPSS Modeler`.

## Introduction

![](images/ufig3_1.jpg)

In this chapter, we discuss the data sampling process, a crucial step in selecting a subset of the full dataset for analysis. Proper sampling is essential to minimize sampling bias. As mentioned earlier, the quality of the model depends heavily on the quality of the data. Therefore, it is vital to use high-quality data to develop an effective predictive model.

We also explore data partitioning, which involves splitting the dataset into several sub-samples. The training sample is used to train the model, the validation sample is used to validate it, and the test sample is employed for the final testing before the model is used for actual predictions.

This chapter introduces key concepts and terminology in data sampling, which are necessary to understand various sampling methods. It is important to differentiate between the population, sampling frame, and sample. Our goal in sampling is to ensure that the sample accurately represents the population. Since our predictive model is trained using the training sample, we must ensure that the model is generalizable to other datasets. In other words, the model should be capable of making accurate predictions with any new dataset, thereby demonstrating its usability.

## Sampling the Data

![](images/ufig3_2.jpg)

Sampling is essentially the process of selecting a subset of the entire dataset (sample) for analysis purposes. The goal of sampling is to gather representative and reliable information from a population, especially when it is impractical or impossible to collect data from every individual or element within that population. Sampling is a crucial step in any research project to ensure that the data are sufficient and representative. Proper sampling allows us to create a quality dataset that is adequately sized and representative of the target population, enabling us to produce a valid and generalizable model.

To better understand the sampling process and how to sample data effectively, I will describe the concepts of population, sampling frame, sampling strategy, and sample size from the perspective of data mining. These concepts are deeply discussed in research methodology books that focus on survey, experiment, and interview designs, which are common methods for collecting primary data. However, in data mining studies, we apply these concepts slightly differently because we work with secondary data—data that has been collected prior to the project. Typically, such data are collected by marketing companies, industrial organizations, or governmental agencies. Given that these databases are often very large, it is not practical to analyze the full dataset. Therefore, it is essential to have a strategy to correctly sample a subset of the large dataset for analysis.

[Figure 3.1](#chapter3.xhtml#fig3_1) illustrates the differences between the population, sampling frame, and sample. We will discuss the details of these concepts, their interrelationships, and the various sampling methods available.

![FIGURE 3.1 Population, sampling frame, and sample. Return to text.⏎](images/fig3_1.jpg)

FIGURE 3.1 Population, sampling frame, and sample. [Return to text.⏎](#chapter3.xhtml#b3fig3_1)

### Population

![](images/ufig3_3.jpg)

"Population" refers to the primary target audience from which we want to examine data patterns and draw conclusions. The population in our study could consist of individuals, objects, cases, or specific industry sectors. The target population should be large enough to ensure the significance of our findings, yet focused enough to maintain the feasibility of the study.

For example, consider a project aimed at predicting passengers' airline recommendations. In this case, U.S. airline passengers represent an appropriate target population, covering U.S. residents who use air transportation for travel. Targeting worldwide residents would make data collection challenging due to the vastness of the population. Moreover, when focusing on residents of all countries, confounding variables—such as cultural, political, educational, or economic factors specific to each country—could affect the target variables. The absence of data on these variables could compromise the validity of our findings. By narrowing the focus to the U.S. market, we can more readily access data and draw valid conclusions about U.S. air travelers' decisions. We may choose to include residents of all ages or focus on those aged 18 and older, depending on the study's scope. In this book, I use a passenger survey dataset focused on predicting airline recommendations, specifically targeting adult passengers, as they are the ones who typically purchase tickets.
