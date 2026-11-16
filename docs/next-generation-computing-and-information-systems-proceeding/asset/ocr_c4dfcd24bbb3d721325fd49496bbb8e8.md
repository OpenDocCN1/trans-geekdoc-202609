# 3 METHODOLOGY

In this section, we discussed an overview of the experiments conducted to predict ACT scores using machine learning regression models. Figure 1 provides a visual representation of the comprehensive workflow process we followed throughout our experiments. This workflow encapsulates the key stages of our research, including data preprocessing, model training, and evaluation. Each step in this process is crucial to predict ACT scores accurately. By visualizing our workflow, we aim to offer a clear and insightful glimpse into the systematic approach for our research.

![](bbox=[0.28, 0.23, 0.7, 0.59])

Figure 1. Workflow of the study.

# 3.1 Data collection and visualization

The dataset used for this experiment contains 1010 samples and initially comprises 14 attributes. This dataset was collected as part of the research conducted by Radiiah H. and Sin-Ban. (Haque et al. 2021) The dataset's attributes include the following: User Number, User ID, Location, Age, Gender, Outdoor Job, Outdoor Activities, Smoking Habit, Humidity, Pressure, Temperature, UV Index, Wind Speed and ACT Score. Figure 2 depicts the frequency distribution of each attribute within the dataset. That will give a better understanding of each attribute's characteristics.

# 3.2 Data preprocessing

We have removed the "UserNo" and "UserID" attributes, as they do not contribute to our predictive model. Several attributes, including "Age", "Gender", "OutdoorJob", "OutdoorActivities", "SmokingHabit" and "UVIndex" were categorical. To convert these attributes into numeric form, we applied label encoding, ensuring that the models could effectively utilize this information.