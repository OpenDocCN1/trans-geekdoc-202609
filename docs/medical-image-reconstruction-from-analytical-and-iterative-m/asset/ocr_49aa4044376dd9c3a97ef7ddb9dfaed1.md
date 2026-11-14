The attenuation-corrected measurement is

\( p_c = L_1\rho_1 + L_2\rho_2. \)

# 4.7 Summary

+   - The working principle for X-ray CT measurement is Beer's law. One needs to take the logarithm to convert the CT measurements into line integrals.
+   - PET and SPECT measure line integrals directly. However, these measurements suffer from photon attenuation within the patient.
+   - Attenuation correction for PET can be achieved by the pre-scaling method. The scaling factor is obtained by transmission measurements.
+   - Attenuation correction for SPECT is difficult and cannot be done by pre-scaling. Attenuation correction is a built-in feature in SPECT reconstruction algorithms. FBP algorithms exist for uniform attenuator and for nonuniform attenuator as well. However, the FBP algorithm for the nonuniform attenuator is very complicated to implement.
+   - The readers are expected to understand the differences between transmission and emission tomography, and also the different attenuation effects in PET and SPECT.

# Problems

+   Problem 4.1 The line-integral data \( p \) from transmission tomography can be obtained by \( p = \ln(I_0/I_d) \), where \( I_0 \) and \( I_d \) are the numbers of the photons entering and leaving the patient body, respectively. The noise characteristics of the photon numbers are Poisson distributed. In practice, the entering number \( I_0 \) is very large and can be treated as a constant. Prove that the mean value (i.e., the expected value) and the variance of the line integral \( p \) can be approximated as \( p \) and \( 1/I_d \), respectively.

+   Problem 4.2 The object to be imaged is a 2D uniform disk with a radius \( R \). The linear attenuation coefficient of the disk is a constant \( \mu \) and its radioactivity line density is a constant \( \rho \). The center of the disk is at the center of the detector rotation. Find the expressions of the attenuated projection data \( p(s, \theta) \) for SPECT and PET cases, respectively.

+   Problem 4.3 Prove that the inverse Fourier transform of the transfer function \( H_\mu(\omega) \) of the filter shown in Figure 4.19 is the convolution kernel \(\frac{\cos(\mu s)}{s} * \delta'(s) = - \frac{(\mu s)\sin(\mu s) + \cos(\mu s)}{s^2} \).