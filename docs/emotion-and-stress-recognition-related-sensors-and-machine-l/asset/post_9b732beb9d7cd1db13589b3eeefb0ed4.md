
## Table 2. Cont.

| No | Author | Emotion | Signals | Features | Data | Analysis | Subjects | HMD | VR Stimuli | Stimuli Comparison | Dataset Availability |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 39 | Cerato et al. (2020) | Annoyed Valence | HRV, EDA, EEG | HRV, SCG, SCR, EDA, Thr | Mean, Gradient, Process | KNN, SVM, NNN | Oculus Rift2 | 3D video games | No | Yes | |
| 40 | Bán et al. (2020) | Fear | HRV, EDA | Fixation counts, TFFT | MANOVA, t-test | 53 (slightly anxious) | HTC Vive | 3D acrobatia game | No | No | |
| 41 | Rosado et al. (2021) | Fear | Signal: electroencephalography (EEG), electromyography (EMG), heart rate variability (HRV), high frequency (HF), low frequency (LF), LF(low/high frequency ratio), low frequency (VLF), total skin conductance ratio, skin conductance level (SCL), skin evoked potentials (ERPs) and time to first fixation | Data analysis: k-nearest neighbors algorithm (KNN), support vector machines (SVM), random forest (RF), neural networks (NN) | SCL | HRV, EDA | | Oculus Rift2 | 3D room with angry avatars | No | No | |
| 42 | Huang et al. | | | | | | | | | | | |

### 3.2. Evolution of the Research

Figure 2 shows the number of papers published each year which included the topics virtual reality and emotion analysis. This number of studies was calculated based on all the papers screened. In the 1990s, the average number of papers published annually was 6.4, the first being in 1995. In the 2000s, the average number of papers published increased to 26.3, from 2010 to 2014, the average multiplied by three to 77.4. In the last five years, the curve has grown exponentially to 203 in 2019, and 278 in 2020.

![](img/601340ca744b738277eef45ff127492a_488_0.png)

**Figure 2.** Evolution of the number of papers published each year on the topic of virtual reality and emotions. The total number of papers to be published in 2020 has been extrapolated using data up to 25 March 2020.

### 3.3. Analysis

Figure 3 depicts the evolution in the number of papers analysed in the review based on the emotion analysis. Until 2015, the majority of the papers analysed arousal-related emotions, mostly arousal, anxiety and stress. From that year, some experiments started to analyse valence-related emotions, such as valence, joy and sadness, but the analysis of arousal-related emotions was still predominant. 50% of the studies used CRA (arousal 38.1% [54] and anxiety 11.9% [125]), and the other 50% used basic or complex emotions (stress 23.8% [112], anxiety 16.6% [109], fear near 11.9% [43], awe 2.4% [121], calmness 2.4% [135], joy 2.4% [135], pleasantness 2.4% [6] and sadness 2.4%).

### 3.4. Implicit Techniques, Features and Participants

Figure 4 shows the evolution of the number of papers analysed in the implicit measures used. The most used were HRV (73.8%) and EDA (59.5%). However, the majority of the studies used ANS to analyse emotions. The majority of the studies that used HRV used very few features from the frequency domain, such as HF, LF or HF/LF [119,126] and 2 non-linear features, such as Poincare and Poincaré [65,105]. Of the studies that used EDA, the majority used tonic skin conductance (SC) [116] but some also used tonic (SCL) [54] or phasic activity (SCR) [124]. In recent years, EEG has increased, with 6 papers being published (14.3%), and the CNS has started to be used, in combination with HMDs, to recognise emotions. The analyses that have been used were ERP [138], power spectral density [140] and connectivity [65]. EMG (11.9%) and RSP (9.5%) were also used, mostly in combination with HRV. Other implicit measures used were eye-tracking, gait patterns and salivary cortisol responses.

The average number of participants used in the various studies depended on the signal, that is, 75.34 (σ = 73.57) for EDA, 68.58 (σ = 68.35) for HRV and 33.67 (σ = 21.80) for EEG.

### 3.5. Data Analysis

Figure 5 shows the evolution of the number of papers published in terms of the data analysis performed. The vast majority analysed the implicit responses of the subjects in different emotional states using hypothesis testing (83.33%), correlations (14.29) or linear regression (4.76%). However, in recent years, we have seen the introduction of supervised machine-learning algorithms (11.90), such as SVM [105], Random Forest [139] and KNN [140] to perform automatic emotion recognition models. They have been used in combination with EEG [65], HRV [105] and EEG [140].

![](img/601340ca744b738277eef45ff127492a_489_0.png)

**Figure 3.** Evolution of the number of papers published each year based on emotion analysed.

![](img/601340ca744b738277eef45ff127492a_489_1.png)

**Figure 4.** Evolution of the number of papers published each year based on the implicit measure used: HMDs and Formats

### 3.6. VR Set-Ups

Figure 6 shows the evolution of the number of papers published based on HMD used. In the first years of the 2010s, eMagin was the most used. In more recent years, advances in HMD technologies have positioned HTC Vive as the most used (19.05%). In terms of formats, 3D environments are the most used [138] (85.71%), with 360° panoramas following far behind [142] (16.67%). One research used both formats [64].

![](img/601340ca744b738277eef45ff127492a_490_0.png)

**Figure 5.** Evolution of the number of papers published each year by data analysis method used.

![](img/601340ca744b738277eef45ff127492a_490_1.png)

**Figure 6.** Evolution of the number of papers published each year based on head-mounted display (HMD) used.

### 3.7. Validation of VR

Table 3 shows the content of the papers that presented analyses of the validation of VR in an emotional research. 83.3% of the papers did not present any type of validation. Three papers included direct comparisons of results between VR environments and the physical world [64,65,109], and 3, in terms of the formats used, the emotional reactions evoked in 3D VRs, photos [109], 360° panoramas [64] and augmented reality [129]. Finally, another compared the influence of immersion [121], the similarity of VR results with previous datasets [108] and one compared its results with a previous version of the study performed in the real world [132].

## Table 3. Previous research that included analyses of the validation of virtual reality (VR).

| Type of Validation | % of Papers | Number of Papers |
| :--- | :--- | :--- |
| No validation | 83.33% | 35 |
| Real | 7.14% | 3 |
| Format | 7.14% | 3 |
| Immersivity | 2.38% | 1 |
| Previous datasets | 2.38% | 1 |
| Replication | 2.38% | 1 |

This work highlights the use of immersive VR, in particular using head-mounted displays, in emotion recognition in combination with implicit measures. It provides a clear perspective based on a systematic review and aggregated analysis, focusing on the role that VR might play as an elicitation tool in the coming years.

The evolution of scientific VR and emotions has grown exponentially, to more than 200 papers per year (Figure 2). However, the performance improvements in the last few years in the latest generation of HMDs, in terms of resolution, field of view, immersion levels and the fall in their price, has boosted their use in emotion-recognition research. With VR's increased application in recent years in other areas, such as rehabilitation, neuropsychology and therapy [2], results suggest that the 2010s were the decade of rapid growth of VR in emotion research using implicit measures, and the 2020s might be the decade when the future unfolds. Environmental simulations might, in the future, go beyond the paradigm of non-immersive/video-based 2D images to immersive scenarios, where subjects feel a strong sense of presence and can interact with the stimuli presented.

Regarding HMDs and implicit measures in emotion analysis, there is no consensus about the use of CMA [92] or the Ekman theory of basic emotions [91], both approaches are used in 50% of the research (Figure 3). The differences in the frameworks used caused some disparities in comparing the results of different studies. The majority of the studies (80.5%) included analyses of arousal [54], or high-arousal-discrete emotions, such as stress [112], anxiety [119] and fear [43]. On the other hand, only 29.9% of the studies analysed emotions closely related to valence, such as awe [121], calm [93], joy [108] and sadness [135]. Therefore, the challenge of effective affective computing using HMDs is in its first growth phase, and physiological dynamics, in particular, are under-researched. Recent research since 2017 has started to address this [65,139], a dimension of the CMA not addressed in general affective computing research using pictures or videos [143] has also not been in HMD set-up. However, a basic emotion closely related to the dominance, was analysed in 11.9% of the studies enrolled. In contrast to that the challenge is felt when someone watches a horror film, is by the empathy of with the protagonist, the level of presence that immersive VR allows the analysis of fairly directly felt by subjects on scenarios they are viewing. In the future, VR will allow researchers to analyse the dimension of dominance in affective computing research.

In terms of the implicit measures used to recognise emotions through HMDs, ANS measures are used most: HRV (73.8%) and EDA (55.9%), many times used in combination. However, until 2016, the majority of the papers used only HR and SC (Table 2), in combination with EMG and GSR. From 2016, the research started to include HRV frequency domain and non-linear dynamics analyses [105,119], and EDA analyses, such as CDA, dividing the signals into tonic and phasic components [64]. In terms of the CNS, EEG research has been undertaken since 2016, including ERP [138], power spectral density [140] and functional connectivity analysis [65]. Other non-physiological implicit measures have been used since 2019, as eye-tracking [141], gait
