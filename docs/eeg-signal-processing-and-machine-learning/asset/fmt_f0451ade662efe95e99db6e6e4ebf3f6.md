
The scalp projections of P3a and P3b for five selected trials are shown in [Figures 13.11](#c13.xhtml#c13-fig-0011) and [13.12](#c13.xhtml#c13-fig-0012) for before and during fatigue state respectively.

Although there is not a significant difference in the estimated scalp projections for P3a and P3b before and during fatigue state, the important issue is the separation of these subcomponents and estimation of other parameters. The results obtained by considering one subject confirm that the suggested paradigm is a good option for designing a mental fatigue detection system and the estimation of P300 subcomponent parameters can be good features for discriminating the fatigue state. Other important features can be obtained using phase synchronization measures.

![Figure 13.10 The ERP achieved by averaging 40 EEG trials before and during the fatigue state from the Cz channel.](images/c13f010.gif)

[**Figure 13.10**](#c13.xhtml#R_c13-fig-0010) The ERP achieved by averaging 40 EEG trials before and during the fatigue state from the Cz channel.

From what has been discussed previously, the phase synchronization of different EEG rhythms especially alpha rhythm can be used as good features for recognition of the fatigue state. To investigate this, three seconds of the data segment has been considered and the `EMD` applied to decompose the EEG signal into its constituent oscillations. For the beta rhythm, the `ALE` is applied to the resulting `IMF`. One second of data segment (1000 samples) before stimulus onset and one second after stimulus onset are considered for measuring the phase synchronization. Beta and theta rhythms are extracted from frontal electrodes (`F3` and `F4` channels) and the alpha rhythm is extracted from central electrodes (`C3` and `C4` channels). The phase synchronization is calculated for five trials for one second before and after stimulus onset. The calculated phase synchronization for theta, alpha, and beta rhythms can be seen in [Figures 13.13](#c13.xhtml#c13-fig-0013), [13.14](#c13.xhtml#c13-fig-0014), and [13.15](#c13.xhtml#c13-fig-0015) respectively. In these figures the average phase synchronization is also depicted by the thick line. From these figures the changes in phase synchronization can be clearly seen for alpha and theta rhythms before stimulus onset. Therefore, using the recorded EEG signal the EEG phase synchronization can be considered as a good feature for discrimination of the fatigue state.

## 13.7 Assessing Mental Fatigue by Measuring Functional Connectivity

Similar to many other applications, the brain connectivity is expected to vary during the alert‐to‐fatigue transitions. One early attempt in this study was in [\[49\]](#c13.xhtml#c13-bib-0049) where they estimated the multivariate autoregressive (`MVAR`) model coefficients from multichannel EEG signals and classified them using different classifiers such as a multiclass `SVM`. `MVAR` parameters indeed represent the brain connectivity, as they are estimated not only based on the individual channel history but also the correlations with other channels. They also applied `KPCA` in order to reduce the number of features before applying the classifier.

![Figure 13.11 The estimated scalp projections of P3a (top row) and P3b (bottom row) before fatigue.](images/c13f011.gif)

[**Figure 13.11**](#c13.xhtml#R_c13-fig-0011) The estimated scalp projections of P3a (top row) and P3b (bottom row) before fatigue.

![Figure 13.12 The estimated scalp projections of P3a (top row) and P3b (bottom row) during the fatigue state.](images/c13f012.gif)

[**Figure 13.12**](#c13.xhtml#R_c13-fig-0012) The estimated scalp projections of P3a (top row) and P3b (bottom row) during the fatigue state.

![Figure 13.13 Theta phase synchronization of F3–F4: (a) before stimulus and (b) after stimulus.](images/c13f013.gif)

[**Figure 13.13**](#c13.xhtml#R_c13-fig-0013) Theta phase synchronization of F3–F4: (a) before stimulus and (b) after stimulus.

![Figure 13.14 Alpha phase synchronization of C3–C4: (a) before stimulus and (b) after stimulus.](images/c13f014.gif)

[**Figure 13.14**](#c13.xhtml#R_c13-fig-0014) Alpha phase synchronization of C3–C4: (a) before stimulus and (b) after stimulus.

![Figure 13.15 Beta phase synchronization of F3–F4: (a) before stimulus and (b) after stimulus.](images/c13f015.gif)

[**Figure 13.15**](#c13.xhtml#R_c13-fig-0015) Beta phase synchronization of F3–F4: (a) before stimulus and (b) after stimulus.

In another attempt, Qi et al. [\[50\]](#c13.xhtml#c13-bib-0050) used `fMRI` and introduced an empirical method to examine the reorganization of dynamic functional connectivity in a two‐session experiment where one session including a mid‐task break (Rest) was compared to a successive task design in the other session (No‐rest). In their method, the functional connectivity has been estimated over a sliding window to construct the temporal brain network. The networks were estimated from 20 participants and the spatiotemporal architecture was examined by temporal efficiency analysis.

Task breaks would allow for retrieval of the mental resources, as well as return to the initial task goals and the adjustment of one's effort allocation strategy, which in turn may relieve mental fatigue and improve behavioural performance. Moreover, varying the break length affects the recovery from fatigue.

They demonstrated that taking a mid‐task break leads to a restorative effect towards the end of the experiment instead of an immediate post‐rest behaviour recovery. Also, the reduced spatiotemporal global integrity of the temporal brain network in a No‐rest session was significantly improved with the break opportunity in the last task block of the Rest session. Hence, they provided evidence to support the beneficial effect of rest breaks in both behaviour performance and brain function. Moreover, these findings extended prior static functional connectivity studies of mental fatigue and highlight that altered dynamic connectivity may underlie cognitive fatigue [\[50\]](#c13.xhtml#c13-bib-0050).

In [\[51\]](#c13.xhtml#c13-bib-0051) the `EEGs` have been analyzed using functional connectivity estimated by Granger causality. The authors concluded that the topology of the brain networks and the brain's ability to integrate information changed in transition from alert to fatigue. They also observed a significant difference in terms of strength of Granger causality in the frequency domain and the properties of the brain effective network, i.e. causal flow, global efficiency, and characteristic path length between such conditions. Larger variations were observed over the frontal brain lobes for the alpha frequency band.

The use of brain connectivity for analysis of mental fatigue and drowsiness has been reported in a number of other publications including \[[52](#c13.xhtml#c13-bib-0052), [53](#c13.xhtml#c13-bib-0053)\]. In [\[52\]](#c13.xhtml#c13-bib-0052) the 32‐channel `EEGs` are first restored from eye‐blink artefact using second‐order blind identification (`SOBI`) `ICA` method. After `ICA` the sources with maximum correlation with `EOG` are removed as eye‐blinks. Then, the differences between the covariances of six regions have been used as the indices for classification. These regions are centro‐frontal, centro‐posterior, left and right fronto‐laterals, and left and right posterio‐lateral brain zones.
