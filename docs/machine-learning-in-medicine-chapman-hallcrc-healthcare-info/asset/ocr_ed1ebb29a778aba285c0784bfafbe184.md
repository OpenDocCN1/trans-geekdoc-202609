# 10.4.1 Datasets

In this research, we used three datasets:

+   - **Van Kastereren [60] dataset**: In this dataset, there are daily life activities such as sleeping, cooking, leaving home and so on and the data were collected in three different households in durations less than a month.

+   - **Aruba testbed of CASAS [16] dataset**: In this dataset, sensors such as motion, door and temperature are used. However, we use motion and door sensors in our study. In total, there are 11 activities in this dataset and the collection was done in 224 days.

+   - **WSU testbeds of CASAS [16] dataset**: In this dataset, there are five activities, which are making a phone call, hand washing, meal preparation, eating and cleaning. Twenty instances of each activity were performed by 20 students in (1) adleror and (2) adlnormal versions. While normal behavior is reflected in the adlnormal version, residents were told to include errors in adleror to simulate the difficulties of elderly people.

# 10.4.2 Data Generation

Abnormal behavior in the daily life activities of elderly people is divided into two parts: (1) activity-related anomalies and (2) sub-activity-related anomalies. In activity-related anomalies, an activity itself is totally normal while there is an anomaly related to its frequency or its timing in a day. On the other hand, the sub-activity-related anomaly is related to the context and the quality of activity performed such as frequency of sensor activations involved as well as their order and correlation. In the first one, activities as a whole are repeated or forgotten (e.g. having dinner); while in the second one, some steps (sensor activations) of activities are forgotten or repeated (e.g. adding salt to the dish).

# *10.4.2.1 Activity-Related Abnormal Behavior*

To simulate these types of indicators, we insert a set of actions into the whole day actions of activities (see Algorithm 10.1), which will give multiple instances of the same type of an activity. Moreover, insertion in some inadequate time of the day will generate time-related abnormalities such as waking up and eating. We insert the following activities: preparing meal, eating, working, washing dishes, leaving home and entering home into the normal activity sequences of the Aruba dataset.