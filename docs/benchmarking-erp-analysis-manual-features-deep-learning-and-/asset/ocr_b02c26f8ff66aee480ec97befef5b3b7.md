![](bbox=[0.109, 0.072, 0.89, 0.512])

**Fig. 2: Pipeline of ERP Analysis.** Input raw EEG data are preprocessed with a unified pipeline to get ERP trials, including removal of non-EEG channels, notch and band-pass filtering, bad channel interpolation, average re-referencing, artifact removal, resampling, baseline correction, trial epoching, and Z-score normalization. The processed ERP trials are loaded and passed to various models for training and classification, including manual feature extraction, supervised deep learning trained from scratch, and foundation models with pre-trained weights.

frequency, peak power, mean frequency, median frequency, and spectral flatness [62]–[64]. These features characterize the overall distribution and structure of spectral energy. All spectral features are estimated using Welch's method for PSD estimation, followed by numerical integration and computations.

including mean, standard deviation, RMS, line length, and peak-to-peak amplitude [65]–[68], are computed across multiple temporal scales, yielding 5 × Σ levels feature dimensions. We set the number of levels equal to 15. Temporal Pyramid Pooling is employed to capture ERP dynamics at multiple temporal resolutions. This approach jointly captures global waveform structure and localized transients, improving robustness to temporal variability and latency jitter.

**Complexity features:** This category includes normalized & non-normalized Shannon spectral entropy and Tsallis entropy [34]–[36]. These features are derived from the normalized PSD, which is interpreted as a probability distribution. Shannon spectral entropy quantifies spectral disorder and complexity, with higher values indicating more uniformly distributed spectral energy, while Tsallis entropy generalizes Shannon entropy by incorporating non-extensive properties, providing greater sensitivity to nonlinear and non-stationary signal characteristics.

**Peak-Related Features:** amplitudes of positive and negative peaks and their normalized latencies [24]–[26]. Peak-related features are extracted to characterize salient ERP components. The maximum positive and minimum negative peak amplitudes reflect the strength of event-related neural responses. The total analysis window length-normalized latencies to account for variability in ERP duration and ensure comparability across trials and subjects.

**2) ERP Feature Extraction:** We compute a total of **91 features**, including 75 temporal pyramid pooling features, 4 peak-related Features, 9 frequency-band & complexity features, and 3 Hjorth parameters.

**Temporal Pyramid Pooling:** five statistical measures, in-

**Frequency & Complexity Features:** relative power in the δ, θ, α, and β bands, total power, spectral centroid, spectral flatness, median frequency, and normalized spectral entropy [27]–[30]. Although ERPs are time-locked signals, frequency-domain analysis provides complementary informa-