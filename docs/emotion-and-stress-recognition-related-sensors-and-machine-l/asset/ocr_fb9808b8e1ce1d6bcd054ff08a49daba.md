$a_a = a_f + a_t,$

where $a_f, a_t$ and $a_a$ represents the frontal alpha, temporal alpha, and alpha asymmetry respectively and $a_{channel}$ represents the alpha power spectral density of the frontal and temporal EEG channels. Similarly, the frontal and temporal beta asymmetries were calculated using,

```
$$\beta_f = \frac{\beta_{AF4} - \beta_{AF3}}{\beta_{AF3} + \beta_{AF4}}$
```

```
$$\beta_t = \frac{\beta_{TR8} - \beta_{T17}}{\beta_{T17} + \beta_{TR8}}$
```

where $eta_f$, and $eta_t$ represents the frontal and temporal beta asymmetries and $eta_{channel}$ represents the beta power spectral densities for the frontal and temporal bays. Features were evaluated using a t-test for determining the statistical significance of features in stress and control group. A lower p-value returned by the t-test shows that the feature was significantly discriminating in stress and control group.

# 3.4. Subject Labeling

The proposed method uses two types of labeling for supervised classification. PSS-10 was used for the questionnaire-based labeling to objectively evaluate the stress of participants. This questionnaire consists of ten questions. Each question asks the subject about the frequency of stressful events that occurred. The response for each question is on a scale of 0 to 4, where 0 represents the event never occurred and 4 represents a frequent occurrence. The total PSS score for each participant has a range between 0 and 40. The participants are divided in two groups i.e., the control and stress group, using the PSS score. A threshold was selected for purpose, which was given by the following:

```
$T_p = \mu \pm \frac{\sigma}{2},
```

where $T_p$ is threshold of PSS score, $\mu$ is the mean, and $\sigma$ is standard deviation of the PSS scores.

The psychologist assigned labels for the stress and control groups after an expert evaluation based on the interview and PSS scores. During the interview, the expert investigated the physical, emotional, behavioral, and cognitive symptoms of stress. Physical symptoms included aches or pain, diarrhea or constipation, nausea, dizziness, chest pain, and rapid heart rate. Emotional symptoms of stress depression, anxiety, moodiness, irritability, overwhelming feelings, and lonesomeness. Behavioral and cognitive symptoms included memory problems, inability to concentrate, poor judgment, negativity, racing thoughts, and constant worrying. The interviews were conducted by the psychologist who was affiliated with a public sector hospital. The labels (control/subject) were assigned to participants by the expert based on the responses and the PSS score for each participant. The eighteen symptoms evaluated by the expert are presented in Table I. The assigned labels were used as ground truth for the system using the corresponding EEG records for each subject.