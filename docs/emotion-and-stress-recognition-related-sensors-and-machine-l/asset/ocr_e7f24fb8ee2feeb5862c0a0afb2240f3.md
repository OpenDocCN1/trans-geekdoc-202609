Our final prototype of in-ear EEG device is shown in Figure 4. The total material cost per piece is approximately 10 US Dollars. Our in-ear EEG device's impedance was measured to be between 0.05 and 5.5 ohms which was comparable to that of OpenBCI electrodes: one of the commercial EEG electrodes [38].

![](bbox=[0.337, 0.185, 0.662, 0.396])

**Figure 4.** Single channel electrode used in the experiment using earphone rubber and silver-adhesive fabric electrode.



After the in-ear EEG devices were assembled, signal verification was performed. Mismatch tone (MMN) is one of the widely-used methods for EEG verification [39,40]. It was used to verify in-ear signals in the previous study [41]. Hence, it was also applied in our work. MMN is an experiment that observes the auditory event-related potential (ERP). ERP is a subject's EEG response to an unexpected change of sensory perception.

Our MMN experiment started by playing a short beep tone repeatedly until the subject was familiar to the unexpected tone. Unexpected mismatch tones were inserted among the familiar tone. Unexpected mismatch tones had a change of frequency (lower or higher), intensity (unusually louder or lighter), or phase. The mismatch tone, if acknowledged, will provide an ERP response as a negative peak. The mismatch responses usually give a negative peak between 90 and 250 milliseconds after the beep [41]. The ERP latency may vary according to personal memory [42].

The MMN experiment parameters in this study were set according to the previous study [40]. A combination of three tone frequencies: 500, 1000, and 1500 Hz lasting for 75 milliseconds, were used as a standard tone, whereas two types of mismatch tones were used. The first type was frequency mismatch containing 10% lower or higher pitch applied to each frequency. The other type was a duration mismatch tone which lasted for 100 milliseconds, 25 milliseconds longer than the standard tone. With the tone, the mismatch tones were inserted. Mismatched tones arrived at the probability of 0.5, but no consecutive mismatch tones were allowed.

The tones were played through an earphone. The in-ear EEG device was inserted to the right ear while the earphone was inserted to the left ear. The ground electrode was placed on the forehead and the reference electrode was placed on the right cheek, as suggested by [43]. OpenBCI's electrode was also placed at T8 as a comparison electrode. A Butterworth filter was used to notch 50 Hz powerline noise. It was applied as a bandpass to filter the EEG signal between 2 and 30 Hz. The signal correlation between T8 and in-ear EEG was also calculated.