AlexNet, VGGNet, ResNet, GoogleLeNet are some of the many architectures of CNN developed over the years for the purposes image detection and classification.

# 4.5. AUDIO SIGNAL PROCESSING

As the title suggests, audio signal processing is the field of study from signal processing which deals with the manipulation of sound signal. Audio Signal Processing is not a new field of study. It has been used earlier in radio, phonography and telephonic communication. Nowadays, deep learning techniques are used for audio signal processing. In audio signal processing, the main focus is always on how to extract important frequency components from the audio sample which can be used to efficiently distinguish the audio signal.

Audio signals are typically in the range of 20 Hz to 20 kHz. These are longitudinal waves created by compression and expansion of air. When the sound enters our ear, it gets transmitted to the cochlea which is filled with thousands of hairs of variable size inside a fluid filled membrane. The short hair responds to higher frequency while the long hair responds to the low frequency of sound. Thus, the ear acts like a natural Fourier transform analyser [14].

The first step in audio processing is sampling which is defined as process of converting continuous signal into discrete values. The amount of information present in the discrete signal is defined by sampling frequency or rate. A higher sampling rate indicates less loss of information but the computational complexity of processing the discrete audio signal increases.

The amplitude of each sample of the discrete signal is also an important feature.

The processing of the entire audio signal at the same time can pose higher computational complexity apart from high time and resource consumption. The best way is to divide the audio signal into small frames of 20 – 40 ms. The power spectral density of each frame is calculated by applying Fourier transform on the autocorrelated audio signal. It shows the distribution of power among various frequency in the frame as shown in Fig. (4.11).

One important fact about the human ear is that the sounds with higher frequency is difficult to perceive than the sounds of lower frequency. This why the mel filter banks are used. The mel scale is defined as the scale of pitches judged by listeners to be equal in distance from one another. The reference point is taken such that 1000 mel = 1000 Hz. The mel filter bank acts like a human ear as the mel scale changes rapidly for less frequency than for higher frequency as shown in Fig. (4.12).