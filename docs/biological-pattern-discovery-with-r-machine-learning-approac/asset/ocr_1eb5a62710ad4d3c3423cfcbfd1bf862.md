# Biological Pattern Discovery with R

![](bbox=[0.228, 0.098, 0.772, 0.353])

Fig. 5.10. Two estimated peak spectra derived from the spectra with the estimated baselines shown in Figure 5.9.

# 5.7 The Bayesian Whittaker-Henderson algorithm

The Bayesian Whittaker-Henderson smoother algorithm (BWH) has been proposed for providing a better baseline estimation performance [Leu, et al., 2012]. The algorithm is an extension from several old algorithms by framing the Whittaker-Henderson smoother into the Bayesian learning framework. Moreover, BWH can align multiple spectra. The algorithm assumes that a signal, if it is true, should occur in more than one replicate. Based on this assumption, BWH can support robust signal detection for a spectra data set set of multiple replicates.

# 5.7.1 The working principle of BWH

Most spectra smoothing algorithms assume that only spectra intensities below a baseline are treated as noise and spectra intensities above a baseline are not treated as noise. However, BWH treats artifacts on both sides of a baseline as noises. This that the noise is assumed to distribute on both sides of a baseline when using BWH to estimate a baseline for a spectrum. BWH also assumes both the fidelity and the smoothness follow independent and identical Gaussian distributions. They are defined as below, where $\sigma_f^2$ and $\sigma_s^2$ are variances,