# Core Concepts in Computer Science: Computer Networks

the electronic circuitry in the receiver can detect and interpret the signal. Second, the signal must maintain a level sufficiently higher than noise to be received without error. Third, attenuation is an increasing function of frequency.

+   - Distortion: Distortion means that the signal changes its form or shape. Delay distortion is a phenomenon peculiar to guarded transmission media. The distortion is caused by the fact that the velocity of propagation of a signal through a guided medium varies with frequency. For a band limited signal, the velocity tends to be highest near the center frequency and lower towards the two edges of the band. Thus, various frequency components of a signal will arrive at the receiver at different times. This effect is referred to as delay distortion, as the received signal is distorted due to delay in its components. The distortion effect as shown in the following figure:

Frequency is the number of occurrences of a repeating event unit of time. It is also referred to as temporal frequency, which emphasizes the contrast to spatial frequency and angular frequency.

![](bbox=[0.358, 0.453, 0.903, 0.573])

Delay distortion is particularly critical for digital data. Consider that a sequence of bits is being transmitted, using either analog or digital signals. Because of delay distortion, some of the signal components of one bit position will spill over into other positions, causing inter symbol interference, which is a major limitation to maximum bit rate over a transmission control. Equalizing techniques can also be used for delay distortion.

+   - Noise: Noise refers to any unwanted signal. For any data transmission event, the received signal will consist of the transmitted signal, modified by the various distortions imposed by the transmission system, plus additional unwanted signals that are inserted somewhere between transmission and reception; the latter, undesired signals are referred to as noise-a-major limiting factor in communications system performance.