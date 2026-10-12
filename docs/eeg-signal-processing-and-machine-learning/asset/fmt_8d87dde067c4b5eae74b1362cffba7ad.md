
### Figure 11.15
[**Figure 11.15**](#c11.xhtml#R_c11-fig-0015) Basal (left) and lateral (right) X‐ray images showing the inserted subdural FO electrodes (shown by arrows) and scalp EEG electrodes.

### Figure 11.16
![Figure 11.16 A segment of concurrent multichannel data. The first 22 signals belong to scalp EEG and the last 12 signals, recorded using FO electrodes, belong to intracranial EEG (iEEG).](images/c11f016.gif)

[**Figure 11.16**](#c11.xhtml#R_c11-fig-0016) A segment of concurrent multichannel data. The first 22 signals belong to scalp EEG and the last 12 signals, recorded using FO electrodes, belong to intracranial EEG (iEEG).

To enable detection of IEDs from scalp EEG using the joint recordings, primarily the intracranial data should be analyzed and the IEDs identified either manually or automatically. Obviously, detection of IEDs from very long (recorded in hours or days) intracranial data is very cumbersome. Therefore, establishing a reliable method in automatic IED detection is always desirable. Unfortunately, there is uncertainty in detecting IEDs even if it is done by expert clinicians mainly because of their variabilities in morphology.

Often inspection of IEDs from the scalp EEG is that for a subset of epileptic patients, there are no visually discernible IEDs on the scalp, rendering the above procedures ineffective, both for detection purposes and algorithm evaluation. Conversely, intracranially placed electrodes yield a much higher incidence of visible IEDs as compared to concurrent scalp electrodes. Spyrou et al. utilized concurrent scalp and iEEG from a group of TLE patients with low number of scalp‐visible IEDs [\[116\]](#c11.xhtml#c11-bib-0116). They tried to find out if by using the timing information of the IEDs from iEEG, the resulting concurrent scalp EEG contains enough information for the IED segments to be reliably distinguished from non‐IED segments. Their proposed automatic detection algorithm was tested in a leave‐subject‐out fashion, where each test subject's detection algorithm is based on the other patients' data.

Here, a fundamental assumption is that although a spike shape may not be clearly visible in the single‐trial scalp EEG, IED information is indeed present in those cases since the IEDs captured by averaging iEEG‐timed scalp EEGs over multiple trials are more likely to be visible.

The relation between the amplitude, location and propagation characteristics of IEDs in both recording modalities have been analyzed extensively \[[117](#c11.xhtml#c11-bib-0117)–[120](#c11.xhtml#c11-bib-0120)\].

### 11.6.2 iEED‐Times IED Detection from Scalp EEG

Spyrou et al. [\[116\]](#c11.xhtml#c11-bib-0116) investigated 20 minute simultaneous scalp and iEEG recordings from 18 TLE patients (11 males, seven females, mean age 25.2 years, range 13–37). For the iEEG multicontact FO electrode bundles and for the scalp EEG the Maudsley EEG electrode setting were used. Patients suffering from seizures arising from mesial temporal structures was submitted for telemetry recording with FO when history, interictal scalp EEG, neuroimaging and neuropsychological studies were not able to confidently determine the side of seizure onset, or there were doubts about a lateral temporal or extra‐temporal seizure onset. In 10 patients the seizure onset was identified within mesial temporal structures preceding in at least 2 ms the scalp changes while in eight patients it was located outside the mesial temporal region (lateral temporal). Most EEG recordings only contained wakefulness (13 patients) but some (5 patients) also included slow‐wave sleep.

The raw EEG data were sliced in a ±162.5 ms (±32 samples) window centred at the points scored as spike from intracranial data and baselined on the preceding 162.5 ms with the resulting signal finally being linearly detrended to remove undesired drifts. Non‐IED segments were also obtained from time segments where there are no scored IEDs.

In their work, TF features were used. A fundamental assumption is that although a spike shape may not be visible or clear on the single‐trial scalp EEG, the IED information is indeed present in such cases since averaging iEEG‐timed scalp EEG IEDs provides visible spike structures. Wavelet features were obtained by performing a discrete wavelet decomposition using the ‘db4’ mother wavelet since it provides the highest correlation with IEDs.

Through five level wavelet decomposition they used the maximum, the minimum, the mean, and the standard deviation of the wavelet coefficients in each of the five sub‐bands as features. Also, they used the time domain representations of the wavelet coefficients for the five sub‐bands. In addition, chirplet features were obtained using matching pursuit with a variable number of chirplets [\[121\]](#c11.xhtml#c11-bib-0121). Chirplets can represent signals with variable frequency over time [\[121\]](#c11.xhtml#c11-bib-0121). A chirplet is defined as:

(11.24)![equation](images/c11-disp-0025.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi mathvariant="italic">ch</mi><mfenced open="(" close=")"><mi>t</mi></mfenced><mo>=</mo><msub><mi>g</mi><mrow><mi>s</mi><mo>,</mo><mi>a</mi></mrow></msub><mfenced open="(" close=")"><mrow><mi>t</mi><mo>&#8722;</mo><mi>u</mi></mrow></mfenced><msup><mi>e</mi><mi mathvariant="italic">jvt</mi></msup></math>

with:

(11.25)![equation](images/c11-disp-0026.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>g</mi><mrow><mi>s</mi><mo>,</mo><mi>a</mi></mrow></msub><mfenced open="(" close=")"><mi>t</mi></mfenced><mo>=</mo><mfrac><mn>1</mn><mrow><msup><mi mathvariant="normal">&#960;</mi><mrow><mn>1</mn><mo>/</mo><mn>4</mn></mrow></msup><msqrt><mrow><mi mathvariant="normal">&#963;</mi><mfenced open="(" close=")"><mrow><mi>s</mi><mo>,</mo><mi>a</mi></mrow></mfenced></mrow></msqrt></mrow></mfrac><mo mathvariant="italic">exp</mo><mfenced open="(" close=")"><mrow><mo form="prefix">&#8722;</mo><mfenced open="(" close=")"><mrow><mfrac><mn>1</mn><mrow><msup><mi mathvariant="normal">&#963;</mi><mn>2</mn></msup><mfenced open="(" close=")"><mrow><mi>s</mi><mo>,</mo><mi>a</mi></mrow></mfenced></mrow></mfrac><mo>&#8722;</mo><mi mathvariant="italic">jl</mi><mfenced open="(" close=")"><mrow><mi>s</mi><mo>,</mo><mi>a</mi></mrow></mfenced></mrow></mfenced><mfrac><msup><mi>t</mi><mn>2</mn></msup><mn>2</mn></mfrac></mrow></mfenced></math>

Each chirplet consists of four parameters controlling the scaling (`s`), chirp rate (a), through the functions `σ()` and `l()`, the time shift (`u`) and frequency shift (`v`) [\[121\]](#c11.xhtml#c11-bib-0121). For each data segment only three chirplets were fitted to represent the waveform.

The between‐subject differences were decreased [\[116\]](#c11.xhtml#c11-bib-0116) and the scalp and intracranial segments were normalized to have unit norm per electrode channel. These reduce the individual differences between subjects enhancing the performance of the classifier.

Next, both scalp‐visible and non‐scalp‐visible IEDs are used in the classifier training and for analyzing the performance of the algorithm. A regularized linear logistic regression approach \[[122](#c11.xhtml#c11-bib-0122), [123](#c11.xhtml#c11-bib-0123)\] is used to train classifiers that can distinguish between IED and non‐IED events. Logistic regression has been widely used for EEG classification. Linear classifiers work by estimating a weight row vector `w` and a threshold (or bias) `b` that operate on the data `x` in the following way:
