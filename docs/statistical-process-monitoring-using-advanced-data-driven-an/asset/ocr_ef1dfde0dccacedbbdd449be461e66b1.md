![](bbox=[0.21, 0.105, 0.79, 0.515])

# FIGURE 8.18 Hybrid DBN-OCSVM monitoring framework.

# 8.3.3.1 Results and discussion

In this section, we first present a preliminary analysis of the considered ozone dataset. Then, the performance of the deep-learning-based methods for detecting abnormal ozone measurements is evaluated. Finally, we compare the detection results of the DBN-OCSVM approach to those of the standalone clustering methods and the DSA-based clustering methods.

The data chosen to develop the DBN model is anomaly-free, and it was collected from January 1 to March 4, 2015 (see Fig. 8.19). A heatmap of the correlation matrix of the ozone data is presented in Fig. 8.20. As can be seen in the figure, data from the majority of stations are highly cross-correlated. Additionally, there are three clear groups: stations S1–S8, stations S9–S13, and station S14. The data within the first and second groups shows high cross-correlation because they are in close proximity to each other (Fig. 8.16). The data from station S14 have a relatively low correlation with data from the other stations. This is because the data from station S14 were collected from a rural zone, and the variation of ozone in rural zones differs from the variation in urban and peri-urban zones. Specifically, in rural zones, the level of ozone is higher at night because of the low presence of ozone destroyers.