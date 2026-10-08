
![](img/601340ca744b738277eef45ff127492a_207_0.png)

![](img/601340ca744b738277eef45ff127492a_207_1.png)

**Figure 2.** Generic in-ear EEG prototype [37]. The left side illustrates a drawing whereas right side illustrates a model prototype.

Netflix, from our test, the in-ear EEG device built from memory foam ear-plugs could not fit into small ear canals. Furthermore, in fit, it could gradually slip out of the ear canal. Thus, in this study, the main body of the in-ear EEG device was changed to earphone rubbers, which were tested and found to have high flexibility. Additionally, they come in different sizes which could be properly selected to fit different ear canals, as shown in Figure 3.

![](img/601340ca744b738277eef45ff127492a_207_2.png)

**Figure 3.** Different sizes of earphone rubbers.

### 3.1.2. Electrode Selection

Three different materials were considered and tested for the in-ear EEG device electrodes, a half-sphere shaped silver, aluminum foil, and silver-adhesive fabric. The half-sphere shaped silver is probably one of the most widely-used materials for EEG electrodes. However, according to [30] the electrodes should be as flexible as possible to the earpiece to ensure robust contact. Half-sphere silver is solid and not as flexible as the earphone rubbers. Therefore, the half-sphere silver was not selected. For aluminum foil, although it has low impedance and flexibility, it could not be easily attached to electrodes. This is because the aluminum foil is not adhesive to soldering.

The silver-adhesive fabric, which was used with memory foam as in-ear EEG device prototype [30], has similarity to memory foam and earphone rubbers. It could also be glued and sewn to the wires without soldering. Therefore, the silver-adhesive fabric was considered suitable material for the electrodes for our in-ear EEG device.

In this study, the size of the fabric was much larger than in the previous study [30] for better contact. The fabric was glued to the earphone rubbers, and the shield wires were then sewn to the fabrics. The number of the electrodes was also reduced to one channel per ear as the EEG signals among channels in the same in-ear from the previous studies were very similar [17]. The shield wire was slightly larger and heavier than a normal wire. However, it significantly reduced signal noise. Therefore, it was preferable to use standard wire.

Our final prototype of in-ear EEG device is shown in Figure 4. The total material cost per piece is approximately 10 US Dollars. Our in-ear EEG device's impedance was measured to be between 0.05 and 5.5 ohms which was comparable to that of OpenBCI electrodes: one of the commercial EEG electrodes [38].

![](img/601340ca744b738277eef45ff127492a_208_0.png)

**Figure 4.** Single channel electrode used in the experiment using earphone rubber and silver-adhesive fabric electrode.

After the in-ear EEG devices were assembled, signal verification was performed. Mismatch tone (MMN) is one of the widely-used methods for EEG verification [39,40]. It was used to verify in-ear signals in the previous study [41]. Hence, it was also applied in our work. MMN is an experiment that observes the auditory event-related potential (ERP). ERP is a subject's EEG response to an unexpected change of sensory perception.

Our MMN experiment started by playing a short beep tone repeatedly until the subject was familiar to the unexpected tone. Unexpected mismatch tones were inserted among the familiar tone. Unexpected mismatch tones had a change of frequency (lower or higher), intensity (unusually louder or lighter), or phase. The mismatch tone, if acknowledged, will provide an ERP response as a negative peak. The mismatch responses usually give a negative peak between 90 and 250 milliseconds after the beep [41]. The ERP latency may vary according to personal memory [42].

The MMN experiment parameters in this study were set according to the previous study [40]. A combination of three tone frequencies: 500, 1000, and 1500 Hz lasting for 75 milliseconds, were used as a standard tone, whereas two types of mismatch tones were used. The first type was frequency mismatch containing 10% lower or higher pitch applied to each frequency. The other type was a duration mismatch tone which lasted for 100 milliseconds, 25 milliseconds longer than the standard tone. With the tone, the mismatch tones were inserted. Mismatched tones arrived at the probability of 0.5, but no consecutive mismatch tones were allowed.

The tones were played through an earphone. The in-ear EEG device was inserted to the right ear while the earphone was inserted to the left ear. The ground electrode was placed on the forehead and the reference electrode was placed on the right cheek, as suggested by [43]. OpenBCI's electrode was also placed at T8 as a comparison electrode. A Butterworth filter was used to notch 50 Hz powerline noise. It was applied as a bandpass to filter the EEG signal between 2 and 30 Hz. The signal correlation between T8 and in-ear EEG was also calculated.

### 3.3. Emotion Model Stimuli

The valence and arousal emotion model [4], as in Figure 5, was used in this research, as it is a widely simplified emotion model. Four emotions (happiness, calmness, sadness, and fear) were classified according to the quadrants, respectively.

![](img/601340ca744b738277eef45ff127492a_209_0.png)

Figure 5. Valence and arousal model. Anger and fear have high valence and arousal. Happiness and excitement have high arousal and valence. Sadness and depression have low arousal and valence. Relaxation and pleasure have low arousal and high valence [4].

The International Affective Picture System (IAPS) [44] and the Geneva Affective Picture Database (GAPED) [45] were used as emotional stimuli. IAPS was the most widely used among previous research [1]. IAPS was elicited at the Center for the Study of Emotion and Attention, University of Florida, by Long, et al. [44]. IAPS pictures were designed, and publicly available for use in emotional stimuli. The emotions elicited based on two dimensions, which valence ranged from unpleasant to pleasant, while arousal ranged from calm to excited. Every picture has valence and arousal ranging from the scale 1 (lowest) to 9 (highest). However, IAPS contains fewer numbers of pictures stimulating low valence and arousal than needed, so additional pictures from GAPED were used.

The GAPED database was developed by Dan-Glauser, et al. at the University of Geneva [45]. It was intended to provide additional pictures to limited number of IAPS for experimental researchers. GAPED provided a 730 picture database for emotion simulation, which was also based on valence-arousal parameters. Moreover, four classical music pieces from auditory emotional research [46] were also applied. The four music pieces were also chosen on the emotion-arousal model, which corresponded to the IAPS and GAPED pictures.

### 3.4. Feasibility

Previous studies on emotion classification using multiple EEG channels. The feasibility of emotion classification using a single-channel in-ear EEG was evaluated first. The feasibility was conducted by performing an emotion classification experiment using secondary data from the Dataset for Emotion Classification using Physiological and Audiovisual (DEAP) [47]. DEAP data set is a widely available dataset for Brain Computer Interface (BCI) emotion study collected by Koistainen, et al. [47]. 32 channel EEG data from 32 subjects were collected, while they watched music video clips chosen to elicit emotions. The emotions elicited were based on the valence-arousal model. Valence was associated with positivity which ranged from unpleasant to happy/pleasant. Arousal was associated with excitement which ranged from calm to excited. The subjects rated the music video clips on valence-arousal scales. The DEAP dataset was here labelled, and the classification accuracy on the data could be evaluated by the subjects' rating. Out of 32 channels, only T7 and T8, which were stated to be close and correlate to the in-ear EEG.
