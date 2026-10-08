
audio-visual stimuli, many studies have used film to induce arousal and valence [103]. These emotion elicitation methods have two important limitations. The set-ups used, mostly screens, are non-immersive devices, which provide only a low level of presence in subjects [30]. Therefore, the stimuli do not evoke the feeling of “being there”, which is needed to analyse emotions in simulated real-world situations. In addition the stimuli are non-interactive, so do not allow the subjects to intervene in the scene, which would open the possibility to recognise emotional states during interactive tasks. These limitations can be overcome by using immersive VR as a new emotion elicitation method. Since the year 2000, VR has increasingly been used as affective stimulus, however the majority of the studies have applied classical statistical methods, such as hypotheses and correlation, to analyse subjects' physiological responses to emotions [104]. In recent years, research has started to apply affective computing paradigms with VR as the emotion elicitation method, combining implicit measures with machine-learning methods to develop automatic emotion recognition models [105].

This paper provides a systematic review of the literature on the use of head-mounted displays in implicit measure-based emotion recognition research, and examines the progress of the research field, the emotions elicited, the data analysis, the set-ups and the validations performed.

## 2. Materials and Methods

### Data Collection

We adopted an adapted version of the Preferred Reporting Items for Systematic Reviews and Meta-Analyses (PRISMA) [106]. This includes steps to identify literature, to screen the identified literature, to check the eligibility of the screened literature and finally, to synthesize the literature. The search was queried using the following string: carried out on 25 March 2020. TITLE-ABS-KEY (“virtual reality”) OR “head-mounted display”) AND TITLE-ABS-KEY (“emotion* OR “affective*”) AND DOCTYPE (AR or re). The keywords virtual reality head-mounted display include all the studies on VR and, in particular, that all used HMDs. In addition, the keywords ‘emotion* OR ‘affective* include all the papers related to emotion. The combination of both requirements limited the search to journals and reviews (snowballing). A total of 1424 records were identified. 14 additional records were found from other sources.

The screening and eligibility checks were undertaken as follows:
- (1) first, by investigating titles and abstracts, 13 records were excluded.
- (2) The manuscripts were specially screened for a thematic match with virtual reality as emotion elicitation. A total of 1157 records were excluded for not matching the topic, and 3 records were because they were unavailable.
- (3) We investigated 265 records to exclude those that did not fit, using a specific rejection order- that is, if they used HMDs, we moved to the next criterion, implicit measures, if they used implicit measures, we moved on to the last criterion, the analysis of an emotion. 132 records were rejected for not using implicit measures, 68 for [missing text] and 23 for not analysing an emotional dimension. Finally, 42 studies were included in the analysis which used virtual reality displayed in an HMD, in combination with implicit measure to analyse or recognise emotional states. The summary of the procedure is depicted in [Figure 1].

![](img/601340ca744b738277eef45ff127492a_483_0.png)

Figure 1. Scheme of the PRISMA procedure followed in the review.

## 3. Results

### 3.1. Summary of Previous Research

In recent years, studies have applied implicit measures to analyse emotions using immersive VR with HMDs. Table 2 provides a summary of the studies included in the analysis.

Table 2. Summary of previous research.

| No | Author | Analysis | Features | Signals | Subjects | HMD | Stimuli | Comparison | Dataset Availability |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Jang et al. (2022) | 1-test | HRV, frequency domain, SC, ST | HRV, EDA | | | MD3 | VR driving | No |
| 2 | Modhan et al. (2021) | 1-test | HR, SC, ST | HRV, EDA | 67 | Not reported | 3D flying | No |
| 3 | Vu et al. (2020) | 1-test | | | HRV, EDA | | Not reported | 3D height exposure | Partially (with a different real) | No |
| 4 | Gerini et al. (2019) | ANOVA | | | HRV, EDA | 30 (with food disorders) | Not reported | VR vs. to real | No |
| 5 | Fippolo et al. (2018) | ANOVA | | | EMG | | Not reported | 3D photo and real food catering | No |
| 6 | Parwani et al. (2018) | ANOVA | | | EMG | 50 | oMeta-Z280 | 3D high-mobility walking vehicle with street | No |
| 7 | Pallanzini et al. (2013) | ANOVA | HR, SC, RSP | HRV, EDA | 39 | VR Bandle | 3D virtual lab with spiders and snakes | No |
| 8 | Pepperkin et al. (2014) | ANOVA | HR, SC | HRV, EDA | 96 (spider phobic) | oMeta-Z280 | 3D spider ball | No |
| 9 | Hartunto et al. (2014) | ANOVA | | | HRV | 75 (to high anxiety) | oMeta-Z280 | 3D social | No |
| 10 | Modhan et al. (2015) | MANOVA | | | HRV | 24 healthy subjects | NVIS-oVisor | No |
| 11 | Feisfecher et al. (2014) | Cross-correlations | | HRV, EDA | 306 | oMeta-Z280 | 3D room with time-varying threat (explosions, anger) | No |
| 12 | Notion et al. (2015) | ANOVA | SCL | EDA | 120 | HTC Re-T1 | 3D park with balloons, freedom, | No |
| 13 | Feisfecher et al. (2016) | ANOVA | HR, SC | HRV, EDA | 83 (spider phobic) | oMeta-Z280 | 3D virtual lab with spiders | No |
| 14 | Hildebrandt et al. (2017) | Regression | | | HRV, EDA | 300 | NVIS-oVisor | 3D room with threats (explosions, gunshots, etc.) | No |

| No | Author | Emotion | Signals | Features | Subjects | Analysis | HMD | VR Stimuli | Stimuli Comparison | Dataset Availability |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 15 | Figueroa-Truillo et al. [121] | Stress | EDA | SCR | 12 | Kendall test and correlations | Oculus Rift DK2 | 3D rooms (neutral, stress and scary) | No | No |
| 16 | Boon (2019) | Arousal | EDA, HRV, RSP | HR, LE, HF, HF RR | 36 | Regression | Oculus Rift DK2 | 3D Flight simulator | No | No |
| 17 | Shilton et al. (2018) | Arousal | EDA, HRV | HR, LE, HF, RR | 42 | ANOVA | Oculus Rift DK2 | 3D Trier Social Stress Test | No | No |
| 18 | Chitarco et al. (2017) | Awe | EDA, HRV, EMG | HRV, LE, SC, EMG | 45 | ANOVA | Samsung Gear | 360° neutral and awe videos | Immersive vs. non-immersive | No |
| 19 | Zeng et al. [122] | Arousal | EDA | HRV time domain and frequency (AVNN, SDNN) | 40 | t-test | Oculus Rift DK2 | 3D fire evacuation | No | No |
| 20 | Burgos et al. (2020) | Arousal | HRV, EDA | HR, SC | 51 (agoraphobics) | t-test | iVR | 3D car accident | No | No |
| 21 | van Woost et al. (2017) | Stress | EDA | FSDP, ERSP | 44 (19 women with PTSS) | MANOVA | oculus Z300 | 3D combat-related and classroom virtual | No | No |
| 22 | Banzhal et al. (2017) | Arousal | EFG | FSDP | 17 | MANOVA | Samsung Gear | 360° rooms | No | No |
| 23 | Chitarco et al. (2020) | Stress | EDA | HR, LE, HF, SC | 18 | ANOVA | Oculus Rift DK2 | 3D virtual vs. natural | No | No |
| 24 | Chitarco et al. (2017) | Valence | HRV | HR, LE, HF, LEHF | 108 | ANOVA | Sony SmartZ-3D | 3D cemetery and park | No | No |
| 25 | Figueroa-Truillo et al. (2017) | Pleasantness | HRV, EDA | SCR | 100 | Mann-Whitney U tests and correlations | Samsung Gear | 3D, 360° and real retail store (real-world elements) | real vs. 3D VR | No |
| 26 | Biedermann et al. (2018) | Arousal | EDA, HRV, RSP | HRV, SC, RR | 100 | ANOVA | HTC Vive | Mixed reality (3D VR with real-world elements) | No | Yes |
| 27 | Tsai et al. (2018) | Arousal | EDA | HRV, time domain and frequency domain (HR, LE, HF) | 30 | ANOVA | oculus Z300 | 3D catastrophic environments | Augmented reality vs. VR | Upon request |

| No | Author | Emotion | Signals | Data Analysis | Subjects | HMD | VR Stimuli | Stimuli Comparison | Dataset Availability |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 28 | Marin-Morales et al. (2019) | Arousal, Valence, Fear | EEG, HRV | PSD and functional connectivity; HRV (HR, RMSE, MSDD, and non-linear domain measures) | 60 | Samsung Gear VR | 360° virtual rooms | No | No |
| 29 | Küsker et al. (2019) | Arousal | HRV | t-test, correlation and regression | 33 | HTC Vive | | No | No |
| 30 | Goerner et al. (2019) | Arousal | | | 49 (right-handed) | Oculus Rift | 3D exposure to a high height | No | Yes |
| 31 | Zimmermann et al. (2019) | Stress | HRV | ANOVA | | | 3D forest | No | Replication of real world study |
| 32 | Lee et al. (2019) | Stress | Navigation | ANOVA; recovery of salivary alpha amylase | | HTC Vive | 3D Trier Social Stress Test | No | No |
| 33 | Schweizer et al. (2019) | Stress | HR, SC | travel time, t-test and correlation | 60 | HTC Vive | 3D, building on fire | No | No |
| 34 | Kain et al. (2019) | Calm, sadness | EEG, Patterns | ANOVA; steps walked, foot plantar pressure | 12 | Samsung Gear | 3D motion-related videos | No | No |
| 35 | Umar et al. (2019) | Arousal | EEG | PSD | 28 | Oculus Rift | 360° sport videos | No | No |
| 36 | Taka et al. (2019) | Anxiety | HRV | ANOVA; PSD and functional connectivity (HR, RMSE, MSDD, and non-linear Entropy) | 19 | | 3D concerts with public audience | No | |
| 37 | Marin-Morales et al. (2019) | Arousal, Valence | EEG, HRV | Time (HR, RMSE, MSDD, and non-linear Entropy; ...) | 60 | HTC Vive | 3D art museum | Real museum vs. 3D museum | Upon request |
| 38 | Stole et al. (2019) | Fear | EEG | ANOVA | 29 | | Oculus Rift | 3D room with angry avatars | No |
