![](bbox=[0.199, 0.093, 0.779, 0.377])

**Fig. 7.3** Proposed system model for synthesizing respiratory sounds

wheeze signals are given as input to the time-frequency transform. The continuous wavelet transform transforms the time-domain respiratory signal to time-scale analysis and is represented in the forms of scalogram representation. These real scalograms are fed as input to conditional GAN in order to generate more artificial scalogram images with the help of a generator network in cGAN. Finally, inverse CWT is applied to synthesize the respiratory sound signals in time domain.

# 7.3.3.2 Time-scale representation using CWT

The continuous wavelet transform (CWT) modifies the temporal length of the basis function for the purpose of achieving a changeable time-frequency localization. To interpret very small changes in frequencies, CWT utilizes longer basis functions at the cost of confined localization in time and uses shorter basis functions ascertaining high localization in time [27]. This time-frequency transform elicits a spectrum with time scale vs amplitude named scalogram. Compared to spectrograms, scalograms are useful for analyzing realistic signals at diverse scales. As the frequencies in CWT transform are logarithmic in nature, the obtained scalogram plot also uses a log scale frequency axis.

# 7.3.3.3 Generator and discriminator network architecture of cGAN

The network architecture for generator and discriminator are shown in Figs. 7.4 and 7.5 and the corresponding analysis result is tabulated in Tables 7.1 and 7.2. In cGAN, the