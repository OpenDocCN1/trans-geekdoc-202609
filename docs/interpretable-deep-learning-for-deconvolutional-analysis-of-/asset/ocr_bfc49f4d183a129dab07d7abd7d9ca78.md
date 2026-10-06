# # CellPress

# # Neuron
NeuronResource

# A Caudal whisker deflections

![](bbox=[0.195, 0.142, 0.485, 0.355])

# G Raster

![](bbox=[0.535, 0.142, 0.855, 0.325])

# B Whisker activity

![](bbox=[0.195, 0.385, 0.485, 0.455])

# H

![](bbox=[0.535, 0.355, 0.855, 0.525])

# C Test

![](bbox=[0.195, 0.482, 0.485, 0.545])

# Grouping neurons (group sparsity)

![](bbox=[0.535, 0.562, 0.855, 0.642])

# D

![](bbox=[0.195, 0.572, 0.485, 0.635])

# Individual neurons

![](bbox=[0.535, 0.662, 0.855, 0.742])

# E

![](bbox=[0.195, 0.662, 0.485, 0.742])

**Figure 4. Applied to somatosensory thalamus neurons, DUN learns a plasticity-level kernel, kernel events and insfer-specific amplitudes**

(A) Experimental setup; periodic whisker deflections at constant velocity in each trial (top), eliciting-shaped neural activity (left) in the ventral posteromedial (VPM) nuclei of the thalamus in anesthetized rats (right).

(B) DUN learns a simple kernel with neuron-specific firing rates (blue).

(C) Contrast from 10 neurons for one test trial: whisker deflections at 125 ms over 2000 ms.

(D) Perisensory histogram of an example neuron (black) with DUN-estimated firing rates (blue).

(E) Kernelization of whisker motion (blue) with the grey sinusoid fit that describes the stimulus motion.

(F) Quantitative evaluation of the encoder and decoder performance in detecting events on single trials. The curve shows the performance of a peak-finding algorithm applied to smoothed raster across trials. A 10 ms (2-ms tolerance) was used to compute false/misses. Peak finding from Python's signal processing package.

(G) Example trial: spikes, smoothed whisker rate (black), DUN-estimated spike rate (blue), and inferred codes for 16 + 2 events in time (bottom). Each event has a kernel amplitude, unlike previous methods (Supplementary information for more details on neurons, stimulus, and data from Terérica here.).

1158 Neuron 713, 1151–1168, April 16, 2025

(legend continued on next page)