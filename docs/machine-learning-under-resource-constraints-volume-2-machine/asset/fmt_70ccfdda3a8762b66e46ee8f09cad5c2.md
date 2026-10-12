
[Figure 8.13](#9783110785951_020762.xhtml#b_9783110785968-008_fig_013) shows the event display of this particularly interesting `ν[τ]`\-candidate. The event is fully contained within the instrumented volume of the detector, as DOMS near the detector boundaries did not observe a significant amount of light. Colors in this figure represent the arrival time of the observed Cherenkov photons and range from red (early) to blue (late). The size of the color-coded DOMs represents the amount of light collected by a particular DOM. The spherical shape of the event, indicated by large amount of light collect at early times (central DOMs in red) and smaller amounts of light detected by outer DOMs at later times, is clearly visible from the event display.

For the second event, a double pulse score of 0.565 was observed for a single waveform and a cascade score of 0.675 was observed for the event as a whole. This event is thus most likely a background event.

![Fig. 8.13: Event view of the ντ-candidate observed during the 2014 data-taking season of IceCube. The event is fully contained inside the instrumented volume. Colors in this plot represent the timing of the detected Cherenkov photons from red (early) to late (blue), whereas the size of the DOMs corresponds to the amount of light observed by a particular DOM. Figure courtesy of the IceCube collaboration.](graphic/b_9783110785968-008_fig_013.png)

Fig. 8.13: Event view of the `ντ`\-candidate observed during the 2014 data-taking season of IceCube. The event is fully contained inside the instrumented volume. Colors in this plot represent the timing of the detected Cherenkov photons from red (early) to late (blue), whereas the size of the DOMs corresponds to the amount of light observed by a particular DOM. Figure courtesy of the IceCube collaboration.

## 8.4 Estimation of Event Properties for IACTs

**Maximilian Linhoff**

**Jens Buß**

**Abstract:** To be able to do gamma-ray astronomy and obtain spectral information about the sources using IACT data, three properties of each recorded air-shower event have to be estimated: the energy of the primary particle, its type, and its direction. Estimating the energy is a one-dimensional regression task. The type of a particle is in general a multi-class classification. However, for standard gamma-ray analysis it is simplified to a binary classification into “gamma” (the signal class) and “hadron” (the background class). Direction is a two dimensional regression, since the two angles of the spherical celestial coordinate system have to be estimated. In IACT arrays like MAGIC or CTA, geometric approaches utilising the fact that the air shower was observed from multiple angles, usually deliver the best results. However, this task is considerably harder for monoscopically operating telescopes, like FACT or the LST-1 prototype. Here, machine learning instead of the geometric approach delivers the most competitive results.

In this section, we present the analysis chain based on the feature extraction from [Chapter 7](#9783110785951_015782.xhtml#b_9783110785968-007), using classical machine learning approaches to solve these tasks for FACT, CTA, and the LST-1 prototype.

We present the used algorithms and obtained results of this analysis chain, including energy-dependent benchmarks for the analysis such as the angular resolution of the directional reconstruction, the bias and variance of the energy estimation, the ROCcurve of the gamma/hadron classification, and the overall the point-source flux sensitivity.

For the telescope arrays, an additional challenge is how to best combine the data and/or predictions of the single telescopes into a common prediction for the observed air shower.

In this section, we discuss how to estimate the relevant properties of the primary particles which induce the air showers from the features extracted as described in [Section 7.3](#9783110785951_015782.xhtml#b_9783110785968-007_s_003). This section was partly adapted from two Ph.D. theses written in the context of the CRC 876 \[101, 294\].

To do gamma-ray astronomy and the spectral analysis of gamma-ray sources, three main properties have to be estimated for each recorded air-shower event:

**Particle type** IACTs measure thousands of air showers induced by charged cosmic rays for each measured gamma ray. To reduce this background as effectively as possible, events are classified as induced by gamma rays or hadrons. This is a classification task.

**Primary energy** While techniques such as unfolding could directly estimate a spectral distribution from several input features, the condition of the inverse problem usually improves when using a direct estimator of the primary energy. Using a single estimate also makes it much easier to define common data formats for event lists and instrument response functions since the low-level image features will differ between the different observatories and software packages, but an estimated energy is very universal. This is a one-dimensional regression task.

**Particle origin** To enable gamma-ray astronomy, we need to know from where the particle actually came. In the end, we want to know this direction expressed in the fixed coordinate system of the International Celestial Reference Frame (ICRS). Usually, the estimation is done in the local coordinate system of the detector, say, using horizontal coordinates, which are then transformed into the sky-fixed system. The direction of the particle also plays a crucial role in the background suppression, as the cosmic ray background is isotropic compared with the compact or point-like gamma-ray sources.

The two-dimensional regression to estimate the origin of a gamma ray is especially hard for monoscopic IACTs, as multiple telescopes allow simpler and more precise geometric reconstruction methods. We will discuss both approaches, a machine learning-based solution for monoscopic telescopes and several approaches for stereoscopic arrays.

Historically, these tasks were performed by applying event selection criteria, often called `cuts`, for the particle classification and hand-crafted regression formulas fitted to simulations for the energy estimation and reconstruction of origin, see e. g. \[[43](#9783110785951_034588.xhtml#b_9783110785968-011_ref_043)\].Modern methods of machine learning have improved performance and removed human biases from these steps.

Additionally, a high precision timestamp of the arrival time of the event is needed, which is of special interest for pulsars like the one at the center of the Crab Nebula, which has a period of ≈ 30 ms \[[79](#9783110785951_034588.xhtml#b_9783110785968-011_ref_079)\]. This is usually produced by the trigger electronics at the telescope, can be used without further processing and can achieve sub-microsecond precision.

In case of stereoscopic observations, the question arises when and how to combine the data of the single telescopes to form a common prediction for the air shower. Multiple approaches of different complexity exist and are discussed towards the end of this section. This is also a topic of ongoing research to improve the analysis, especially for the complex arrays of CTA.

### 8.4.1 Labeled Training Data

Since we have well-defined reconstruction tasks and labeled data available from either Monte Carlo simulations (see [Chapter 5](#9783110785951_011899.xhtml#b_9783110785968-005)) or measurements of regions where no (known) gamma-ray source resides and thus only background events are expected, supervised machine learning is the method of choice.
