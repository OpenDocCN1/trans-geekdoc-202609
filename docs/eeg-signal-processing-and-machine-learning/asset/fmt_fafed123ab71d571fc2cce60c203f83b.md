
# Vagus Nerve Stimulation and Neurotechnology Projects

Vagus nerve stimulation involves delivering electrical impulses to the vagus nerve. The relationship between depression, inflammation, metabolic syndrome, and heart disease might be mediated by the vagus nerve. Vagus nerve stimulation is sometimes used for epilepsy and depression.

In Japan, a brain‐mapping project named Brain Mapping by Integrated Neurotechnologies for Disease Studies (Brain/MINDS) started in 2014 ([http://www.brainminds.jp](http://www.brainminds.jp/)).

In the USA, DARPA has funded and demonstrated advanced neurotechnologies that rely on surgically implanted electrodes to interface with the central or peripheral nervous systems ([https://www.darpa.mil/news‐events/2019‐05‐20](https://www.darpa.mil/news-events/2019-05-20)). The agency has demonstrated achievements such as neural control of prosthetic limbs and restoration of the sense of touch to the users of those limbs, relief of otherwise intractable neuropsychiatric illnesses such as depression, and improvement of memory formation and recall. Due to the inherent risks of surgery, these technologies have so far been limited to use by volunteers with clinical need including military service personals. Currently, there are six teams pursuing a range of approaches that use optics, acoustics, and electromagnetics to record neural activity and/or send signals back to the brain at high speed and resolution. Both invasive and noninvasive approaches are taken. The teams are:

*   **The Battelle team** aiming to develop a minutely invasive interface system that pairs an external transceiver with electromagnetic nanotransducers that are nonsurgically delivered to neurons of interest. The nanotransducers would convert electrical signals from the neurons into magnetic signals that can be recorded and processed by the external transceiver, and vice versa, to enable bidirectional communication.

*   **The Carnegie Mellon University team**, aiming to develop a completely noninvasive device that uses an acousto‐optical approach to record from the brain and interfering electrical fields to write to specific neurons. The team will use ultrasound waves to guide light into and out of the brain to detect neural activity. The team's write approach exploits the nonlinear response of neurons to electric fields to enable localized stimulation of specific cell types.

*   **The Johns Hopkins University Applied Physics Laboratory team**, aiming to develop a completely noninvasive, coherent optical system for recording from the brain. The system will directly measure optical path‐length changes in neural tissue that correlate with neural activity.

*   **The PARC team**, aiming to develop a completely noninvasive acousto‐magnetic device for writing to the brain. Their approach pairs ultrasound waves with magnetic fields to generate localized electric currents for neuromodulation. The hybrid approach offers the potential for localized neuromodulation deeper in the brain.

*   **The Rice University team**, aiming to develop a minutely invasive, bidirectional system for recording from and writing to the brain. For the recording function, the interface will use diffuse optical tomography to infer neural activity by measuring light scattering in neural tissue. To enable the write function, the team will use a magneto‐genetic approach to make neurons sensitive to magnetic fields.

*   **The Teledyne team**, aiming to develop a completely noninvasive, integrated device that uses micro optically pumped magnetometers to detect small, localized magnetic fields that correlate with neural activity. The team will use focused ultrasound for writing to neurons.

In addition, there are over 21 ongoing companies and startups in the United States involving in brain–machine interfaces, implants, and neuroprosthetics.

## 17.12 Joint EEG and Other Brain‐Scanning Modalities for BCI

Typically, hybrid BCIs such as EEG‐functional near‐infrared spectroscopy (fNIRS) [[158]](#c17.xhtml#c17-bib-0158), [[159]](#c17.xhtml#c17-bib-0159) or EEG–fMRI [[160]](#c17.xhtml#c17-bib-0160) provide a higher classification accuracy than those of unimodal BCIs [[161]](#c17.xhtml#c17-bib-0161), [[162]](#c17.xhtml#c17-bib-0162). This is mainly due to low spatial resolution of EEG and low temporal resolution of imaging modalities such as fMRI or low depth of imaging of NIRS. Recent MEG technology also allows for joint EEG–MEG due to higher sensitivity of MEG to depth and conductivity.

### Joint EEG–fMRI for BCI

Although the use of fMRI solely or joint with EEG is not practical for real‐life BCI applications, there have been some experiments to exploit the high spatial resolution of fMRI to boost the BCI performance often achieved using EEG only. In [[149]](#c17.xhtml#c17-bib-0149) a new tensor factorization approach for transferring the capabilities of fMRI to EEG is proposed which includes simultaneous EEG–fMRI sessions for finding a mapping from EEG to fMRI, followed by a BCI run from only EEG data, but driven by fMRI‐like features obtained from the mapping identified previously [[163]](#c17.xhtml#c17-bib-0163).

In their method, they used orthogonal tensor decomposition using Tucker model as a method for subspace decomposition of EEG and deconvolving fMRI. Then, they designed a higher order partial least squares (HOPLS) model for discovering the relationships between the latent subspace representations of EEG and deconvolved fMRI [[149]](#c17.xhtml#c17-bib-0149).

Their experiments involve an open loop P300‐based speller paradigm wherein the brain activity can be decoded using latent features extracted from simultaneously acquired EEG–fMRI data. Letter decoding accuracy using EEG–fMRI data has been shown to outperform the accuracy obtained from only EEG.

This data‐driven method is likely to discover latent linkages between electrical and hemodynamic signatures of neural activity previously unexplored using model‐driven methods, and is likely to serve as a template for a multimodal strategy wherein cross‐modal EEG–fMRI interactions are exploited for the operation of a unimodal EEG system.

### 17.12.1 Joint EEG–fNIRS for BCI

NIRS is relatively robust to electrical noise and has good spatial resolution. To alleviate the ITR degradation, the authors in [[159]](#c17.xhtml#c17-bib-0159) proposed a simultaneous EEG–fNIRS operated by intuitive mental tasks, such as mental arithmetic (MA) and word chain (WC) tasks, performed within a short trial length (5 seconds). The subjects performed MA and WC tasks without preliminary training and remained relaxed (baseline; BL). The ITR (bits per second) is defined as:

[(17.24)](#c17.xhtml#R_c17-disp-0025)

```
ITR = m × (log₂N + P log₂P + (1 − P) log₂((1 − P)/(N − 1)))
```
