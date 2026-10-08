
The participant has to perform 5 rounds. Each round has 20 words with a mismatch of 80% between the word and the colour it is printed with. We use several tactics to induce stress among participants. As participants were required to provide answers as quickly as possible, we first induced stress by providing performance feedback on their speed and accuracy. We further elevated stress levels by exposing the participant to loud traffic noises through a headset. Moreover, an experimenter continuously observed the participant, and verbally commented on the participant's performance. Completing the stress task took 5 min.

### 3.3.2. Task 2 [Relaxation]: Minesweeper Introduction Video

The second task aimed to induce relaxation after the stress task. It was also intended to provide an introduction to the game, Minesweeper. For this, we selected an entertaining Minesweeper Let's Play from the platform youtube.com. The video was completed beforehand with 3 pilot study participants. We explicitly informed the user that the video is purely for relaxation purposes and encouraged the user to relax and enjoy the video. The video took 5 min.

### 3.3.3. Task 3 [Stress]: Minesweeper

Previous studies already utilized Minesweeper to induce a stress condition [90,91]. Therefore, we used an implementation, where the user had to find 10 mines in an area of 10 x 10 fields within a time frame of 100 s. The user had to complete 10 rounds. To increase the stress level, the time was reduced by 10 s every round the user successfully completed the task. The score was indicated at all times, and the user was challenged to complete at least 7 rounds successfully, which was deemed to increase stress. Moreover, similar to task 1, the experimenter provided verbal comments aiming to elevate the stress level.

### 3.3.4. Task 4 [Relaxation]: Nature Video

This is the second relaxation task, in which we presented a relaxing video for 5 min. Similar to the previous relaxation task, we selected this video based on user feedback from a previous pilot study.

### 3.4. Data Gathering

The participant's plantar pressure data, as well as the accelerometer data, were collected as a time series with a sampling rate of 50 Hz and the timestamp on an SD card. The EDA data was collected with a sampling rate of 4 Hz at the Empatica E4 wristband. From this data, the mean EDA and the average slope over non-overlapping windows of 10 s were calculated. In order to collecting data, the questionnaire followed the user's perceived stress, energy level, and level of pleasantness: “How much did you feel stressed during the task? How energetic did you feel the task? How pleasant did you feel the task?” We quantified the answers by letting participants rate their answer on a 7-pt Likert scale (1: low; 7: high). Moreover, we conducted the NASA TLX to account for the induced task load. It consists of 6 questions which are equally weighted.

### 3.5. Data Analysis

To identify whether our task induced stress or relaxation as we expected, we conducted a pairwise t-Test on user's perceived stress, energy level, and the level of pleasantness and the task load. In addition, to detect significant difference of average EDA slope we conducted another t-Test. Since the data was normally distributed according to Shapiro's test, parametric tests such as pairwise t-Test and oneway-Anova were used. The participant's plantar pressure data and IMU data were used to calculate features mentioned above and used in model training.

## 6. Results

As shown in Figure 5, both stress tests, Task 1: Stroop Colour and Word Test, as well as Task 3: Minesweeper, indeed an elevated stress level based on the users' subjective rating. Task 1 scored M = 5.06 (SD = 0.68) and Task 3 scored M = 6.05 (SD = 0.76), respectively. In relaxation tasks, Task 2: Minesweeper Introduction Video, as well as Task 4: Nature Video, the average rated stress level significantly reduced to M = 2 (SD = 0.76) and M = 1.39 (SD = 0.58). A pairwise t-Test (t = 19.33, p < 0.05), demonstrating significance and providing evidence of our success in inducing stress and relaxation among the users.

| Task 1 (Stress) | Task 2 (Relaxation) | Task 3 (Stress) | Task 4 (Relaxation) |
|---|---|---|---|
| How much did you feel stressed during the task? | 5.06/7 | 2/7 | 6.05/7 | 1.39/7 |
| How energetic did you feel during the task? | 5.38/7 | 3.67/7 | 5.85/7 | 2.91/7 |
| How pleasant did you find the task? | 4.5/10 | 4.47/7 | 4.95/7 | 6.43/7 |
| Task Load | 64.83/100 | 33.55/100 | 74.67/100 | 21.3/100 |

![](img/601340ca744b738277eef45ff127492a_331_0.png)

Figure 5. Summary of the results for each task in study 1. The graph of electrodermal activity was computed using the average of the mean electrodermal activity (EDA) over non-overlapping windows of 10 s of all the participants. Accuracy graphs were computed by calculating the average stress detection accuracy of all the participants over non-overlapping windows of 10 s.

Acute stress raises adrenaline levels, making participants feel energetic. In accordance with the answers, all participants stated they felt significantly energetic during the stress task 1 (M = 5.38; SD = 0.89) and 3 (M = 5.85; SD = 1.04), than the relaxation task 2 (M = 3.67; SD = 1.67) and 4 (M = 2.91). A pairwise comparison between the stress and relaxation task demonstrated a statistical difference (t = 7.09; p < 0.05). We hypothesised that a relaxation task would be more pleasant than a stress task. The perceived pleasure was positive throughout all tasks (T1: M = 4.5; SD = 1.1; T2: M = 4.47; SD = 1.6; T3: M = 4.95; SD = 1.9; T4: M = 6.43; SD = 0.79). Grouping relaxation tasks demonstrated statistical significance only for the last relaxation task, having a nature video, was as extraordinarily pleasurable. A one-ANOVA (F(2,77) = 7.88, p < 0.05) confirmed that this as significantly more pleasant than all other tasks.

As displayed in Figure 5, the average EDA profile of the participants showed a significant increase in all stress tasks (T1 and T3) in comparison to the relaxation tasks (T2 and T4), which is evidenced by a pairwise-T test (t = 2.05; p < 0.05). These findings show that the physiological response also correlates to the self-reported stress level and with the Load Task of participants.

As previously stated, we identified four general characteristics that occurs at our point placed under pressure. We developed a model for each feature using low-dimensional identification using a machine learning classifier. We tested 5 different classifiers with our data, including Random Forest (RF) (ntree=3, mtry=2), K-Nearestbour (KNN) (k = 9), Support Vector Machine (SVM) (sigma = 13.2476, gamma = 0.25, kernel = radial), Decision Tree (CART) (cp = 0.012984) and Linear Discriminant Analysis (LDA). A one-way ANOVA for correlated samples (F(1,48) = 4.82, p < 0.05) showed significant differences. A Tukey's post-hoc analysis showed LDA-RI pairs yielded a significant difference. We selected the LDA because it showed a consistent and higher performance with our objective.

Using a supervised learning approach, we trained 10-feature models (A1, A2, ... D2) based on the annotation of our ground truth. For ground truth, we considered the data gathered from all participants, whose stress was M > 4 for the stress tasks and whose stress was M < 4 for the relaxation tasks. Hence, for training purposes, we excluded ambiguous data, which showed a low stress level at all tasks (T1: 7/23p; T3: 3/23p; T4: 3/23p). And moreover, we excluded the first 60 s and the last 60 s of each task when training at the beginning and task exhaustion at the end of the task.

Each model (A: Foot Pressure, A1: Fore Foot, A2: Rear Foot, A3: Total Foot, B: Center of Pressure B1: Co-X axis, B2: Co-Y axis, C: Accelerometer C1: X-axis, C2: Y-axis, C3: Z-axis, D: Foot Tapping, D1: Median Frequency, D2: Dominant Frequency) was trained and validated using one-leave-out method. Method, we used a user-specific model, which was trained by all other users, but does not include the one we tested with model.
