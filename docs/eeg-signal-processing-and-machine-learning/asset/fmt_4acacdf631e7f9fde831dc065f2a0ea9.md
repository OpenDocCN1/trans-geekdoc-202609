
## 数学公式

(15.6) ![equation](images/c15-disp-0006.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll">
<msub><mtext>lCOH</mtext><mrow><mi>x</mi><mo>,</mo><mi>y</mi></mrow></msub>
<mfenced open="(" close=")"><mi>f</mi></mfenced>
<mo>=</mo>
<mfrac>
<mrow><mo>Im</mo><msup><mfenced open="(" close=")"><mrow><msub><mi>c</mi><mrow><mi>X</mi><mo>,</mo><mi>Y</mi></mrow></msub><mfenced open="(" close=")"><mi>f</mi></mfenced></mrow></mfenced><mn>2</mn></msup></mrow>
<mrow><mn>1</mn><mo form="postfix">&#8722;</mo><mo>Re</mo><msup><mfenced open="(" close=")"><mrow><msub><mi>c</mi><mrow><mi>X</mi><mo>,</mo><mi>Y</mi></mrow></msub><mfenced open="(" close=")"><mi>f</mi></mfenced></mrow></mfenced><mn>2</mn></msup></mrow>
</mfrac>
</math>

EIC is simply

(15.7) ![equation](images/c15-disp-0007.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll">
<msub><mi>EIC</mi><mrow><mi>x</mi><mo>,</mo><mi>y</mi></mrow></msub>
<mo>=</mo>
<mfenced open="|" close="|">
<mrow><mi>H</mi><mfenced open="(" close=")"><mrow><mo>Im</mo><mfenced open="(" close=")"><mrow><msub><mi>c</mi><mrow><mi>x</mi><mo>,</mo><mi>y</mi></mrow></msub><mfenced open="(" close=")"><mi>f</mi></mfenced></mrow></mfenced></mrow></mfenced>
</mrow>
</mfenced>
</math>

Also, a modified version of EIC is defined as:

(15.8) ![equation](images/c15-disp-0008.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll">
<msub><mtext>EICm</mtext><mrow><mi>x</mi><mo>,</mo><mi>y</mi></mrow></msub>
<mo>=</mo>
<mfenced open="|" close="|">
<mfrac>
<mrow><mi>H</mi><mfenced open="(" close=")"><mrow><mi>E</mi><mfenced open="\[" close="\]"><mrow><mo>Im</mo><mo stretchy="true" form="prefix">(</mo><mi>X</mi><mfenced open="(" close=")"><mi>f</mi></mfenced><mi>Y</mi><msup><mfenced open="(" close=")"><mi>f</mi></mfenced><mo>&#42;</mo></msup></mrow></mfenced></mrow></mfenced></mrow>
<mrow><mi>E</mi><mfenced open="\[" close="\]"><mrow><mi>H</mi><mo stretchy="true" form="postfix">(</mo><mo>Im</mo><mfenced open="(" close=")"><mrow><mi>X</mi><mfenced open="(" close=")"><mi>f</mi></mfenced><mi>Y</mi><msup><mfenced open="(" close=")"><mi>f</mi></mfenced><mo>&#42;</mo></msup></mrow></mfenced></mrow></mfenced></mrow>
</mfrac>
</mfenced>
</math>

Finally, they conclude and claim that `EIC` and `iCOH` demonstrate superior results compared with other functional connectivity estimates.

These measures are usually applied in a channel‐wise manner, producing a very high number of variables [[13]](#c15.xhtml#c15-bib-0013), [[18]](#c15.xhtml#c15-bib-0018). All these studies and experiments clearly show that the brain connectivity significantly changes for many of these neurodegenerative diseases particularly AD.

A possible option is to try to estimate the equivalent current dipoles [[1]](#c15.xhtml#c15-bib-0001), [[19]](#c15.xhtml#c15-bib-0019), [[20]](#c15.xhtml#c15-bib-0020). Once the currents are estimated, the same connectivity metrics used in the channel‐wise analyses can be applied to them. Moreover, the volume‐conduction effect does not affect these dipole‐based connectivity assessments. However, the solution of the inverse problem is not unique and the choice of the reconstruction algorithm and other a priori assumptions influence the dipole estimation leading to potentially misleading results [[12]](#c15.xhtml#c15-bib-0012), [[14]](#c15.xhtml#c15-bib-0014).

A research study was carried out by Escudero et al. [[21]](#c15.xhtml#c15-bib-0021) for differentiation between NC, AD, and MCI using MEG signals. In their research they pre‐processed the signals before assessing the coherence between the selected brain zones.

![Figure 15.1 Distribution of the MEG sensors into left central (LC), anterior (LA), lateral (LL) and posterior (LP); and right central (RC), anterior (RA), lateral (RL) and posterior (RP) regions. Midline sensors appear empty. The lines depict the region boundaries.](images/c15f001.gif)

**Figure 15.1** Distribution of the MEG sensors into left central (LC), anterior (LA), lateral (LL) and posterior (LP); and right central (RC), anterior (RA), lateral (RL) and posterior (RP) regions. Midline sensors appear empty. The lines depict the region boundaries.

In this work scalp electrode space has been divided into nine regions as illustrated in [Figure 15.1](#c15.xhtml#c15-fig-0001). Instead of measuring the connectivity directly, MEG signals have been processed using the empirical mode decomposition (`EMD`) and blind source separation (`BSS`).

In the proposed algorithm, the `EMD` technique was used to decompose each MEG channel into a set of intrinsic mode functions (`IMFs`). Then, a constraint `BSS` block extracts the representative delta, theta, alpha, and beta rhythms of each region. In addition to the corresponding spectral coherence, *magnitude squared coherence* (`MSC`) is used here to measure the brain synchrony. It quantifies linear correlations as a function of frequency. `MSC` is bounded between 0 and 1. This measure can detect the linear synchronization between two signals, but it does not discriminate the directionality of the coupling [8.50]. A simplified block diagram of the algorithm is presented in [Figure 15.2](#c15.xhtml#c15-fig-0002). In [Figure 15.3](#c15.xhtml#c15-fig-0003)a and b a channel of MEG signal and its corresponding `IMFs` computed using the `EMD` algorithm can be viewed.

To select the right `IMFs` in terms of centre frequency from each region, the `IMFs` have been clustered based on their amplitudes, frequency, and proximity to any one of the four centre frequencies. As depicted in [Figure 15.4](#c15.xhtml#c15-fig-0004) the *k*‐means algorithm has been used to select a reference signal frequency for each band. This is necessary since the frequency band centres change from subject to subject.

![Figure 15.2 Block diagram of the spectral coherency, c(f), measure.](images/c15f002.gif)

**Figure 15.2** Block diagram of the spectral coherency, `c(f)`, measure.

Quantitative measurement of spectral coherency without or with regional extraction of rhythms has led to the charts in [Figure 15.5](#c15.xhtml#c15-fig-0005) respectively in the left and right bar graphs.

As a result, raw MEG measurements of subject group pairs produced `c(f)` accuracy rates of 51.6–61.1%, compared to 66.7–77.3% for the pairs of subject groups when rhythms were extracted.

### 15.2.2 ERP‐Based AD Monitoring

Advanced techniques in signal processing can be employed to detect and reveal the changes in event‐related potentials (`ERPs`), particularly for P300 subcomponents, due to AD. P3b subcomponent elicits as the result of novel or target stimuli in an odd‐ball paradigm experiment. For AD patients both amplitude and latency of P3a changes compared to the healthy subjects. For AD the P3b amplitude reduces whereas P3a amplitude does not have any significant change compared with those of healthy subject. Also, the relative (to P3a) latency for P3b significantly increases as the result of AD [[22]](#c15.xhtml#c15-bib-0022). [Figure 15.6](#c15.xhtml#c15-fig-0006) clearly shows the changes in P3b.

### 15.2.3 Other Approaches to EEG‐Based AD Monitoring

The authors of [[11]](#c15.xhtml#c15-bib-0011) examined changes in the large‐scale structure of resting‐state brain networks in patients with AD and compared with non‐demented controls, by applying concepts from graph theory to the MEG signals.

For the main frequency bands, synchronization between all pairs of MEG channels was assessed using PLI‐weighted connectivity networks and characterized by a mean clustering coefficient and path length.

![Figure 15.3 (a) A 10 second segment of one EMG channel and (b) its corresponding IMFs.](images/c15f003.gif)

**Figure 15.3** (a) A 10 second segment of one EMG channel and (b) its corresponding `IMFs`.

![Figure 15.4 Reference selection using the k‐means algorithm.](images/c15f004.gif)
