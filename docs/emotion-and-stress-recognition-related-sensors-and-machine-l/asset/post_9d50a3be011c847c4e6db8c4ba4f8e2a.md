
## 5.3. Apparatus and Data Gathering

Similar to the previous study, the StressFoot prototype was used to collect foot motion and pressure data. The Empatica E4 wristband was used to collect EDA, as well as motion data from the participants.

The data gathering was thus similar to the previous study. Additionally, we collected accelerometer data from the E4 wristband to identify motion (walking) and posture (sitting/standing). We used the E4's preset rate of 32 Hz. The data analysis also remained similar to the previous study. Next, we segmented the accelerometer data into non-overlapping windows. Literature suggests a window size less than 10 s, such as 2.5 s [92] or 1 s [93]. Through an experimentation with three users, we used 5 s as a suitable window size for our case. To identify motion and posture we relied on a threshold with a single feature, as mentioned by Goreski et al. [94]. The feature is the first derivative of the entire motion, also known as an "Acceleration Change Vector" (AVC) [94].

This feature can identify: 
- walking (AVC=2 ms⁻²)
- standing (AVC < 0.1 ms⁻²)
- sitting (0.1 ms⁻² < AVC < 2 ms⁻²). 

Using these timestamps, we identified the sitting time from the foot motion and pressure data from the StressFoot prototype.

Finally, the data was segmented into 10 s of non-overlapping windows. Then, all features were extracted, marked and classified using a multi-feature model (A1+B2+C3+D1). At every 10 s, the model classified whether a participant was stressed or relaxed. We then calculated the number of windows that classified stressed. This provides a measurement of the duration that a participant might have been stressed.

Therefore, for each hour, we calculated a ratio ($R_s$):

$$R_s = \frac{nWindows_{sitting}}{nWindows_{Total}}$$

## 5.4. Results

### 5.4.1 Activities

As depicted in Table 3, all participants spent the majority of their time in sitting posture (M = 79.5, SD = 6.1). Designing PCBs, coding, soldering, debugging firmware/software, reading/writing papers, meetings, writing emails, coffee/lunch and watching YouTube, were the major activities that participants performed during the 8 h field study.

| Table 3. Percentage of being in sitting posture |
| Participant | P1 | P2 | P3 | P4 | P5 | P6 | P7 | P8 | P9 | P10 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Sitting time [%] | 85.7 | 76.5 | 76.3 | 73.9 | 88.4 | 86.7 | 70.6 | 75.1 | 73.8 | |

Most of the participants marked higher stress levels (on a 7-point Likert scale) when they performed work-related activities, such as coding, debugging and writing papers. A summary of the self-reported stress level, level of energy and pleasantness among all participants is depicted in Table 4. According to the table, when participants felt stressed (Stress Level > 4), a lower level of pleasantness (M = 3.8, SD = 1.4) was reported to participants were relaxed (Stress Level < 4). Welch’s t-test confirmed that there is a significant difference (t = -4.10, p < 0.05). Moreover, Welch’s t-test showed a higher task load when participants were stressed compared to being relaxed (t = 7.02, p < 0.05). These findings confirm that we collected significantly different levels of stress (and relaxation).

| Table 4. Summary of pleasantness, energy level and task load. |
| | Stress > 4 | Stress < 4 | p | t |
| :--- | :--- | :--- | :--- | :--- |
| Level of Pleasantness | M = 3.8, SD = 1.4 | M = 5.2, SD = 0.9 | <0.05 | 4.10 |
| Level of Energy | M = 4.9, SD = 1.1 | M = 4.3, SD = 1.4 | <0.05 | 1.64 |
| Task Load | M = 62.3, SD = 8.6 | M = 42.4, SD = 11.4 | <0.05 | 7.02 |

Table 5 summarises EDA slices of the participants in stressed and relaxed conditions. When a participant marked the previous hour with a stress level > 4, we considered that hour as a high stress duration. The majority of participants (5 out of 6) demonstrated an average positive slope. Comparatively, while participants were relaxed, 8 out of 10 showed an overall negative slope. However, none of the participants showed a significantly different EDA slope according to Welch's t-test (see Table 5). The limited difference is due to high variances of EDA readings caused by factors such as motion artifacts, ambient temperature and electrode contact.

| Table 5. Summary of EDA slices of each participant while stressed and relaxed. |
| Part. No | Stress | Relax | p | t |
| :--- | :--- | :--- | :--- | :--- |
| P1 | 1.99 × 10⁻⁶ | -1.61 × 10⁻⁵ | >0.05 | 0.08 |
| P2 | | -3.58 × 10⁻⁶ | | |
| P3 | 5.16 × 10⁻⁶ | -3.93 × 10⁻⁵ | >0.05 | 0.02 |
| P4 | 2.91 × 10⁻⁶ | -9.69 × 10⁻⁵ | >0.05 | 0.17 |
| P5 | 7.04 × 10⁻⁵ | -2.38 × 10⁻⁴ | >0.05 | 0.15 |
| P6 | 2.5 × 10⁻⁵ | -6.81 × 10⁻⁵ | >0.05 | 0.38 |
| P7 | | 9.03 × 10⁻⁶ | | |
| P8 | | -5.77 × 10⁻⁶ | | |
| P9 | | 4.48 × 10⁻⁶ | | |
| P10 | -8.08 × 10⁻⁵ | -3.52 × 10⁻⁵ | >0.05 | 0.14 |

We now analyse how our models compare to the users' Self-Reported Stress Level (SRL). The graphs already demonstrate a positive correlation. To identify the significance of this relationship, we calculated the Pearsons Correlation Coefficients (r) for each participant. All participants showed a positive correlation, with an average relationship of r = 0.79 (SD = 0.10). Eight out of ten demonstrated a statistically significant relationship (r > 0.7, p < 0.05) between SRL and RS. Among these participants, three had a high correlation (r > 0.9) and only two showed a moderate Pearson Correlation Coefficient (r = 0.67 and r = 0.65). However, this result was not significant (p > 0.05). Even from two participants, P8 reported lower stress levels (<4) for the entire study duration, which is also confirmed by our model showing a lower RS (<0.5) value during the entire study period. Overall, we can conclude that all the participants showed a positive correlation, given the majority demonstrated a significantly high correlation between SRL and $R_S$. Such findings evidence the robustness of our model in-field, beyond a controlled laboratory setting.

![](img/601340ca744b738277eef45ff127492a_338_0.png)

Figure 7. The figure shows the Self-Reported Stress Level.
