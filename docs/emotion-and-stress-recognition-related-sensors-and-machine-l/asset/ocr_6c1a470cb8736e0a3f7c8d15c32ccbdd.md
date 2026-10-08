# Task 5
[Stress]

# Task 6
[Relaxation]

How much did you feel stressed during the stress task?

| 5.36/7 | 1.72/7 |

How energetic did you feel during the task?

| 5.18/7 | 3.45/7 |

How pleasant did you find the task?

| 5.18/7 | 6.36/7 |

Task Load

| 71.41 / 100 | 19.39 / 100 |

Electrodermal Activity

![](bbox=[0.304, 0.27637, 0.696, 0.32533])

A: Foot Pressure (Insole) A1: Fore Foot

![](bbox=[0.304, 0.34026999999999996, 0.696, 0.38973])

B: Center of Pressure (Insole) B2: CoP Y-Axis

![](bbox=[0.304, 0.41107, 0.696, 0.45957])

C: Foot/Leg Posture (Accelerometer) C3: Z-Axis

![](bbox=[0.304, 0.47937, 0.696, 0.52883])

D: Foot Tapping (Accelerometer) D1: Median Frequency

![](bbox=[0.304, 0.54977, 0.696, 0.59873])

Multi-Feature Models A1+B2+C3+D1 ALL

![](bbox=[0.304, 0.61907, 0.696, 0.66853])

**Figure 6.** Results of generalizability. The graph of electrodermal activity and accuracy shows the averages of the 11 participants over non-overlapping windows of 10 s.



These subjective ratings are also consistent with the physiological data gathered—average EDA response. It showed an overall increasing slope at the stress task 5 and negatively decreasing slope for relaxation task 6. The trend of both tasks by a t-Test confirmed the average EDA slopes to be significantly different (t=6.9, p < 0.05).



The features were extracted as mentioned before and classified (using LDA) with seven previously built models. We chose four single feature models based on the best performer for each characteristic, which are: A1, B2, C3 and D1. Furthermore, we used a multi-feature model combining all four. The sixth model was generated based on previous data and by combining the meaningful features of A1 and C3. The final model was a combination of all computed features. Again, we windowed the accuracy of models over 10 s to observe any periodic trends (see Figure 6).