He et al. [5] developed a ten-layer CNN to detect cognitive stress based on short-term ECGs. Here, spectrum information was used to extract consecutive ECG R-peaks for use as instead of raw ECG data. This study also used a sliding window method to increase the number of data points. Their results showed that the proposed CNN achieved a lower error rate than conventional machine learning models. In addition, the authors found that meaningful information related to stress lie in the 0.4–20 Hz range by visualizing the activation maps of multiple layers. This demonstrates that deep learning approaches can benefit from having data-driven features that are not captured by conventional machine learning approaches.

# 3. Methods



We recruited 18 subjects (8 females and 10 males, 24.6 ± 4.6) from Pohang University of Science and Technology (POSTECH), South Korea, via open recruitment. The study subjects were selected based on the following criteria: (1) they had no cardiovascular or mental problems and (2) they had not undertake exercise before the day of the test and (3) they had not caffeinated beverages on the day of the test. This study was approved by the POSTECH Ethics Committee (IRB-2019-E001).

The experiments were conducted parallel normally, unexpected technical problems (namely a subject's carelessness and an unexpected Windows OS update) occurred during two experiments, meaning that these two subjects' data were not captured fully. Thus, we used the datasets from the remaining 16 subjects.

# 3.2. Experiments



Each experiment set took about 1 h, and comprised two stages: (1) an initial relaxation stage (colored with light green), before the experiment began (about 15–20 min) and (2) the main relaxation stage (about 45 min). These are described in more detail in Figure 1.

![](bbox=[0.245, 0.603, 0.755, 0.715])

> Figure 1. An experiment process. There are two stages for the experiment: an initial relaxation stage (colored with light green), and a relaxation stage (indicated by gray lines). The regular experiment stage can be segmented into 5 min of relax tasks (colored with dark green) and stress tasks (colored with orange). From the start to end of the regular experiment, subjects' physiological signals were captured by a wearable device. At the end of each short relax or a stress task, a mental stress level assessment was carried (with an orange arrow).

During the initial relaxation stage, each subject was asked to wear a wearable device that collected ECG and RESP data and to completely relax, eliminating any excitement or nervousness regarding the experiment. In addition, we explain our protocol to prevent any mistakes by the subject. During the main experiment stage, the subjects alternately experienced simulated relaxing states (called RELAX tasks in Figure 1) and stressful states. During the relaxations,