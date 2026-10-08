![](bbox=[0.196, 0.163, 0.803, 0.363])

Figure 1. The proposed methodology for long-term human stress classification.

The recorded EEG signals were made noise free in the pre-processing stage. Neuro-physiological features including alpha (α), low beta (β₁), beta (β), gamma (γ), delta (δ), theta (θ), and relative gamma (RG) power were extracted from the signals at each electrode. Frontal and temporal alpha and beta asymmetries, and alpha asymmetry calculated from these features. Five supervised machine learning algorithms (SVM, NB, KNN, LR, and MLP) were used to classify human stress. Two different labeling methods were used, including the perceived stress score and expert evaluation, where the PSS and interview scores were simultaneously recorded. A detailed description of these methods is presented in the following subsections. The flow of events during the acquisition process is shown in Figure 2.

| Filling of Consent Form (3-5 minutes) | EEG Setup (3-5 minutes) | EEG Recording (3 minutes) | Filling of PSS Form (10-15 minutes) | Interview by Psychology Expert (20-30 minutes) |

Figure 2. Experimental sequence and the data acquisition.

# 3.1. Data Acquisition

All EEG recordings were performed in a free lab using the EMOTIV Insight headset, which records brainwaves and provides advanced electronics that are optimized to produce clean and robust signals. Its data transmission rate is 128 samples per second, which provides the ability to perform an in-depth analysis on the brain activity. It has a minimum resolution of 0.51 volts least significant bit (LSB) with 5 EEG electrodes (F3, F4, F7, T7, T8) and 2 reference electrodes. The headset is shown in Figure 3 with the five electrodes highlighted for reference. The device uses 14 bits for quantization, where 1 LSB = 0.51 µV. A 16-bit analog to digital conversion (ADC) is used, where 2 bits of instrumental noise floor are discarded. The reference electrodes CMS/DRL are located on left mastoid bone. The participants were asked to close their eyes for a duration of three minutes and were instructed to keep their head still to reduce movement artifacts. This helped in minimizing the muscular motion and reduce these artifacts, as we recorded data at the frontal