
model using features provides reasonable accuracy (M = 83.9%). However, the standard deviation (SD = 12.01) is higher than any other model. The highest accuracy (M = 85.32; SD = 8.1) was from the of all four performers (A1+B2+C3+D1). Although the standard deviation is relatively high as a single feature model, C3 showed the highest accuracy (M = 83.1; SD = 11.9) compared to other single feature models. In addition, a pairwise f-Test was used to identify the separation between stress and relaxation tasks. Except for model A3, all other models showed high distinguishability (See Table 1).

Table 1. Model performance (selected classifier: Linear Discriminant Analysis (LDA)).

| Feature | A1+B2-C3 | C3+A1 | A1 | B2 | D1 | B1 | A2 | A3 |
|---|---|---|---|---|---|---|---|---|
| Accuracy % | 85.2 | 85.0 | 83.1 | 79.8 | 69.3 | 67.5 | 66.6 | 62.5 | 50.7 |
| SD% | 9.7 | 12.0 | 11.1 | 6.7 | 7.9 | 8.0 | 6.7 | 11.4 | 10.8 | 9.2 |

## 4. Empirical Relaxation–Study 2

To validate the generalizability of our models, we replicated the study with different participants, using different users and different tasks. The study protocol was approved by the University of Auckland Human Participants Committee.

The apparatus and data remained the same. The procedure was very similar, with only the difference being between a single stress and a relaxation task. After each task, participants were asked to answer the questionnaire from our study and to complete a NASA Test. The data analysis remained the same. We recruited 11 participants (7 males and 4 females), aged 22-34 (M = 26.4, SD = 3.17) with ethnicity: the inclusion/exclusion criteria were similar to this study. We also used a different stress (Task 5: Mental Arithmetic Test) and relaxation (Task 6: Nature video).

Participants were asked to complete 20 challenging maths questions based on fundamental mathematics within 5 min. We created additional pressure by informing participant's performance will be graded. Similar to previous tasks, an experimenter observed their performance and commented on their performance.

To relax the user, we showed a 5 min nature video with soothing music. The video was different than the one in Task 4.

In accordance with the questionnaire, the participants agreed they felt stress (M = 85.36; SD = 0.92) during the mental arithmetic task and relaxed (M = 1.72; SD = 0.64) during the relaxation task (see Figure 6). A pairwise t-test (t = 11.74; p < 0.05) confirmed that all participants felt more stressed Task 5 (M = 3.45; SD = 2.01), which was confirmed as statistically significant following a pairwise t-test (t = 2.55; p < 0.05). Additionally, participants rated the relaxed (M = 6.36; SD = 0.67) as more pleasant than the stress task (M = 4.18; SD = 2.13), which was evidenced by a pairwise t-test (t = 3.54; p < 0.05). Most crucially, in terms of Task Load (equally weighted), a pairwise comparison (t = 9.49; p < 0.05) between two tasks clearly indicated that stress 5 induced a higher task load than relaxation Task 6.

### Task 5
[Stress]

### Task 6
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

![](img/601340ca744b738277eef45ff127492a_334_0.png)

A: Foot Pressure (Insole) A1: Fore Foot

![](img/601340ca744b738277eef45ff127492a_334_1.png)

B: Center of Pressure (Insole) B2: CoP Y-Axis

![](img/601340ca744b738277eef45ff127492a_334_2.png)

C: Foot/Leg Posture (Accelerometer) C3: Z-Axis

![](img/601340ca744b738277eef45ff127492a_334_3.png)

D: Foot Tapping (Accelerometer) D1: Median Frequency

![](img/601340ca744b738277eef45ff127492a_334_4.png)

Multi-Feature Models A1+B2+C3+D1 ALL

![](img/601340ca744b738277eef45ff127492a_334_5.png)

**Figure 6.** Results of generalizability. The graph of electrodermal activity and accuracy shows the averages of the 11 participants over non-overlapping windows of 10 s.

These subjective ratings are also consistent with the physiological data gathered—average EDA response. It showed an overall increasing slope at the stress task 5 and negatively decreasing slope for relaxation task 6. The trend of both tasks by a t-Test confirmed the average EDA slopes to be significantly different (t=6.9, p < 0.05).

The features were extracted as mentioned before and classified (using LDA) with seven previously built models. We chose four single feature models based on the best performer for each characteristic, which are: A1, B2, C3 and D1. Furthermore, we used a multi-feature model combining all four. The sixth model was generated based on previous data and by combining the meaningful features of A1 and C3. The final model was a combination of all computed features. Again, we windowed the accuracy of models over 10 s to observe any periodic trends (see Figure 6).

The overall accuracy rates are shown in the Table 2. A one-way ANOVA for correlated samples ($F_{6,319}=12, p<0.05$) showed significant differences between the accuracy of the models. A Tukey's post-hoc analysis revealed the significant difference occurred due to the low mean accuracy of D1. Since model A1+B2+C3+D1 showed slightly higher accuracy than C3+A1 and a lower standard deviation ($M=87.5; SD=10.0$), we suggest it is the best performing model. Furthermore, it will work for most of the users, since it considers a feature such as D1.

Table 2. Performance for sets of participants (classifier: LDA).



| Feature Model | A1+B2+C3+D1 | C3+A1 | ALL | C3 | B2 | D1 |
|---|---|---|---|---|---|---|
| Accuracy [% | 87.45 | 87.5 | 86.6 | 89.7 | 79.6 | 66.5 |
| SD [% | 8.5 | 9.6 | 12.0 | 10.5 | 6.5 | 7.6 |

## 5. Experimental–Study 3

In this study, the goal is to demonstrate the robustness of our model. Therefore, we conducted an in-field study where we recorded data over a day. Similar to the previous studies, the University of Auckland Human Participants Committee approved the protocol.

We recruited 10 participants (7 males and 3 females) aged 25-34 ($M=29.9; SD=3.4$). Among these participants, four were from the first study, another four from the second study and two were newly recruited. A requirement for our participant selection was a foot size that matched the prototype. In addition, the participant had to work in an office and spend the majority of their time in a sitting position (>70%). Apart from this, the inclusion/exclusion criteria remained similar to previous studies.

The study was conducted on a particular day that the participants expected to have some periods of acute stress. The stress tasks included working for a deadline, debugging a firmware/software, having a meeting with their supervisor, writing a paper for an upcoming submission. Having lunch/coffee with friends and having casual chats with friends were activities that possibly relax stress. We began at 09:45 a.m. time at the participants' office space. After explaining the study procedures, filling consent forms and collecting demographic data, the experimenter installed the participants to wear the StressFoot and E4. At 10:00 a.m., the experimenter initiated apps for data collection and asked participants to report their current stress level, energy level and how pleasant they felt on a 7-point Likert scale. Then we asked them to continue their work. As we asked participants to fill out two forms, a calendar application reporting the time and duration of tasks performed, as well as a questionnaire. These were the only tasks we asked the participants to perform hourly 8 h from 10:00 a.m. to 6:00 p.m. To ensure the participants would remember to report and fill out the calendar and the form, they received reminders via visual and audio pop-ups at the end of each hour. The questionnaire asked the participants to rate their perceived stress level, energy level, as well as how pleasant they felt during last hour. Part of the questionnaire was to fill a NASA TLX, which was used to calculate the overall workload.
